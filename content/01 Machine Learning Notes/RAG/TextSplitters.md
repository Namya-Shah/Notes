---
Link:
tags:
  - RAG
---
# Brief Introduction
- **LLMs can't process huge documents at once**, so text must be broken into smaller, meaningful chunks before retrieval or reasoning.
- **Text Splitters handle this job**, acting like editors that decide chunk boundaries to keep context clean, relevant, and manageable.
- They support multiple strategies -- from **simple fixed-size chunks**, to **structure aware splitting**, to **code-safe splitting**, and even **semantic chunking** based on meaning.
- These approaches help handle diverse content types: long articles, research papers, scraped webpages, structured documents, datasets, and code.
- Effective chunking is critical for RAG performance, directly improving retrieval accuracy, context quality, and overall model intelligence.


# References
---
1. [[CharacterTextSplitter]]
2. [[RecursiveCharacterTextSplitter]]
3. 
