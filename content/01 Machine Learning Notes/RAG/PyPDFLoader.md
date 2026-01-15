---
Link:
tags:
  - RAG
---
# Brief Introduction
- **PDFs are the most common real-world documents**, but they're complex with pages, layers, formatting quirks, and inconsistent structures.
- **PyPDFLoader handles this complexity** by loading PDFs page-by-page, turning each page into its own Document object.
- This page-level granularity improves accuracy during chunking, embedding retrieval, and especially when citations or references matter
- It also automatically attaches metadata like page numbers and file names, making source-aware RAG systems much easier to build.
- PyPDFLoader gracefully manages PDF quirks, giving you clean, reliable text so you can focus on building your pipeline rather than fixing formatting.


# References
---
1. 
