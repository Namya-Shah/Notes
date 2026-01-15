---
Link:
tags:
  - RAG
---
# Brief Introduction
- **Recursive Character Text Splitter preserves structure**, splitting text using a hierarchy (paragraphs -> newlines -> sentences -> words -> characters).
- It makes **semantically meaningful cuts**, ensuring ideas stay intact rather than being sliced at awkward points.
- Uses a **smart fallback mechanism**, recursively trying the next best separator until each chunk fits the given size limit.
- Produces **more natural, context-rich chunks**, which improves embedding quality and retrieval accuracy in RAG systems.
- Ideal for structured writing -- articles, blogs, essays, reports -- where maintaining flow and coherence significantly boosts system performance.

# References
---
1. 
