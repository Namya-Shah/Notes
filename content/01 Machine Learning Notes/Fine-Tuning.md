---
Link:
tags:
  - ML
  - LLM
  - Fine-Tuning
---
```table-of-contents
```
# Brief Introduction
- Fine-tuning an LLM customizes its behavior, deepens its domain-expertise, and optimizes its performance for specific tasks.
- By refining a pre-trained model with specialized data, we can:
	- **Update Knowledge**: Introduce new, domain-specific information that the base model didn't originally include.
	- **Customize Behavior**: Adjust the model's tone, personality, or response style to fit specific needs or a brand voice.
	- **Optimize for Tasks**: Improve accuracy and relevance on particular tasks or queries your use-case requires.
- Combining both (fine-tuning, RAG) approaches yields the best results - leading to greater accuracy, better usability, and fewer hallucinations.
# Real-World Applications of Fine-Tuning
- **Sentiment Analysis for Finance**: Train an LLM determine if a news headline impacts a company positively or negatively, tailoring its understanding to financial context.
- **Customer Support Chatbots**: Fine-tune on past customer interactions to provide more accurate and personalized responses in a company's style and terminology.
- **Legal Document Assistance**: Fine-tune on legal texts (contracts, case law, regulations) for tasks like contract analysis, case law research, or compliance support, ensuring the model uses precise legal language.
# Benefits
## Fine-Tuning vs RAG
- *Fine-tuning can do mostly everything RAG can - but not the other way around.*
- During training, fine-tuning embeds embeds external knowledge directly into the model. This allows the model to handle niche queries, summarize documents, and maintain context without relying on an outside retrieval system.
- It is possible to retrieve fresh data with fine-tuning as well, however it is better to combine RAG with fine-tuning for efficiency.
## Task-Specific Mastery
- Fine-tuning deeply integrates domain knowledge into the model. This makes it highly effective at handling structured, repetitive, or nuanced queries, scenarios where RAG-alone systems often struggle.
## Independence from retrieval
- A fine-tuned model has no dependency on external data sources at inference time. It remains reliable even if a connected retrieval system fails or is incomplete, because all needed information is already within the model's parameters.*This self-sufficiency means fewer points of failure in production.*
## Faster Responses
- Fine-tuned models don't need to call out to an external knowledge base during generation. Skipping the retrieval step means they can produce answers much more quickly.
## Custom Behavior and Tone
- Fine-tuning allows precise control over how the model communicates. This ensures the model's responses stay consistent with a brand's voice, adhere to regulatory requirements, or match specific tone preferences.
## Reliable Performance
- Even in a hybrid setup that uses both fine-tuning and RAG, the fine-tuned model provides a reliable fallback. If the retrieval component fails to find the right information or returns incorrect data, the model's built-in knowledge can still generate a useful answer. This guarantees more consistent and robust performance for your system.
# Why You Should Combine RAG & Fine-Tuning?
- **Task-Specific Expertise**: Fine-tuning excels at specialized tasks or formats (making the model an expert in a specific area), while RAG keeps the model up-to-date with the latest external knowledge.
- **Better Adaptibility**: A fine-tuned model can still give useful answers even if the retrieval component fails or returns incomplete information. Meanwhile, RAG ensures the system stays current without requiring you to retrain the model for every new piece of data.
- **Efficiency**: Fine-tuning provides a strong foundational knowledge base within the model, and RAG handles dynamic or quickly-changing details without the need for exhaustive re-training from scratch. This balance yields an efficient workflow and reduces overall compute costs.

> [!NOTE]
> The standard method of post training is called *Supervised Fine-Tuning (SFT)*

- **Other Methods**
	- Preference Optimization (DPO, ORPO)
	- Distillation and Reinforcement Learning (RL)
# Hyperparameter Tuning
- `max_seq_length = 2048` - Controls context length. While Llama-3 supports 8192, we recommend 2048 for testing. Unsloth enables 4x longer context fine-tuning.
- `dtype = None` - Defaults to None; use `torch.float16` or `torch.bfloat16` for newer GPUs.
- `load_in_4bit = True` - Enables 4-bit quantization, reducing memory use 4x for fine-tuning. Disabling it enables LoRA 16-bit fine-tuning. You can also enable 16-bit LoRA with `load_in_16bit = True`.
- To enable full fine-tuning (FFT), set `full_finetuning = True`. For 8-bit fine-tuning, set `load_in_8bit = True`.
## Supervised Fine-Tuning
- Further trains a pre-trained model on task-specific labeled dataset (input-output pairs).
- Updates all models weights to adapt it to the new task.
- Best for tasks like sentiment analysis and text classification where labeled data is available.
## Instruction Fine-Tuning
- Trains the model using datasets pairing instructions (prompts) with expected responses.
- Helps the model generalize to new tasks and follow natural language instructions.
- Commonly used in chatbots, question answering and open-ended tasks.
## Parameter-Efficient Fine-Tuning (PEFT)
- Adjusts only a small subset of parameters, keeping most of the model unchanged.
- Methods include training adapter layers, low-rank reparameterization (LoRA) or just prompt tokens.
- Enables efficient adaptation of large models with less memory and computation -- for example, PEFT can reduce trainable parameters from tens of thousands to just a few thousand.
## Reinforcement Learning with Human Feedback
- Uses human ratings to teach a model to align outputs with human preferences.
- Involves three steps: generate outputs, train a reward model from human feedback and optimize model behavior using reinforcement learning (like PPO).
- Ideal for tasks requiring alignment with human values and nuanced preferences such as generating helpful, safe or ethical content.


# References
---
1. [[Low-Rank Adaptation (LoRA)]]
2. [[Quantized LoRA (QLoRA)]]
3. [[Parameter Tuning]]
4. 
