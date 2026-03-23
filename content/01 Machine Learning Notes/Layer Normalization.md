---
Link:
tags:
  - ML
---
# Brief Introduction
![[Pasted image 20250725233940.png]]
- It helps in stabilizing the learning process and dramatically reducing the number of training epochs.
# At both modules (Encoder-Decoder)
![[Pasted image 20250725234033.png]]
# The Decoder Side
- In the decoder, the self-attention layer is only allowed to attend to earlier positions in the output sequence.
- The "Encoder-Decoder Attention" layer works just like multiheaded self-attention, except it creates its **Queries matrix from the layer below it**, and takes the **Keys and Values matrix from the output of the encoder stack**.
# The Linear and Softmax Layer
![[Pasted image 20250725234609.png]]
- The linear layer is a simple fully connected neural network
- It produces a much larger vector called a **logits vector**
- The weight matrix will have size of 512 x 30k (vocab size)
- 

# References
---
1. 
