---
Link:
tags:
  - RAG
---
# Introduction
**Retrieval-Augmented Generation (RAG)** is an AI technique that improves language model responses by retrieving relevant external information from a knowledge source (like documents or databases) and combining it with the model's generative output to produce more accurate and grounded answers.
# Why is RAG better than only LLM?
- Helps mitigate hallucinations
- Easy and reliable way to manage knowledge
- Give model new or proprietary information
# What Document Loaders Actually Do
- Convert raw files -> standardized LangChain "Document" format
- Extract text cleanly from multiple file types
- Preserve metadata like filenames, URLs, or page numbers
- Serve as the first step of every RAG workflow.
# 5-Step RAG Framework
- **Step 1:** Scope the MVP
	- Project Discovery
	- Who are the audience?
	- Use case(s)?
	- Inventory (picking the source raw data)
- **Step 2:** Create Golden Dataset
	- Giving a Q&A type of dataset
	- User Input | "Correct" Result
	- Use real-world queries
	- Synthetic Queries (Inventory -> LLM -> Queries)
		- Iterate on query gen prompt
		- Generate queries for personas + use cases
		- Ground in real-world data (if available)
- **Step 3:** Build v0 Retrieval System
	- Docs -> Database -> Vector Search
	- Docs -> Database -> Lexical Search
	- Docs -> Database -> Vector Search | Lexical Search
	- Evaluating baselines
		- Precision
			- Percentage of retrieved chunks which are relevant
			- $\frac{TP}{TP+FP}$
				- $TP$ = Relevant & retrieved
				- $FP$ = Not relevant & retrieved
		- Recall@k
			- Percentage of all relevant chunks that are retrieved
			- $\frac{N_{r\in k}}{N_r}$
				- $N_{r\in k}$ = Num relevant in top k
				- $N_r$ = Total num relevant
		- Mean Reciprocal Rank (MRR)
			- Captures performance of a set of queries based on ranking
			- $\frac{1}{|Q|}\sum_{i=1}^{|Q|}\frac{1}{rank_i}$
				- $|Q|$ = Num queries
				- $rank_i$ = Rank of top relevant chunk
- **Step 4:** Build v0 Answer System
	- ![[Pasted image 20260103182239.png]]
- **Step 5:** Run experiments
	- Design project for experimentation, not production
	- Change one thing at a time

# References
---
1. [[TextLoaders]]
2. [[PyPDFLoader]]
3. [[DirectoryLoader]]
4. [[WebBaseLoader]]
5. [[CSVLoader]]
6. [[TextSplitters]]
7. [[Embeddings]]
8. [[Retrievers]]
