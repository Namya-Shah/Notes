---
Lecture Date: 2025-08-02
Presentation: 
Links: 
Subject:
  - "[[EM 622 - GALLM]]"
References: 
tags:
  - EM622
---
```table-of-contents
```
In ELMo, we train separate left-to-right and right-to-left LMs and then, they are stacked and applied to "pre-trained embeddings"
![[Pasted image 20250806093738.png]]
- It is not true bi-directional
# GPT Transformer Model
![[Pasted image 20250806094005.png]]
- OpenAI suggested to replace LSTM to Transformer. 
- On the **left side**, it shows that we pass one word and predict the other. We train the model fully and then we move to **right side** to fine tune the model on specific classification task.
- Long sequences don't work with RNNs but can work with Transformers
# Problems with Previous Methods
- **Existing contextual LMs** only use left context or right context, but language understanding is bidirectional.
- Why are LMs unidirectional?
	- Directionality is needed to generate a well-formed probability distribution
	- Words can "see themselves" in a bidirectional encoder.
- **The birth of BERT took place**
# BERT
- BERT generates a language model by training in both directions which gives words more context.
- BERT provided a way to more accurately pre-train models with less data
- It involved a pre-training and fine-tuning stages
- It is based on the Transformer architecture (encoders)
- In $\text{BERT}_\text{BASE}$, we have **12 encoder layers**
- In $\text{BERT}_\text{LARGE}$, we have **24 encoder layers**
![[Pasted image 20250806112950.png]]
- For one encoder, we will get one embedding vector of ($1 \times 512$) which if we have 10 words will be a matrix of ($10 \times 512$).
- It is very contextual in nature. If we have two similar words at the starting (suppose bank), it will have same embedding vector but as we move up through encoding layers, they will become different. (**Contextual Learning**)
- Encoder-only LLMs can't generate anything. So LLMs are either decoder-based or encoder-decoder based LLMs
# Input Representation
- BERT works by taking inputs (sequence of tokens), which are converted into vectors.
- Three transformative operations are first performed on the input tokens before feeding to the network.
	- Token embeddings: Add [CLS] and [SEP] to the input tokens
		- CLS -> Classification Token
		- SEP -> Separator Token
	- Segment embeddings: Add sentence markers to the input tokens
		- Whether the word belongs to first sentence or other.
	- Positional embeddings: Add position indicators to the input tokens.
# Pretraining Objective: Masked LM
- Mask out **k%** of the input words, and then predict the masked words
	- k = 15 (works the best as per the paper)
	- ![[Pasted image 20250806115038.png]]
	- Too little masking: Too expensive to train
	- Too much masking: Not enough context
- **Problem:** Mask token never seen at fine-tuning
- **Solution:** 15% of the words to predict, but don't replace with [MASK] 100% of the time.
- **Instead:**
	- **80% of the time, replace with [MASK]**
		- went to the store -> went to the [MASK]
	- **10% of the time, replace random word**
		- went to the store -> went to the running
	- **10% of the time, keep same**
		- went to the store -> went to the store
# Pretraining Objective: Next Sentence Prediction
- To learn relationships between sentences, predict whether Sentence B is actual sentence that proceeds Sentence A, or a random sentence.
![[Pasted image 20250806115816.png]]
- 50% of the time the second sentence comes after the first one
- 50% of the time it is a random sentence from the full corpus
# Fine-tuning
- The process of using BERT for a specific task is known as fine-tuning
- To fine-tune the BERT pre-trained model on our dataset, we do so by just adding a single layer on top of the core model.
- ![[Pasted image 20250806120318.png]]
	- The `C` token predicts if the sentence is next sentence or not. We pass it in linear layer and then softmax function. If the value comes out close to 0, we say that the sentence is not the next sentence and if the value comes out close to 1, we say that the sentence is the next sentence.
	- `C` is a vector
	- Difference between $T_1$ and $E_1$
		- 
- ![[Pasted image 20250806121146.png]]
# Conclusions
- Empirical results from BERT are great, but biggest impact on the field is:
	- With pre-training, bigger == better, without clear limits (so far).
- Unclear if adding things on top of BERT really helps by very much.
	- Good for people and companies building NLP systems
	- Not necessary a "good thing" for researchers, but important.

---
# Research Papers
BERT: [1810.04805](https://arxiv.org/abs/1810.04805)
ELMo: [1802.05365](https://arxiv.org/abs/1802.05365)
Semi-Supervised Learning: [1511.01432](https://arxiv.org/abs/1511.01432)
[Improving Language Understanding by Generative Pre-Training, OpenAI](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf)

