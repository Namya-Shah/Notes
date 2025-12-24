---
Lecture Date: 2025-08-20
Presentation: 
Links: 
Subject:
  - "[[EM 622 - GALLM]]"
References: 
tags:
  - EM622
---
```table-of-contents
```
# Normalization
- Removal of needless whitespace, lowercasing, and/or removing accents.
- Eg. Unicode Normalization

```python
from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")
print(type(tokenizer.backend_tokenizer))
# <class 'tokenizers.Tokenizer'>

print(tokenizer.backend_tokenizer.normalizer.normalize_str("Hello how are u?"))
# 'hello how are u?'
```
# Pre-Tokenization

# Training Algorithm
## Step 1:
## Step 2-n: Add new tokens until the desired vocabulary size is reached by learning merges (Tokenizer Training)

# Tokenization Algorithm
- Normalization
- Pre-tokenization
- Splitting the words into individual characters
- Applying 


