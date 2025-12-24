---
PDF: "[[attention is all you need.pdf]]"
tags:
  - "#Research-Paper"
---
- **"The fundamental constraint of sequential computation, however remains."** - Pg. 2
	- In RNN-based models (including LSTMs and GRUs), the processing of input data happens step-by-step, where the output at time step t depends on the result from time step t-1, which:
		- **Prevents parallelization** across sequence positions during training (you can't compute the state at t+1 before computing the state at t).
		- **Slows down computation**, especially for long sequences.
		- **Limits scalability** due to memory and time constraints.
> [!IMPORTANT] Why Self-Attention was required?
> Even though, researchers had developed tricks (like factorization and conditional computation) to make RNNs more efficient, this inherent need to process data in order (sequentially) was still a bottleneck
>
> The transformer architecture, addresses this problem by completely removing recurrence and instead using self-attention mechanisms that allow parallel processing across the entire sequence.

- What does "attention" mean?
	- A method that lets the model look at all positions in a sequence at once.
- **"to grow global dependencies between input and output"** - Pg. 2
	- The attention mechanism helps the model learn relationships between any two parts of the sequence, regardless of how far apart they are (called global dependencies). This is important in tasks like translation, where a word at the beginning of a sentence may relate to a word at the end.
- **"The goal of reducing sequential computation also forms the foundation of the Extended Neural GPU, ByteNet and ConvS2S, all of which use convolutional neural networks as basic building block, computing hidden representations in parallel for all input and output positions. In these models, the number of operations required to relate signals from two arbitrary input or output positions grows in the distance between positions, linearly for ConvS2S and logarithmically for ByteNet. This makes it more difficult to learn dependencies between distant positions"** - Pg. 2
	- Earlier models like **ConvS2S** and **ByteNet** used **CNNs** to process sequences in parallel, avoiding the slow step-by-step processing of **RNNs**. But they still had a limitation: to understand long-distance relationships in a sequence, they needed many convolution layers -- which makes learning those relationships harder.
	- This is one of the problems the **Transformer's attention mechanism** was designed to solve -- by **directly connecting any two positions**, regardless of distance, in just one step
- **End-to-end memory networks are based on a recurrent attention mechanism instead of sequence aligned recurrence** - Pg. 2
	- End-to-end memory networks
		- This refers to a class of models designed to **remember and retrieve information over time**, often used for tasks like question answering
	- are based on a recurrent attention mechanism
		- These models use attention repeatedly in a loop-like fashion to focus on relevant parts of their memory multiple times -- kind of like reading a document several times to find an answer.
	- instead of sequence-aligned recurrence
		- Traditional RNNs (like LSTMs and GRUs) use sequence-aligned recurrence, meaning:
			- They process the input one step at a time, in order
			- Each step depends on the one before it (aligned with the sequence order)
- **To the best of our knowledge, however, the Transformer is the first transduction model relying entirely on self-attention to compute representations of its input and output without using sequence aligned RNNs or convolution.** - Pg. 2
	- A **transduction model** is one that translates or converts one sequence into another -- for example, turning English into French. The transformer is such a model.
	- The Transformer is unique because it uses only self-attention, with no recurrence (RNNs) and no convolutions (CNNs).
	- Instead of processing data sequentially or locally, the Transformer uses self-attention to build **internal understanding (representations)** of both the input (like a sentence) and the output (like its translation)
	- The transformer completely avoids traditional building blocks used before -- RNNs (which process one word at a time) and CNNs (which look at local neighborhoods).
> [!NOTE] Autoregressive model in Transformer
> In a transformer, **autoregressive (AR)** means the model generates a sequence of output tokens one at a time, using the previously generated tokens to predict the next one. Essentially, it looks backward at its own output to determine what should come next. This approach is common in the decoder part of transformer models, especially for tasks like text generation.

---
![[Pasted image 20250727143323.png|400x400]]
- **"Why do we use this connection and not pass through multi-head attention and then layer normalization?"**
	- We **do** pass through multi-head attention (or FFN)
	- The residual connection adds the original input to the sublayer's output
	- Then the combined result is normalized
	- This pattern is used because:
		- Residuals help with **gradient flow** in deep networks.
		- LayerNorm **stabilizes training** and prevents activations from exploding or vanishing
# Overview
- The Transformer is a **sequence-to-sequence model** used for tasks like machine translation (e.g., English to German). It consists of:
	- An Encoder: Reads the input sentence (e.g., English)
	- A Decoder: Produces the output sentence (e.g., German), one word at a time.
	- Attention Mechanisms: The core of the model, used to connect and relate different positions in the sequences.
- Encoder (Left Side)
	- Input Embedding
		- What: The input tokens (e.g., \["The", "dog", "ran"\]) are converted to dense vectors of fixed size (say, 512 dimensions).
		- Why: Neural networks cannot process words directly -- embeddings allow words to be expressed numerically in a form the model can learn from.
	- Positional Encoding
		- What: Add a position vector to each word embedding. For example, the word "dog" at position 2 has an encoding that reflects that.
		- Why: Unlike RNNs, the Transformer processes all words in parallel, so it needs explicit information about word order. Positional encoding injects that sequence order into the model.
	- Multi-Head Self-Attention
		- What: Each word in the sequence looks at (or "attends to") all the other words, using multiple attention heads. It builds contextual understanding.
		- Why: This allows the model to capture relationships across the sentence -- for example, "dog" might attend to "ran" to understand it as the subject of action.
	- Add & Norm (Residual + Layer Normalization)
		- What: The original input to the self-attention layer is added back to the output (residual connection), then normalized.
		- Why: Residual connections prevent vanishing gradients and help retain original signal, while normalization stabilizes and speeds up training.
	- Feed-Forward Neural Network Layer
		- What: A simple neural network (typically two dense layers with ReLU) applied to each position independently.
		- Why: After the model has context from attention, this layer allows it to transform that information further -- like filtering or combining signals.
- Decoder (Right Side)
	- The decoder generates output tokens one at a time, using everything it has seen so far. It uses a similar structure to the encoder with a few differences.
	- Output Embedding + Positional Encoding
		- What: The generated output tokens (e.g., "Der", "Hund") are turned into embeddings with position encodings added.
		- Why: Same as encoder -- allows model to process words with position info.
	- Masked Multi-Head Self-Attention
		- What: Like encoder attention, but masked to prevent each position from seeing future words.
		- Why: To preserve the auto-regressive property: when generates a word, the model must not peek ahead at the next word.
	- Encoder-Decoder Attention (Multi-Head)
		- What: The decoder attends over all encoder outputs to gather relevant info from the input sentence.
		- Why: This step connects input and output. E.g., when generating "Hund", the decoder may attend to "dog" in the input to translate correctly.
- Final Step: Linear + Softmax
	- Linear: Projects the output from the decoder to the size of the vocabulary (e.g., 37,000 words). Also known as logits.
	- Softmax: Converts these scores into probabilities for the next word.
	- Why: To select the next word during generation. The word with the highest probability becomes the next predicted word.
# Analogy
- Think of a conference translator:
	- The encoder listens to the full English sentence and understands the meaning (all at once).
	- The decoder speaks German, generating words one by one, referring to the internal understanding and what it has said so far.
	- Attention is like the translator focusing on different parts of the sentences as they speak -- sometimes jumping back to the beginning to recall a noun or verb.
---
- **"The output is computed as a weighted sum of the values, where the weight assigned to each value is computed by a compatibility function of the query with the corresponding key"** - Pg. 3-4
	- Query (Q): The vector representing the item we're focusing on (e.g., a specific word in the decoder).
	- Key (K): The vectors representing all the possible items we might look at (e.g., all words in the input).
	- Value (V): The vectors containing the actual information to be passed on.
	- For each query, we compare it to all the keys, and use the similarity to determine how much attention (or weight) to give to each value.
	- The "compatibility function" is usually a dot product between the query and key:
		- $\text{score} = Q \cdot K^T$
	- The result is passed through a softmax to normalize the weights into probabilities:
		- $\text{weights = softmax}(\frac{Q \cdot K^T}{\sqrt{d_k}})$
	- Then we use these weights to compute the weighted sum of the value vectors:
		- $\text{output} = \sum_i \text{weight}_i \cdot V_i$
# Scaled Dot-Product Attention
![[Pasted image 20250727152826.png|400x400]]
- Dot-product attention is identical to our algorithm, except for the scaling factor of $\frac{1}{\sqrt{d_k}}$.
- Additive attention computes the compatibility function using a feed-forward network with a single hidden layer.
> [!NOTE] NOTE
> Dot-product attention is much faster and more space-efficient in practice, since it can be implemented using highly optimized matrix multiplication code.
>
> Additive attention outperforms dot product attention without scaling for larger values of $d_k$. 

> [!IMPORTANT] IMPORTANT
> For large values of $d_k$, the dot products grow large in magnitude, pushing the softmax function into regions where it has extremely small gradients. To counteract this effect, we scale the dot products by $\frac{1}{\sqrt{d_k}}$.
# Multi-Head Attention
![[Pasted image 20250727152853.png|400x400]]
- Queries & Keys will have same dimension $d_k$ and values will have different dimension $d_v$.
$$
\text{MultiHead}(Q,K,V) = \text{Concat}(head_1, head_2, ..., head_h)W^O
$$
$$
\text{where} \ head_i = \text{Attention}(QW_i^Q, KW_i^K, VW_i^V)
$$

> [!EXAMPLE] EXAMPLE
> Suppose if we have $d_{model}$ = 512. It will be computationally expensive. So, we split it into parallel attention layers. Suppose if we have 8 parallel attention layers, or heads. The new dimensions will be $d_k = d_v = \frac{d_{model}}{h} = \frac{512}{8} = 64$
>
> Due to the reduced dimension of each head, the total computation cost is similar to that of single-head attention with full dimensionality.

# Applications
- In "encoder-decoder attention" layers, the queries come from the previous decoder layer, and the memory keys and values come from the output of the encoder. This allows every position in the decoder to attend over all positions in the input sequence.
- The encoder contains self-attention layers. In a self-attention layer all of the keys, values and queries come from the same place, in this case, the output of the previous layer in the encoder. Each position in the encoder can attend to all positions in the previous layer of the encoder.
- Self-attention layers in the decoder allow each position in the decoder to attend to all positions in the decoder up to and including that position. We prevent rightward information flow in the decoder to preserve the auto-regressive property. We implement this inside of scaled dot-product attention by masking out (setting to $-\infty$) all values in the input of the softmax which correspond to illegal connections.

- **In addition to attention sub-layers, each of the layers in our encoder and decoder contains a fully connected feed-forward network, which is applied to each position separately and identically. This consists of two linear transformations with a ReLU activation in between.** - Pg. 5
	- The FFN is applied to each token (position in the sequence) independently. Each word/token representation is updated by passing it through the exact same feed-forward network, but no information is shared between positions in this step.
	- There's no interaction between tokens in this step.
	- The same weights (within that layer) are used across all positions.
	- The 2048 in the inner layer dimensionality is by design choice as it has wider hidden layer which gives more capacity to network to learn rich transformations. It is sometimes called **bottleneck** or **expansion-compression design**.
$$
\text{FFN}(x) = \max(0, xW_1+b_1)W_2 + b_2
$$
- $x$: Input at a specific position (a vector of size $d_{model}$)
- $W_1, W_2$: Learnable parameter matrices
- $b_1, b_2$: Learnable biases
- $\max(0, \cdot)$: ReLU activation
![[Pasted image 20250727230044.png]]
- **Self-Attention**
	- The full attention mechanism used in Transformer models.
	- Complexity per Layer - $O(n^2 \cdot d)$
		- $n$: sequence length
		- $d$: embedding dimension
		- Each token attends to every other token -> $n \times n$ attention scores, each of dimension $d$.
	- Sequential Operations - $O(1)$
		- All tokens can attend to each other in parallel
		- Transformer allows full parallelism during training.
	- Maximum Path Length - $O(1)$
		- Every token can directly attend to any other -- instant long-range dependency.
	- Best for **short to moderate-length sequences** with need for full context, like translation or summarization. May **need optimization** (e.g., sparse or linear attention) for **long sequences**.
	- Use Cases
		- Best for tasks requiring global context and parallel training, like translation, summarization, and language modeling.
- **Recurrent**
	- Each token is processed one after the other in time -- sequentially.
	- Complexity per Layer - $O(n \cdot d^2)$
		- Each of the $n$ tokens goes through a matrix multiplication of size $d \times d$.
	- Sequential Operations - $O(n)$
		- Must process token 1 -> then token 2 -> etc.
		- Cannot parallelize across positions.
	- Maximum Path Length - $O(n)$
		- Token 1 must go through Token 2 -> 3 -> ... -> n -- long path for distant dependencies.
	- Computation is cheaper than attention in theory, but **parallelism bottleneck makes it much slower in practice**. Not preferred for large-scale tasks anymore. Also simple and effective, for **time-series** and **streaming data**.
	- Use Cases
		- Suitable for time-dependent or streaming data where sequence order is critical, such as speech recognition or sensor data.
- **Convolutional**
	- Uses convolutional filters (e.g., in ConvS2S, ByteNet) to capture nearby dependencies.
	- Complexity per Layer - $O(k \cdot n \cdot d^2)$
		- $k$: kernel size (window size for convolution)
		- Each token processes $k$ neighbors, using a weight matrix of size $d \times d$.
	- Sequential Operations - $O(1)$
		- All positions can compute in parallel -- convolutions are highly parallelizable
	- Maximum Path Length - $O(\log_kn)$
		- Distant positions are connected in logarithmic depth by stacking dilated convolutions.
	- Better than RNNs for parallelism, but still **requires many layers** to capture long-range info. Cost is controllable by adjusting $k$, but path length increases.
	- Use Cases
		- Ideal for tasks focusing on local patterns with high-speed parallelism, like audio processing or character-level modeling.
- **Self-Attention (Restricted)**
	- A limited version of self-attention that only attends to a local neighborhood (window) around each token.
	- Complexity per Layer - $O(r \cdot n \cdot d)$
		- $r$: local attention window size (much smaller than $n$)
		- Reduces cost compared to full attention by only computing attention within a local window.
	- Sequential Operations - $O(1)$
		- Like convolutions, this can also be done in parallel.
	- Maximum Path Length - $O(n/r)$
		- It takes multiple layers of restricted attention to connect distant positions -- slower than full attention.
	- Use Cases
		- Designed for very long sequences (e.g., long documents, genome data), where efficiency outweighs the need for full global attention.
> [!NOTE] NOTE
> **Complexity per layer**: This represents the amount of computation required for each layer.
>  
> **Sequential Operations**: This measures how many operations must be done sequentially, i.e., cannot be parallelized
> 
> **Maximum Path Length**: This measures how quickly information can flow from one part of the sequence to another.

> [!IMPORTANT] IMPORTANT
> Even though transformers' are quadratic in compute $O(n^2)$, the ability to connect all tokens in one step, and train everything in parallel, makes it extremely powerful.

# Positional Encodings
- As model contains no recurrence and no convolution, we add "positional encodings" to the input embeddings at the bottoms of the encoder and decoder stacks.
- The positional encodings have the same dimension $d_{model}$ as the embeddings, so that the two can be summed.
$$
PE_{(pos, 2i)} = sin(\frac{pos}{10000^{\frac{2i}{d_{model}}}})
$$
$$
PE_{(pos,2i+1)} = cos(\frac{pos}{10000^{\frac{2i}{d_{model}}}})
$$
where,
$pos$ is the position of the word in the sequence
$i$ is the index of the dimension
$\frac{2i}{2i+1}$ - even and odd dimensions of the positional encoding
$d_{model}$ - the dimension of the model (e.g., 512, 768) -- how big each token vector is
10000 - a large constant to provide different frequencies
> Each dimension of the positional encoding corresponds to a sinusoid.
- The wavelengths form a geometric progression from $2 \pi$ to $10000 \cdot 2 \pi$.
> [!IMPORTANT] REMEMBER
> Unlike RNNs and CNNs, the Transformer has no built-in notion of sequence order -- it processes all tokens in parallel.
> 
> As we know language is inherently sequential -- "The cat chased the dog" is not the same as "The dog chased the cat".
>
> So, we need a way to inject position information into the model so it knows which word came first, second, third, etc.
- Each position in the sequence is mapped to a unique vector of size $d_{model}$, using sine and cosine functions of different frequencies.
- **Why sine and cosine?**
	- These functions are **periodic**, which helps capture **relative positions**.
	- The combination of many frequencies allows the model to **interpolate positions** and **generalize to longer sequences**.
- For $\frac{1}{10000^{\frac{2i}{d_{model}}}}$:
	- For `i = 0`, the frequency is high
	- As `i` increases, the frequency decreases
	- This makes low dimensions capture fine-grained position differences, and higher dimensions capture **coarser** differences.
- Even indices use sine
- Odd indices use cosine
- **"We chose the sinusoidal version because it may allow the model to extrapolate to sequence lengths longer than the ones encountered during training."** - Pg. 6
	- The pattern they create can be mathematically continued -- or extrapolated -- to longer sequences than those seen during training. In other words, even if the model is given a sequence longer than any it saw in its training data, it can still compute positional encodings for new positions using the same formula.
	- As sine and cosine functions do not depend on a learned lookup table (which would have a fixed size), but instead rely on a formula that works for any position index.
	- So, the model is not limited by the maximum sequence length it was trained on.