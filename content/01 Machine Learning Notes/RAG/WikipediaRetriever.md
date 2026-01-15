---
Link:
tags:
  - RAG
---
# Brief Introduction
- This retrieval scenario focuses on **external knowledge sources**, not local documents or vector databases.
- Ideal for **public, factual, and constantly changing information** like science, history, or general definitions.
- Unlike vector retrieval, there are **no precomputed embeddings** -- results are fetched dynamically at query time.
- Retrieved content is returned as **standard Document objects**, making it easy to plug into LangChain chains and prompts.
- This approach gives your AI access to a **live, always-updated knowledge base** without the overhead of maintaining your own data.

# References
---
1. 
