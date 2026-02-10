---
Link:
tags:
  - ML
---
# Parameters
## Learning Rate
- Defines how much the model's weights are adjusted during each training step.
- **Higher Learning Rates**: Lead to faster initial convergence but can cause training to become unstable or fail to find an optimal minimum if set too high.
- **Lower Learning Rates**: Result in more stable and precise training but may require more epochs to converge, increasing overall training time. While low learning rates are often thought to cause underfitting, they actually can lead to overfitting or even prevent the model from learning.
- **Typical Range**: 0.0002 to 0.000005
	- For normal LoRA/QLoRA fine-tuning, 0.0002 is recommended as a starting point.
	- For reinforcement learning (DPO, GRPO etc.), we recommend 0.000005
	- For full fine-tuning, lower learning rates are generally more appropriate.
## Epochs
- The number of times the model sees the full training dataset.
- **More Epochs**: Can help the model learn better, but a high number can cause it to memorize the training data, hurting its performance on new tasks.
- **Fewer Epochs**: Reduces training time and can prevent overfitting, but may result in an undertrained model if the number is insufficient for the model to learn the dataset's underlying patterns.
- **Recommended**: 1-3 epochs. For most instruction-based datasets, training for more than 3 epochs offers diminishing returns and increases the risk of overfitting.
## LoRA or QLoRA
- LoRA uses 16-bit precision, while QLoRA is a 4-bit fine-tuning method.
- **LoRA**: 16-bit fine-tuning. It's slightly faster and slightly more accurate, but consumes significantly more VRAM (4x more than QLoRA). Recommended for 16-bit environments and scenarios where maximum accuracy is required.
- **QLoRA**: 4-bit fine tuning. Slightly slower and marginally less accurate, but uses much less VRAM (4x less).
## Hyperparameters
| Hyperparameter                | Function                                                                                                                                                                                                      | Recommended Settings                                                                                           |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| **LoRA Rank (`r`)**           | Controls the number of trainable parameters in the LoRA adapter matrices. A higher rank increases model capacity but also memory usage.                                                                       | 8, 16, 32, 64, 128<br><br>Choose 16 or 32                                                                      |
| **LoRA Alpha (`lora_alpha`)** | Scales the strength of the fine-tuned adjustments in relation to the rank (`r`)                                                                                                                               | `r` (standard) or `r*2` (common heuristic)                                                                     |
| **LoRA Dropout**              | A regularization technique that randomly sets a fraction of LoRA activations to zero during training to prevent overfitting. **Not that useful**, so we default set it to 0.                                  | 0 (default) to 0.1                                                                                             |
| **Weight Decay**              | A regularization term that penalizes large weights to prevent overfitting and improve generalization. Don't use too large numbers!                                                                            | 0.01 (recommended) - 0.1                                                                                       |
| **Warmup Steps**              | Gradually increases the learning rate at the start of training.                                                                                                                                               | 5-10% of total steps                                                                                           |
| **Scheduler Type**            | Adjusts the learning rate dynamically during training.                                                                                                                                                        | `linear` or `cosine`                                                                                           |
| **Seed** (`random_state`)     | A fixed number to ensure reproducibility of results.                                                                                                                                                          | Any integer (e.g., `42`, `3407`)                                                                               |
| **Target Modules**            | Specify which parts of the model you want to apply LoRA adapters to -- either the attention, the MLP, or both.<br><br>Attention: `q_proj, k_proj, v_proj, o_proj`<br><br>MLP: `gate_proj, up_proj, down_proj` | Recommended to target all major linear layers: `q_proj, k_proj, v_proj, o_proj, gate_proj, up_proj, down_proj` |
### Gradient Accumulation and Batch Size
- **Effective Batch Size** = `batch_size * gradient_accumulation_steps`
	- A **larger effective batch size** generally leads to smoother, more stable training.
	- A **smaller effective batch size** may introduce more variance.
- Effective Batch Size of 16 works well for most fine-tuning tasks on modern GPUs.

