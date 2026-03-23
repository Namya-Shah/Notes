---
Link:
tags:
  - ML
---
# Brief Introduction
![[Pasted image 20250721002011.png]]
- Links two recurrent networks
- Encoder summarizes the input into a context variable
![[Pasted image 20250721002054.png]]
- The model weights are going to be trained in such a way that it knows after which step it has to start decoding
- The decoder will stop generating when it gets the end of token.
# Different types of RNNs
![[Pasted image 20250721002201.png]]
- Many-to-many (last one): Recognizing the part of speech
- Many-to-many (second last): Machine Translation (Translator)
- Many-to-one: Sentiment Analysis
- One-to-many: Image Capturing (Passing one image as input and generating text), Text Generation (one word generates the essay)
# The current limitations
- Capturing dependencies in long data sequences
- Finding connections between long input and output sentences composed of dozens of words
# Attention mechanism
It allowing to focus on certain parts of the input sequence when predicting a certain part of the output sequence.
![[Pasted image 20250721002529.png]]
> Representing the entire input sequence $x_1, x_2, x_3$ and $x_4$ as a single vector $c$.
# RNNs with an attention mechanism
![[Pasted image 20250721002723.png]]
Decoder states: $s_0, s_1, s_2, s_3$
Attention output: $c_1, c_2, c_3, c_4$
Encoder output: $h_1, h_2, h_3, h_4$
> Attention output is called **context vector**
- $s_0$ can be any random value
# The context vectors
- The context vectors enable the decoder to focus on certain parts of the input when predicting its output.
- Each context vector is a weighted sum of the encoder's output vectors $h_1, h_2, h_3, h_4$
![[Pasted image 20250721003033.png]]
$$
\alpha_{ij} = \frac{\exp(e_{ij})}{\sum_{k=1}^4 \exp(e_{ik})}
$$
$$
e_{ij} = fc(s_{i-1}, h_j)
$$
$fc$ -> fully connected layer
# A single network learning the attention weights
![[Pasted image 20250721003301.png]]
# Backpropagation


# References
---
1. 
