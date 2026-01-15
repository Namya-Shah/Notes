---
Link:
tags:
  - RAG
---
# Brief Introduction
- **Chroma works great for small to medium datasets**, but large-scale RAG systems need something more performance-focused.
- **FAISS (Facebook AI Similarity Search)** is built for fast, scalable similarity search over millions of high-dimensional vectors.
- Unlike Chroma's database-like experience, **FAISS acts as a high-performance vector search engine**, optimized for speed and efficiency.
- FAISS is commonly used when datasets are huge and you need **fine-grained control over indexing and retrieval performance**.
- Both solve the same problem, but with different priorities: **Chroma for simplicity and persistence, FAISS for speed and scale** -- and next, we'll implement FAISS in LangChain.
- FAISS is commonly used when you need very fast similarity search. You're dealing with large scale embedding datasets and you want fine grain control over indexing strategies and performance tradeoffs.
- In real-world systems, FAISS often powers the retrieval layer when scale becomes critical specially in research or enterprise applications.

# References
---
1. 
