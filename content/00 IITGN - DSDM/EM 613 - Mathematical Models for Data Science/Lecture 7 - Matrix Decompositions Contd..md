---
Lecture Date: 2024-07-03
Presentation: 
Links:
  - "[[Self Note @ 1 - Cholesky Decomposition]]"
Subject:
  - "[[EM 613 - Mathematical Models for Data Science]]"
tags:
  - EM613
---
```table-of-contents
```
# Cholesky Decomposition
- **Analogy:** Provides a square-root equivalent operation on *symmetric, positive definite* matrices.
## Theorem
- A *symmetric* [[Lecture 4 & 5 - Linear Algebra - Matrices, matrix operations, solution of linear equations#Symmetric Matrix]], *positive definite matrix* [[Lecture 6 - Matrix Decompositions#Positive semi-definite matrices]] $A$ can be factorized into a product $A=LL^T$, where $L$ is a lower triangular matrix with positive diagonal elements.

$$
\begin{bmatrix}
a_{11} \cdots a_{1n}\\
\vdots \quad \ddots \quad \vdots \\
a_{n1} \cdots a_{nn}
\end{bmatrix}=
\begin{bmatrix}
l_{11} \cdots l_{n1}\\
\vdots \quad \ddots \quad \vdots \\
l_{1n} \cdots l_{nn}
\end{bmatrix} 
\begin{bmatrix}
l_{11} \cdots l_{1n} \\
\vdots \quad \ddots \quad \vdots\\
l_{n1} \cdots l_{nn}
\end{bmatrix} 
$$

- The matrix $L$ is called the **Cholesky factor** of matrix $A$, and $L$ is unique.
### Objective
Consider a symmetric, positive definite matrix $A \in \mathbb R^{3 \text{x} 3}$. Find its Cholesky factorization $A = LL^T$, where

$$
A = \begin{bmatrix}
a_{11} & a_{21} & a_{31}\\
a_{21} & a_{22} & a_{32}\\
a_{31} & a_{32} & a_{33}
\end{bmatrix} =
\begin{bmatrix}
l_{11} & 0 & 0\\
l_{21} & l_{22} & 0\\
l_{31} & l_{32} & l_{33}
\end{bmatrix}
\begin{bmatrix}
l_{11} & l_{21} & l_{31}\\
0 & l_{22} & l_{32}\\
0 & 0 & l_{33}
\end{bmatrix}
$$

#### Procedure
Expanding RHS:

$$
\begin{bmatrix}
l_{11}^2 & l_{21}l_{11} & l_{31}l_{11}\\
l_{21}l_{11} & l_{21}^2 + l_{22}^2 & l_{31}l_{21}+l_{32}l_{22}\\
l_{31}l_{11} & l_{31}l_{21}+l_{32}l_{22} & l_{31}^2+l_{32}^2+l_{33}^2
\end{bmatrix}
$$

Comparing both sides, we get:
**Diagonal Elements:** $l_{11} = \sqrt{a_{11}}, \ l_{22} = \sqrt{a_{22}-l_{21}^2}, \ l_{33} = \sqrt{a_{33}-(l_{31}^2+l_{32}^2)}$
**Off-diagonal elements:** $l_{21}=\frac {a_{21}} {l_{11}}, \ l_{31} = \frac {a_{31}} {l_{11}}, \ l_{32} = \frac {a_{32} - l_{31}l_{21}} {l_{22}}$
## Implications
### Key Points
1. Cholesky decomposition can be calculated for any symmetric, positive definite.
2. The calculation for $l_{ij}$ depends on $a_{ij}$ and previously computed $l_{ij}$.
#### Calculation of determinants
Given the Cholesky decomposition $A = LL^T$, $\det(A) = \det(L) \det(L^T) = \det(L)^2$. As $L$ is a triangular matrix

$$
\det(A) = \prod_i l_{ii}^2
$$

# Eigendecomposition and diagonalization
## Diagonal Matrices
- A matrix that has value zero on all off-diagonal elements, i.e., $D = \begin{bmatrix} c_1 \ \cdots 0\\ \vdots \ \ddots \ \vdots \\ 0 \cdots \ c_n\end{bmatrix}$
### Advantages
1. Fast computation of determinants, powers, and inverses.
2. **Recall:** If matrices $A$ and $D$ are similar if there exists an invertible matrix $P$ such that $D = P^{-1}AP$. Useful for computing the eigenvalues of $A$.
### Definition
- A matrix $A \in \mathbb R^{n \mathrm{x} n}$ is diagonalizable if it is similar to a diagonal matrix, i.e., if there exists an invertible matrix $P \in \mathbb R^{n \mathrm{x} n}$ such that $D = P^{-1}AP$.
### Theorem (Eigendecomposition)
*A square matrix $A \in \mathbb R^{n \mathrm{x} n}$ can be factored as:*

$$
A = PDP^{-1}
$$