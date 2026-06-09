---
tags:
  - Interview
---
# Question
Your RAG retrieval is too slow with a large knowledge base. How do you speed it up?

# Answer
- **Use a hybrid retrieval strategy**
	- Combine vector search with keyword-based retrieval (BM25) to improve relevance while reducing unnecessary searches.
- **Tune chunking and indexing**
	- Smaller, well-structured chunks improve retrieval accuracy and reduce the number of documents that need re-ranking.
- **Apply metadata filtering**
	- Filter documents by source, date, product, region, or category before vector search to shrink the search space.
- **Use Approximate Nearest Neighbor (ANN) indexes**
	- Technologies like HNSW and IVF drastically reduce search latency compared to brute-force similarity searches.
- **Implement multi-stage retrieval**
	- Retrieve a small candidate set first, then apply cross-encoder re-ranking only on the top results.
- **Cache frequent queries**
	- Many enterprise questions repeat. Caching embeddings and retrieval results can significantly cut response times.
- **Optimize embeddings**
	- Use efficient embedding models and periodically re-evaluate whether higher-dimensional vectors are actually improving retrieval quality.
- **Monitor retrieval metrics**
	- Track latency, recall@k, hit rate, and re-ranking time to identify bottlenecks before they impact users.