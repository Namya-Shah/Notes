---
Link:
tags:
  - ML
---
# Notes
Originally proposed for Machine Translation
- Use attention to boost the speed with models can be trained
![[Pasted image 20250725215448.png]]
# Stack of encoders and decoders
![[Pasted image 20250725215530.png]]
- Proposed in Research Paper [[Attention is All You Need]]
# Inside Encoder Module
![[Pasted image 20250725215616.png]]
# Inside the Encoder-Decoder module
![[Pasted image 20250725215643.png]]
- The **Encoder-Decoder Attention** is **cross-attention**
Vanishing Gradient happens when using Sigmoid function
- ChatGPT are decoder only models
# Happening inside Encoder module
![[Pasted image 20250725220443.png]]
- Each encoder receive a list of vectors each of the size 512
- The embedding only happens in the bottom-most encoder.
- The rest of the encoders receives inputs (list of vectors) from the output of the immediate lower encoder.
![[Pasted image 20250725231952.png]]
- Word in each position flows through its own path in the encoder
- There are dependencies between these paths in the self-attention layer
- The feed-forward layer does not have those dependencies
- All matrices (trainable) goes through **backpropagation**
- In **feed-forward neural network**, we have 4 times larger than `Z` matrix. So, if we have 512 weight matrix then the weight matrix for $w_1$ in feed forward network will be `512 * 4 = 2048`
- The feed-forward neural network, will convert the Z matrix of shape 512 to 2048 and then convert it back again to 512.
- The weight matrix in feed-forward neural network will be $w_1 = 512 \times 2048$, and when we convert it back $w_2 = 2048 \times 512$.
# Self-Attention
## Implementation
![[Pasted image 20250725232136.png]]
- Create three vectors from each of the encoder's input vectors
- A **Query** vector, a **Key** vector, and a **Value** vector
- Created by multiplying the embedding by three trainable matrices
- New vectors are smaller (=64) in dimension than the embedding vector (=512)
![[Pasted image 20250725232500.png]]
- **Score** each word of the input sentence against the candidate word
- Dot product of the query vector with the key vector
- Candidate: **Thinking**
![[Pasted image 20250725232512.png]]
- Divide by square root of dimension of the Key vector
- Compute softmax
- Softmax score determines how much each word will be expressed at this position
![[Pasted image 20250725232750.png]]
- Multiply each value vector with the softmax value
- Sum up the weighted value vectors
### The Three Trainable Matrix
![[Pasted image 20250725232814.png]]
- Every row in the X matrix corresponds to a word in the input sequence.
![[Pasted image 20250725232852.png]]
# Multi-Headed Attention
![[Pasted image 20250725232917.png]]
- It expands the model's ability to focus on different positions.
- It gives the attention layer multiple "representation subspaces".
- Transformers uses eight attention heads (*by default*)
![[Pasted image 20250725233047.png]]
- Eight different times with different weight matrices, we end up with eight different Z matrices.
![[Pasted image 20250725233129.png]]
- The concatenated `Z` matrix shape will be `2*64*8 = 2*512`.
- The size for `W^O` is `512*512`.
# Self Attention
![[Pasted image 20250725233216.png]]
# Representing the order of the sequence
![[Pasted image 20250805215756.png]]
- Add a positional embedding to the original embedding
- To determine the position of each word, or the distance between different words in the sequence.
> They tried many different formulas but the one given in the paper works best.
# Layer Normalization
![[Pasted image 20250805232927.png]]
- It helps in stabilizing the learning process and dramatically reducing the number of training epochs.
## Layer Normalization (At Both Modules)
![[Pasted image 20250805233041.png]]
- To learn about residual connections / skip connections: [[What is the importance of skip connections in Transformers]]
- In the decoder side, the self-attention layer is only allowed to attend to earlier positions in the output sequence.
- The "Encoder-Decoder Attention" layer works just like multiheaded self-attention, except it creates its **Queries matrix from the layer below it**, and takes the **Keys and Values matrix from the output of the encoder stack**.
# Linear and Softmax Layer
![[Pasted image 20250806002146.png]]
- The Linear layer is a simple fully connected neural network
- It produces much larger vector called a logits vector (vocab_size)
- 

# Comparing the beasts
- GPT - 2
	- Decoder-only model
- BERT
	- Encoder-only model
- Transformer XL
	- Recurrent Decoder
	- To learn more about recurrent decoder: [[Recurrent Decoder]]



---
Types of transformers
- Encoder-Decoder
	- Encoder processes text from source language
	- Decoder takes output of the final layer of encoder and attention to predict the words in target language.
- Decoder only
	- Text → Decoder 1 → Decoder 2 → … → Decoder n → output

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXf3RlYGelcrmhsR2XreMZ5O-OP21ubHua3XxDVtHiqZiQs0W4K3GsrAg9rejOjrC_ctIpNFWYIxpzNX4qPwUDo39-YUoAGeFZB5tMY6ZSf3oL3z2KHzxsbcqEP0yZLcZ_PnNxi2zg?key=ncV0JRlQ2iPTTfaeiSkQo-46)

Components of decoder block:
- Self attention
- Token wise multi-layer perceptron or feed forward neural network

# References
---
1. 