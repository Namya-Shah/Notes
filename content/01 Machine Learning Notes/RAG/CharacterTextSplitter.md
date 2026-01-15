---
Link:
tags:
  - RAG
  - Text-Splitters
---
# Brief Introduction
- **Character-based Text Splitter uses fixed-length cuts**, slicing text purely by character count without analyzing structure or meaning.
- Ideal for **highly unstructured text** like logs, OCR outputs, messy transcripts, or documents with no clear formatting.
- Gives full control over **chunk size** (how big each piece is) and **overlap** (how much context carries over between chunks).
- Trade-off: it doesn't preserve semantics, so splits may occur mid-sentence or mid-paragraph, but it's predictable and fast.
- Perfect for quick RAG prototypes where simple, mechanical chunking is enough to generate manageable, embedding-ready text segments.


# References
---
1. 
