---
Lecture Date: "2025-08-26"
Presentation: 
Links: 
Subject: 
References: 
tags:
---
```table-of-contents
```
# Word Representations
## Traditional Word Embeddings
- Traditional word embeddings represent each word with fixed vector regardless of context.
- **TLDR:** These embeddings are context-free
## Contextual Word Embeddings
- Contextual word embeddings generate word vectors based on context.
- **TLDR:** These representations are contextualized, meaning the same word can have different embeddings depending on surrounding words.
# Problems with Previous Methods
- **Existing contextual LMs** only use left context or right context, but language understanding is bidirectional.
## Why are LMs unidirectional?
- Directionality is needed to generate a well-formed probability distribution.
- Words can "see themselves" in a bidirectional encoder.
# BERT
- BERT trains the language model in both directions which gives word more context.
- BERT provided a way to more accurately pre-train models with less data.
- It involved a pre-training and fine-tuning stages.
- It is based on the Transformer architecture (encoders)
# Input Representation
- BERT works by taking inputs (sequence of tokens), which are converted into vectors
- Three transformative operations are first performed on the input tokens before feeding to the network.
	- **Token embeddings:** Add [CLS] and [SEP] to the input tokens
	- **Segment embeddings:** Add sentence markers to the input tokens
	- **Positional embeddings:** Add position indicators to the input tokens
![[Pasted image 20250826125837.png]]
- Use 30,000 WordPiece vocabulary on input.
- Each token is sum of three embeddings
- Single sequence is much more efficient.
# Pretraining Objective
## Masked LM
- Mask out k% of the input words, and then predict the masked words.
![[Pasted image 20250826130239.png]]
- Too little masking: Too expensive to train
- Too much masking: Not enough context
- **Problem:** Mask token never seen at fine-tuning
- **Solution:** 15% of the words to predict, but don't replace with [MASK] 100% of the time.
- Instead:
	- 80% of the time, replace with [MASK]
		- ![[Pasted image 20250826131546.png]]
	- 10% of the time, replace random word
		- ![[Pasted image 20250826131609.png]]
	- 10% of the time, keep same
		- ![[Pasted image 20250826131625.png]]
## Next Sentence Prediction
- To learn relationships between sentences, predict whether Sentence B is actual sentence that proceeds Sentence A, or a random sentence
![[Pasted image 20250826131753.png]]
# Model Architecture
- Transformer Encoder
- Data: Wikipedia (2.5B) + BookCorpus (800M)
- Training Time: 1M steps (~40 epochs)
- Optimizer: AdamW, 1e-4 learning rate, linear decay
- **BERT Base**: 12 layer, 768 hidden, 12 head
- **BERT Large**: 24 layer, 1024 hidden, 16 head
- Trained on 4x4 or 8x8 TPU slice for 4 days
# Fine Tuning
- The process of using BERT for a specific task is known as fine-tuning
- To fine-tune the BERT pre-trained model on our dataset, we do so by just adding a single layer on top of the core model.
![[Pasted image 20250826132211.png]]
![[Pasted image 20250826132228.png]]
# Conclusions
- Empirical results from BERT are great, but biggest impact on the field is:
- With pre-training, bigger == better, without clear limits (so far).
- Unclear if adding things on top of BERT really helps by very much.
	- Good for people and companies building NLP systems.
	- Not necessary a "good thing" for researchers, but important