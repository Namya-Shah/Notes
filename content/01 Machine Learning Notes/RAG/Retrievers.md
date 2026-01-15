---
Link:
tags:
  - RAG
---
# Brief Introduction
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
