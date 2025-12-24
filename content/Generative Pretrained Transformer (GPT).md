---
Link: 
tags:
---
# Notes
- Generative
	- These bots are used to generate new text
- Pre-trained
	- Pre-trained refers to how the model went through a process of learning
- Transformer
	- A specific kind of neural network, used for machine learning
- **Examples to use transformers**
	- voice-to-text
	- text-to-voice
	- text-to-image
- Transformers take in an input text along with images or audio, which then is processed and probability distributions are generated which shows which word can come next.
- In images, we have patches or group of pixels. In audio, we have chunks of audio
- The matrices is passed through a multi layer perceptron or feed forward neural network
> In the *attention part*, the vectors talk to each other and not in **feed forward neural network**
- In multi-layer perceptron, the vectors do the operations in parallel
- We keep ==repeating attention and feed forward neural network== till we get an output where the **meaning of the passage is shifted to the last vector**.
- After the above step, we perform a operation on the last vector that produces a probability distribution over all possible tokens
- ==**GPT-3 was trained upon 175,181,291,520 (~ 175 billion) parameters which are organized into 27,938 (~ 28000) matrices**==
> [!NOTE] Word Embeddings
> Word vectors have multiple dimensions, it matters to work in a space that has a lot of distinct directions.
- Dot product
	- Positive: when two vectors point in similar direction
	- Zero: when two vectors are perpendicular
	- Negative: when two vectors are opposite
> [!QUESTION]
> Why does plural words appear together than singular words? E.g., cat & cats -> -ve | rats & cats -> +ve

**Embedding matrix**
- Embedding tokens * Embedding dimension
	- Embedding tokens (50,257, GPT-3)
	- Embedding dimension (12,288, GPT-3)
> [!NOTE] Transformers
> Transformers also encode information about position of word.

> [!QUESTION]
> Why don't we just squeeze it into 1-dimension, so that it can see all the words and perform accordingly?

> [!NOTE] Context Size
> The network can only process a fixed number of vectors at a time, known as its context size.

> [!IMPORTANT] Context Size
> The **context size** limits how much text the transformer can incorporate when it's making a prediction of the next word.

# Unembedding matrix
- The matrix is initialized with random values and learns/updates while learning
# Softmax with temperature
**Formula**
$$
e^{x_1/T}/\sum_{n=0}^{N-1}e^{x_n/T}
$$
- As we **increase temperature**, the weights that have lower logits will increase significantly, making the distribution more uniform and vice-versa.
- Associate each token with high-dimensional vector, what we call embedding
> [!NOTE] Transformer
> The aim of a transformer is to progressively adjust these embeddings.

# Example for word vector
![[Pasted image 20250722190628.png]]
- **mole** would have same word vector because the initial token embedding is effectively a lookup table with no reference to the context.
> The attention block allows the model to move information encoded in one embedding to that of another, potentially ones that are quite far away, and potentially with information that's much richer than just a single word.
- In GPT example, we always apply masking to prevent later tokens from influencing earlier ones.
> [!IMPORTANT]
> Attention pattern size is equal to the square of the context size.
-  # value parameters = # query params + # key params
![[Pasted image 20250722220828.png]]
- Cross attention, where query is defined by one language and key is defined by another language.
> [!QUESTION] Attention
> Does the weights of a specific word gets updated by the context words? If no, then how does it come to know that the context?
> **Answer**: 
# Some important points
- The value vectors inside an attention head would have the same dimension as the embedding space.
- Saving on computation by instead running the weighted sums on the smaller intermediate outputs produced by the value-down matrices.
- Use only the value-down matrix to produce a sequence of 128-dimensional vectors inside each head. Taking weighted sums of these with the attention pattern which means that the head will output a single 128-dimensional vector for each position in the context.
- Multiplying each of those by the head's value-up matrix to get a 12,288 dimensional vector that can be added to the embedding in that position.
# Cross Attention
- Cross attention involves models that process two different types of data, like text in one language and text in another language.
# References
---
1. 
