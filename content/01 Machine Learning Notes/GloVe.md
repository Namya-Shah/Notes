---
Link:
tags:
  - ML
---
# Brief Introduction
$$
J = \sum^V_{i,j=1}f(X_{ij})(w^T_iw_j+b_i+b_j-\log(X_{ij}))^2
$$

$X_{ij}$ -> Cooccurence count of two words i and j
$X_{ij}$ can be calculated from any corpus.
$w_i$ -> word vector
$w_j$ -> context words vector
- dot product of $w_i^Tw_j$
	- $\approx 0$ (No correlation)
	- $\approx 1$ (Perfect correlation)
- We are summing all the pairs of words
- No complicated neural network unlike [[Word2Vec]]
- We do not require to store co-occurence matrices
- **Advantages**
	- Fast training
	- Scalable to huge corpora
	- Good performance even with small corpus, and small vectors code and vectors
# Semantic Relationships
![[Pasted image 20250720135306.png]]
# Synctatic Relationships
![[Pasted image 20250720135526.png]]
# Analogy Testing
![[Pasted image 20250720135148.png]]
![[Pasted image 20250720135609.png]]
- Increasing window size, the results were improving


# References
---
1. 
