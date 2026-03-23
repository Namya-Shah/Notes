---
Location:
  - YouTube
Channel:
  - "[[Neural Breakdown with AVB]]"
Date: 2025-07-15 10:33
Topics:
  - "[[Large Language Models]]"
  - "[[Fine-Tuning]]"
tags:
  - YouTube
---
# Video
<iframe width="560" height="315" src="https://www.youtube.com/embed/bZcKYiwtw1I?si=GxhRH7bPYerhYKrr" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

# Notes
- A **language model** is a probabilistic model of text.
	- **Example:** What is the probability of a particular word occurring in a given sentence?
- **Masked Language Models** predict the probability of a word (token) given surrounding words.
- **Causal Language Models** predict the NEXT WORD given a prefix sequence of words.
- **Tokenizers** convert the input string into a list of integer tokens that would be input into the LM.
- **Padding** allows the input tokens to be a rectangular tensor i.e., all inputs in the batch is of the same length.
- Tokenizer has two outputs: `input_id`, `attention_mask`
	- **Attention Mask** is the mask where we have binary vectors where 1 -> actual token and 0 -> padded token
- **Instruction Tuning**
	- Many LMs are finetuned to follow user instructions in a chat-like format
- `apply_chat_template()`
	- Converts prompt from chat message format to a single string sequence
- `model.generate()`
	- Inputs the tokenized tensor and generates new tokens using LM
- `add_generation_prompt` -> Boolean
	- Prompts the assistant to respond
- `continue_final_message` -> Boolean
	- Allows you to continue LM response from a fixed prefix
- **Role -> System**
	- Generally devs use the "system" role to give high level instructions to LM on how to behave.
- **Role -> User**
	- Generally the user query is passed into the LM with the role "user"
- **Simple Prompting** does not give us good results for this classification task
- In Machine Learning, the **train set** is used to train or finetune the model and the **test set** is used to evaluate the model, this data is NOT used for training.
- `model(input)`
	- Directly passing input does one step of generation by outputting the probabilities of next word.
- **Vocabulary**
	- Language models store millions of subwords that together form the model's vocabulary.
- **Logits** are the raw, unnormalized scores that the model produces to represent the model's confidence for the next word in the input sequence.
- The **softmax** operation converts the logits into a probability distribution, i.e., what is the probability of a given word/subword to be the next token?
- *"you"* and *" you"* are treated as different tokens
- `argmax()` over the logits will return the index of the vocabulary that the model is most confident in.
- While finetuning a pretrained model, ideally we should be applying loss over our answer and not the entire sequence (which also includes the prompt).
-  Logits are of shape: `[Batch Size x Sequence Length x Vocab Size]`
- **Cross Entropy Loss** is a common loss function used to calculate the distance between the predicted logits and the target labels.
	- The loss becomes low when the model correctly predicts the answer for the question
	- The loss is higher depending on how far the network's outputs logits are to the target distribution.
- Optimizer updates the weights of the network after backprop to reduce the loss
- **Overfitting** on a small dataset is a great indicator that your learning pipeline is bug-free. You can train on larger datasets once you are confident there aren't bugs.
- 


