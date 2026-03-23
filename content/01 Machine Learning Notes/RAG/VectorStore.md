---
Link:
tags:
  - RAG
---
# Brief Introduction
- Specialized databases (like Pinecone, Weaviate, Qdrant) built to store and search embeddings at scale. They enable fast nearest-neighbor lookups that power semantic retrieval in RAG systems.
# Notes
- After generating embeddings, the next step is deciding where to store them and how to search them efficiently.
- **VectorStores** are purpose-built databases for storing embeddings and performing fast semantic similarity search.
- They determine the **speed, accuracy, and scalability** of your entire RAG system as your dataset grows.
- LangChain offers several options, with **Chroma (lightweight & local)** and **FAISS (high-performance & scalable)** being two of the most popular.

# References
---
1. [[Chroma]]
2. [[FAISS]]