| Parameter                                                 | Description                                                                                                                                                                                                                                       | Recommended Setting                     |
| --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------- |
| **Batch Size** (`batch_size`)                             | The number of samples processed in a single forward/backward pass on one GPU.<br><br>**Primary Driver of VRAM Usage**<br>Higher values can improve hardware utilization and speed up training, but only if they fit in memory.                    | 2                                       |
| **Gradient Accumulation** (`gradient_accumulation_steps`) | The number of micro-batches to process before performing a single model weight update.<br><br>**Primary Driver of Training Time**<br>Allows simulation of a larger `batch_size` to conserve VRAM. Higher values increase training time per epoch. | 8                                       |
| **Effective Batch Size**                                  | The true batch size used for each gradient update. It directly influences training stability, quality and final model performance.                                                                                                                | 4 to 16<br>Recommended: 16 (from 2 * 8) |
### The VRAM & Performance Trade-off
- `batch_size = 32, gradient_accumulation_steps = 1`
- `batch_size = 16, gradient_accumulation_steps = 2`
- `batch_size = 8, gradient_accumulation_steps = 4`
- `batch_size = 4, gradient_accumulation_steps = 8`
- `batch_size = 2, gradient_accumulation_steps = 16`
- `batch_size = 1, gradient_accumulation_steps = 32`
The first configuration (`batch_size = 32`) uses the most VRAM and will likely fail on most GPUs. The last configuration (`batch_size = 1`) uses the least VRAM, but at the cost of slightly slower training.
> [!NOTE] NOTE
> To avoid OOM (out of memory) errors, always prefer to set a smaller `batch_size` and increase `gradient_accumulation_steps` to reach your target **Effective Batch Size**.
- Training on completions only increase accuracy by 1%.
## Avoiding Overfitting & Underfitting
### Overfitting
- The model memorizes the training data, including its statistical noise, and consequently fails to generalize to unseen data.
- If the training loss drops below 0.2, your model is likely overfitting -- meaning it may perform poorly on unseen tasks.
- One simple trick is LoRA alpha scaling -- just multiply the alpha value of each LoRA matrix by 0.5. This effectively scales down the impact of fine-tuning.
**Solution:**
- **Adjust the learning rate:** A high learning rate often leads to overfitting, especially during short training runs. For longer training, a higher learning rate may work better. It's best to experiment with both to see which performs best.
- **Reduce the number of training epochs.** Stop training after 1, 2 or 3 epochs.
- **Increase** `weight_decay`. A value of `0.01` or `0.1` is a good starting point.
- **Increase** `lora_dropout`. Use a value like `0.1` to add regularization.
- **Increase batch size or gradient accumulation steps.**
- **Dataset expansion** - make your dataset larger by combining or concatenating open source datasets with your dataset. Choose higher quality ones.
- **Evaluation early stopping** - enable evaluation and stop when the evaluation loss increases for a few steps.
- **LoRA Alpha Scaling** - scale the alpha down after training and during inference - this will make the finetune less pronounced.
- **Weight Averaging** - literally add the original instruct model and the finetune and divide the weights by 2.
### Underfitting
- The model fails to capture the underlying patterns in the training data, often due to insufficient complexity or training duration.
**Solution:**
- **Adjust the learning rate:** If the current rate is too low, increasing it may speed up convergence, especially for short training runs. For longer runs, try lowering the learning rate instead. Test both approaches to see which works best.
- **Increase Training Epochs:** Train for more epochs, but monitor validation loss to avoid overfitting.
- **Increase LoRA Rank (`r`)** and alpha: Rank should at least equal to the alpha number, and rank should be bigger for smaller models/more complex datasets; it usually is between 4 and 64.
- **Use a More Domain-Relevant Dataset:** Ensure the training data is high-quality and directly relevant to the target task.
- **Decrease batch size to 1:** This will cause the model to update more vigorously.

# References
---
1. 
