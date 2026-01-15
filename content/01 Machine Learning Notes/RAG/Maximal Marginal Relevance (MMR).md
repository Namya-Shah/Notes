---
Link:
tags:
  - RAG
---
# Brief Introduction
- **Semantic search often suffers from redundancy**, returning multiple documents that say nearly the same thing.
- **Maximal Marginal Relevance (MMR)** addresses this by balancing relevance to the query with diversity among results.
- MMR selects documents that are **useful and add new information**, not just the most similar ones.
- It's especially effective when documents overlap, are paraphrased, or repeat similar ideas.
- By tuning the relevance-diversity balance, MMR produces **richer, non-redundant context**, improving LLM reasoning in RAG systems.
- The balance between relevance and diversity is adjustable. Tuning this balance helps you shape the quality of retrieved context.
```python
from langchain_community.vectorstores import FAISS
from langchain_huggingface import HuggingFaceEmbeddings
from langchain_core.documents import Document

documents = [
Document(page_content="LangChain helps developers build LLM applications easily"),
Document(page_content="Chroma is a vector database optimized for LLM based search"),
Document(page_content="Embeddings convert text into high-dimensional vectors"),
Document(page_content="MMR helps you get diverse results when doing similarity search."),
Document(page_content="OpenAI provides powerful embedding models")
]

# Step 2: Initialize embedding model
embeddings=HuggingFaceEmbeddings(model_name="sentence-transformers/all-MiniLM-L6-v2")

vectorstore=FAISS.from_documents(
documents=documents,
embedding=embeddings
)
# build a retriever
retriever=vectorstore.as_retriever(
	search_type="mmr",
	search_kwargs={"k": 3, "lambda_mult": 0.25} # `lambda_mult` can go from 0.0 to 1.0
)

query="What is Langchain?"
results = retriever.invoke()
print(results)
```
- `lambda_mult` can go from 0.0 to 1.0
- If `lambda_mult:0.0` -> it means full diversity and ignores relevance and vice-versa

> [!NOTE] NOTE
> MMR is preferred in production-grade RAG systems.

# References
---
1. 
