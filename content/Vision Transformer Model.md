---
Link:
tags:
  - Vision-Transformer-Model
---
# Notes
| NLP Transformer            | Vision Transformer (ViT)   | Explanation                                                                     |
| -------------------------- | -------------------------- | ------------------------------------------------------------------------------- |
| Tokens                     | Patches                    | Words/subwords in text -> image split into small fixed-size patches             |
| Token IDs                  | Patch Indices              | Each patch can be indexed like tokens                                           |
| Token Embedding            | Patch Embedding            | Converts token/patch index into dense vectors via learned projection            |
| Positional Embedding       | Positional Embedding       | Adds location information for sequence order/spatial structure                  |
| [CLS] Token                | [CLS] Token                | Special token to summarize sequence/image -> used for classification            |
| Encoder Input Sentence     | Embedded Patch Sequence    | Input to Transformer: tokens + positional encoding OR patches + positional info |
| Transformer Encoder Layers | Transformer Encoder Layers | Identical architecture for modeling dependencies                                |
| Output Token               | [CLS] Token Representation | Used to generate final prediction (e.g., class label)                           |


# References
---
1. 
