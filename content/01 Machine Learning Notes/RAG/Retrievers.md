---
Link:
tags:
  - RAG
---
# Brief Introduction
- The component responsible for fetching relevant chunks from the knowledge base. Can be dense (embedding-based), sparse (BM25/keyword), or hybrid and is one of the most impactful levers in a RAG pipeline.
# Notes
- After loading, splitting, embedding, and storing data, the final missing piece is **intelligent retrieval**.
- RAG systems cannot send all stored data to the LLM -- retrieval must **select only the most relevant information** for each query.
- Intelligent retrievals understands **user intent**, searches large knowledge sources, and fetches context dynamically.
- It also balances relevance and diversity, avoiding **redundant or overly similar results**.
- This retrieval layer turns embeddings and vector stores into **usable, high-quality knowledge systems**, directly shaping the LLM's final answer.
- Retrieval Layer is important part of RAG systems as the quality of data retrieved from the vector store (knowledge base).

# References
---
1. [[WikipediaRetriever]]
2. [[Maximal Marginal Relevance (MMR)]]
3. 
