---
Lecture Date: 2024-06-15
Presentation: "[[Lecture 6.pdf]]"
Links:
  - "[[Matrix Decompositions]]"
  - "[[MATLAB]]"
Subject:
  - "[[EM 613 - Mathematical Models for Data Science]]"
tags:
  - matrix-decompositions
  - EM613
---
```table-of-contents
```
# Why and what?
## Analogy
- Factoring of numbers, such as the factoring of 21 into prime numbers $7 \cdot 3$.
- Also called **Matrix Factorization**.
- Different representation using factors of interpretable matrices. For example: 
	- **Cholesky decomposition**: Square-root like operation for symmetric, positive definite matrices
	- **Singular value decomposition**: Extends this factorization to non-square matrices
- Represent very large numerical data in convenient form for analysis.
# Determinant
## Definition
- The determinant of a square matrix $A \in \mathbb R^{nxn}$ is denoted as det($A$) or $|A|$

$$ \det(A) = \begin{bmatrix} a_{11} & a_{12} & ... & a_{1n}\\ a_{21} & a_{22} & ... & a_{2n}\\ \vdots & \vdots & \ddots & \vdots\\ a_{n1} & a_{n2} & ... & a_{nn}\\ \end{bmatrix} $$

- Determinant of a square matrix $A \in \mathbb R^{nxn}$ is a function that maps $A$ onto a real number.
## Existence of determinant

### Testing for Matrix Invertibility

For the smallest cases, we determine if a square matrix $A$ is invertible.

- For a 1 x 1 matrix $A = a \implies a\ \cdot \frac 1 a = 1$, holds if and only if $a \not= 0$.
    
- For a 2 x 2 matrices, the inverse $A^{-1}$ is given by:

$$ A^{-1} = {1 \over {a_{11}a_{22}-a_{12}a_{21}}} \begin{bmatrix} a_{22} & -a_{12}\\ -a_{21} & a_{11} \end{bmatrix} $$

Thus, $A$ is invertible if $a_{11}a_{22}-a_{12}a_{21}\not= 0$, where,

$$ \det(A) = \begin{array}{|cc|} a_{11} & a_{12} \\ a_{21} & a_{22} \end{array}
=a_{11}a_{22}-a_{12}a_{21} $$
## Relationship with inverse  
### Theorem
$$ For\ any\ square\ matrix\ A \in \mathbb R^{nxn},\ A\ is\ invertible\ if\ and\ only\ if\ \det(A)\not=0 $$
### Expressions for determinants (small matrices)
For, $n = 2$, $\det(A) = \begin{bmatrix} a_{11}&a_{12}\\ a_{21}&a_{22} \end{bmatrix} = a_{11}a_{22}-a_{12}a_{21}$

For, $n = 3(Sarrus'\ rule), \begin{bmatrix} a_{11} & a_{12} & a_{13}\\ a_{21} & a_{22} & a_{23}\\ a_{31} & a_{32} & a_{33} \end{bmatrix} = a_{11}a_{22}a_{33}+a_{21}a_{32}a_{13}+a_{31}a_{12}a_{23}-a_{31}a_{22}a_{13}-a_{11}a_{32}a_{23}-a_{21}a_{12}a_{33}$

# Determinant for special matrices

### Triangular matrices

- A square matrix $T$ is an **upper-triangular matrix** if $T_{ij} = 0\ \forall \ i>j$ (**zero below the diagonal**).
$$

\begin{bmatrix}
1 & 2 & 3 & 6\\
0 & 3 & 2 & 7\\
0 & 0 & 5 & 8\\
0 & 0 & 0 & 9
\end{bmatrix}

$$
- A **lower-triangular matrix** has **zeros above its diagonal**.
$$

	\begin{bmatrix}
	1 & 0 & 0 & 0\\
	3 & 2 & 0 & 0\\
	4 & 7 & 6 & 0\\
	5 & 9 & 6 & 7
	\end{bmatrix}
	$$
- For a triangular matrix $T \in \mathbb R^{nxn}$, the determinant is the product of its diagonal elements:

$$ \det(T) = \prod^n_{i=1}T_{ii} $$

# Physical Significance

### Example

- Consider the three linearly independent vectors $r, g, b \in \mathbb R^3$ given as

$$ r = \begin{bmatrix} 2\\ 0\\ -8 \end{bmatrix} , g = \begin{bmatrix} 6\\ 1\\ 0 \end{bmatrix} , b= \begin{bmatrix} 1\\ 4\\ -1 \end{bmatrix} $$

- Writing these vectors as the columns of a matrix, $A = [r,g,b] = \begin{bmatrix} 2 & 6 & 1\\ 0 & 1 & 4\\ -8 & 0 & -1 \end{bmatrix} \qquad (1.1)$
- The volume is computed as $V = |\det(A)| = 186$

> **The solution for system of linear equations will not change if we use elementary transformations.**
> 
> **It is also true for inverse.**
- For finding the determinant of a matrix (**which is not a system of equations, for e.g., Matrix 1.1**) we change the origin to find the determinant. Transforming the matrix in such a way that it becomes a **diagonal matrix**. 
- **Determinant** (or **invariants**) will not change even if we transform the matrix. **Individual components** will change. Even, the **sum of the diagonals** (*invariant*) will not change.
# Determinant and Trace

## Calculation of a determinant
### Theorem (Laplace Expansion)
Consider a matrix $A \in \mathbb {R}^{nxn}$. Then, for all $j = 1,...,n$:
--- start-multi-column: ID_uc75
```column-settings
Number of Columns: 2
Largest Column: standard
```
1. Expansion along column $j$:

$$ det(A) = \sum^n_{k=1}(-1)^{k+j}a_{kj}det(A_{k,j}). \quad (4.1) $$

	Here, $det(A_{kj})$ is called a **minor** and **$(-1)^{k+j}det(A_{kj})$** is a **cofactor**.
> If we take a **cofactor of minor**, we are reducing a **degree of expansion**.

2. Expansion along row $j$:

$$ det(A) = \sum^n_{k=1}(-1)^{k+j}a_{jk}det(A_{j,k}).\quad (4.2) $$

    Here, $A_{k,j} \in \mathbb R^{(n-1)x(n-1)}$ is the submatrix of $A$ obtained by deleting row $k$ and column $j$.

--- column-break ---

- Minor

$$
\det(A_{kj})
$$

- Cofactor

$$
(-1)^{k+j}\det(A_{kj})
$$

- Submatrix of A

$$
A_{kj} \in \mathbb R^{(n-1)\ \times \ (n-1)}
$$

--- end-multi-column
## Implementation and Calculation

- Computing the determinant of an $n\ x\ n$ matrix requires a general algorithm for $n > 3$.
- Laplace Expansion reduces this to computing the determinant of $(n-1)$ x $(n-1)$ matrices.
- By recursively applying the Laplace expansion, we compute determinants of $n$ x $n$ matrices by ultimately computing determinants of 2 x 2 matrices.
- **Recursion**: Calling function again and again. It can be used for finding factorial for a given number.
### Example (Laplace Expansion)
- Compute the determinant of the matrix

$$ A = \begin{bmatrix} 1 & 2 & 3\\ 3 & 1 & 2\\ 0 & 0 & 1 \end{bmatrix} $$

    using Laplace expansion along the first row. Applying (4.2), we have:

$$ \det(A) = (-1)^{1+1}\cdot1\ \begin{array}{|cc|} 1 & 2\\ 0 & 1 \end{array} +(-1)^{1+2}\cdot2\ \begin{array}{|cc|} 3 & 2\\ 0 & 1 \end{array} +(-1)^{1+3}\cdot3\ \begin{array}{|cc|} 3 & 1\\ 0 & 0 \end{array}
= 1(1-0)-2(3-0)+3(0-0) = -5
$$

Comparison with Sarrus' rule:

$$
\det(A) = 1\ \cdot \ 1 \ \cdot \ 1 \ + \ 3 \ \cdot \ 0 \ \cdot 3 \ + \ 0 \ \cdot 2 \ \cdot \ 2 \ - \ 0 \ \cdot 1 \ \cdot \ 3 \ - \ 1 \ \cdot \ 0 \ \cdot 2 \ - \ 3 \ \cdot \ 2 \ \cdot \ 1 = 1 - 6 = -5.
$$

# Determinant and Trace

### Properties of Determinants:

1. **Multiplicativity**: $\det(AB) = \det(A)\det(B)$.
	- For a positive definite square matrix, we can find out that it is a diagonal matrix.
	- If we have diagonal matrices and we multiply both, then the product should be equal to the multiplication of their determinants.
1. **Invariance under Transposition**: $\det(A) = \det(A^T)$.
2. **Invertibility**: If $A$ is invertible, then $\det(A^{-1}) = \frac 1 {\det(A)}$.
3. **Similar Matrices**: Similar matrices have the same determinant. Therefore, for a linear mapping $\Fhi:V\rightarrow V$, all transformation matrices $[F]$ have the same determinant, making the determinant invariant to the choice of basis.
4. **Column/Row Operations**: Adding a multiple of one column/row by $\lambda$ scales the determinant by $\lambda$. In particular, swapping two rows/columns changes the sign of the determinant: $\det(A) = -\det(A')$ where $A'$ is $A$ with two rows/columns swapped.
5. Adding a multiple of a column/row to another does not change $\det(A)$.
# Trace and its properties
### Definition

The trace of a square matrix $A \in \mathbb R^{nxn}$ is defined as

$$ tr(A)\ :=\sum^n_{i=1}a_{ii} $$

i.e., the trace is the sum of the diagonal elements of $A$.

**The trace satisfies the following properties:**

- $tr(A+B) = tr(A) + tr(B), \ for\ A,B\in \mathbb R^{nxn}$
- $tr(\alpha A)=\alpha tr(A)\ for\ \alpha \in \mathbb R \ and\ A \in \mathbb R^{nxn}$
- $tr(I_n) = n,\ where\ I_n\ is\ the\ n\ x\ n\ identity\ matrix$
- $tr(AB) = tr(BA)\ for\ A\in\mathbb R^{nxk},B\in\mathbb R^{kxn}$

## Characteristic Polynomial
### Theorem (Definition of characteristic polynomial)
For $\lambda\in\mathbb R$ and a square matrix $A\in\mathbb R^{nxn}$,

$$ p_A(\lambda)\ :=\ det(A-\lambda I) $$

is the characteristic polynomial of $A$, expressed as

$$ p_A(\lambda)=c_0+c_1\lambda+c_2\lambda^2+...+c_{n-1}\lambda^{n-1}+(-1)^n\lambda^n $$

where $c_0,...,c_{n-1}$ are coefficients in $\mathbb R$. Specifically,

$$ c_0 = \det(A)\\ c_{n-1} = (-1)^{n-1}tr(A) $$

The characteristic polynomial allows computation of eigenvalues and eigenvectors.

# Eigenvalues and Eigenvectors

### Definition
Let $A\in \mathbb R^{nxn}$ be a square matrix. Then $\lambda\in\mathbb R$ is an eigenvalue of $A$ and $x \in\mathbb R^n$\{0} is the corresponding eigenvector of $A$ if

$$ Ax = \lambda x $$

The following statements are equivalent for a square matrix $A\in \mathbb R^{nxn}$:
- $\lambda$ is an eigenvalue of $A$.
- There exists a vector $x \in \mathbb R^n$\{0} such that $Ax = \lambda x$.
- $x$ is a non-zero vector in $\mathbb R^n$ satisfying $(A-\lambda I)x = 0$.
- $A - \lambda I$ is not invertible, i.e., $\det(A-\lambda I) = 0$.
- $\lambda$ is a root of the characteristic polynomial $p_A(\lambda)=\det(A-\lambda I)$.
# Collinearity and Codirection
### Definitions
 - **Codirected Vectors**: Two vectors that point in the same direction are called codirected.
 - **Collinear Vectors**: Two vectors are collinear if they codirected point in the same or the opposite direction.
### Non-uniqueness of eigenvectors
- Let $x$ be an eigenvector of $A$ associated with eigenvalue $\lambda$. Then for any $c\in\mathbb R$\{0}, it holds that $cx$ is also an eigenvector of $A$ associated with eigenvalue $\lambda$.

$$
A(cx) = A(cx) = cAx = c\lambda x = \lambda(cx)
$$

Thus, all vectors that are collinear to $x$ (i.e., vectors of the form $cx$, where $c \in \mathbb R$\{0} are also eigenvectors of $A$ associated with eigenvalue $\lambda$.
## Algebraic multiplicity of eigenvalues, eigenspaces, eigenspectrum
### Theorem

> $\lambda$ is an eigenvalue of $A$ if and only if $\lambda$ is a root of the characteristic polynomial $p_{A}(\lambda)$ of $A$

- **Algebraic multiplicity**: Let a square matrix $A$ have an eigenvalue $\lambda_i$. Number of times the root ($\lambda_i$) appears in the characteristic polynomial.
 - **Eigenspace and Eigenspectrum**. For $A \in \mathbb R^{nxn}$, the set of all eigenvectors of $A$ associated with an eigenvalue $\lambda$ spans a subspace $E_{\lambda}$ of $\mathbb R^n$, called the eigenspace of $A$ with respect to $\lambda$. The eigenspace $E_{\lambda}$ is denoted as

$$
E_{\lambda} = {{x\in \mathbb R^{n|Ax=\lambda}x}}
$$

The set of all eigenvalues of $A$ is called the eigenspectrum, or simply the spectrum, of $A$.

### Example: The case of Identity Matrix
The identity matrix $I\in\mathbb R^{nxn}$ has characteristic polynomial $p_{I}(\lambda) = \det(I-\lambda I) = (1 - \lambda)^{n}= 0$, which has only one eigenvalue $\lambda = 1$ that occurs $n$ times. Moreover, $Ix = \lambda x = 1x$ holds for all vectors $x \in \mathbb R^n$ \ {0}.
Because of this, the sole eigenspace $E_{1}$ of the identity matrix spans $n$ dimensions, and all $n$ standard basis vectors of $\mathbb R^n$ are eigenvectors of $I$.

Useful properties regarding eigenvalues and eigenvectors:
- A matrix $A$ and its transpose $A^T$ possess the same eigenvalues, but not necessarily the same eigenvectors.
- The eigenspace $E_{\lambda}$ is the null space of $A - \lambda I$ since

$$
Ax = \lambda x \implies Ax - \lambda x \implies (A-\lambda I)x = 0 \implies x \in ker(A-\lambda I)
$$

**Example (Computing Eigenvalues, Eigenvectors, and Eigenspaces).** Let us find the eigenvalues and eigenvectors of the 2x2 matrix

$$
	A = \begin{pmatrix}
	4 & 2 \\ \\
	1 & 3
	\end{pmatrix}
	$$
	**Step 1: Characteristic Polynomial.** The characteristic polynomial $p_{A}(\lambda)$ is computed as
$$

p_{A}(\lambda) = \det(A-\lambda I) = \det
\begin{pmatrix}
4-\lambda & 2\\
1 & 3-\lambda
\end{pmatrix}
= (4-\lambda)(3-\lambda)-2\cdot{1}

$$
**Step 2: Eigenvalues.** Solving $p_{A}(\lambda)$ = 0, we obtain the eigenvalues $\lambda_{1} = 2$ and $\lambda_{2} = 5$.
**Step 3: Eigenvectors and Eigenspaces.**
- For $\lambda = 5$:
$$

A - 5I = 
\begin{pmatrix}
-1 & 2 \\
1 & -2
\end{pmatrix},
Eigenspace\ E_{5} = span
\begin{Bmatrix}
\begin{pmatrix}
2 \\
1
\end{pmatrix}
\end{Bmatrix}

$$
- For $\lambda$ = 2:
$$

A - 2I = \begin{pmatrix}
2 & 2\\
1 & 1
\end{pmatrix},
\ Eigenspace\ E_{2} = span
\begin{Bmatrix}
\begin{pmatrix}
1 \\
-1
\end{pmatrix}
\end{Bmatrix}

$$
- The two eigenspaces $E_{5}$ and $E_{2}$ in above example are one-dimensional as they are each spanned by a single vector.
- In other cases we may have multiple identical eigenvalues (**algebraic multiplicity**) and the eigenspace may have more than one dimension.
- The eigenspace $E_2$ reiterates that all **collinear vectors** are eigenvectors of $A$.

# Geometric Multiplicity
- **Definition. Let $\lambda_i$ be an eigenvalue of a square matrix $A$. The geometric multiplicity of an eigenvalue $\lambda_{i}$ of a matrix $A$ is the number of linearly independent eigenvectors associated with $\lambda_{i}$. In other words, it is the dimensionality of the eigenspace spanned by the eigenvectors associated with $\lambda_i$.
- A specific eigenvalues's **geometric multiplicity** must be at least one because every eigenvalue has at least one associated eigenvector.**The geometric multiplicity cannot exceed the eigenvalue's algebraic multiplicity but may be lower.**
**Example.**
The matrix $$A = 
\begin{pmatrix}
2 & 1 \\  0 & 2
	\end{pmatrix}$$has two repeated eigenvalues $\lambda_{1} = \lambda_{2} = 2$ with an algebraic multiplicity of 2. The eigenvalue 2 has, however, only one distinct unit eigenvector $$x_{1} = \begin{pmatrix}
1 \\  0
\end{pmatrix}$$, thus a geometric multiplicity of 1.

## Linear Independence
### Theorem
The eigenvectors $x_1,...,x_n$ of a matrix $A \in \mathbb R^{nxn}$ with distinct eigenvalues $\lambda_1,...,\lambda_n$ are linearly independent. 
### Interpretation of the theorem
This implies that the eigenvectors of $A$ with distinct eigenvalues form a basis of $\mathbb R^n$.

#### Defective vs. non-defective matrices
- A square matrix $A \in\mathbb R^{nxn}$ is defective if it possesses fewer than $n$ linearly independent eigenvectors.
- A matrix is non-defective if it possesses all linearly independent eigenvectors.
- A non-defective matrix $A \in \mathbb R^{nxn}$ does not necessarily require $n$ distinct eigenvalues, but it does require that the eigenvectors form a basis of $\mathbb R^n$.
- Specifically, a defective matrix has at least one eigenvalue $\lambda_i$ with an algebraic multiplicity $m > 1$ and a geometric multiplicity of less than $m$.

## Positive semi-definite matrices
### Theorem
Given a matrix $A \in \mathbb R^{mxn}$, we can always obtain a symmetric, positive semidefinite matrix $S \in \mathbb R^{nxn}$ by defining

$$ S\ := \ A^TA $$
#### Remarks 
- If $rk(A)=n$, then $S\ :=\ A^TA$ is symmetric and positive definite.
- Symmetry requires $S = S^T$ and thus, $S = A^TA=A^T(A^T)^T=(A^TA)^T=S^T$.
- positive semi-definiteness requires $x^TSx \geq 0$, and thus, $x^TSx = x^TA^TAx=(Ax)^T(Ax)\geq 0$, because the dot product computes a sum of squares, which are non-negative.
## Spectral Theorem
### Theorem
If $A \in \mathbb R^{n \ \text{x} \ n}$ is symmetric, there exists an orthonormal basis of the corresponding vector space $V$ consisting of eigenvectors of $A$, and each eigenvalue is real.

### Implications
A direct implication of the spectral theorem is:
1. The eigen decomposition of a symmetric matrix $A$ exists (with real eigenvalues).
2. These real eigenvalues give an **orthonormal basis** of eigenvectors so that $A = PDP^T$, where $D$ is diagonal and the columns of $P$ contain the eigenvectors.

### Theorem (Determinant)

The determinant of a matrix $A \in \mathbb R^{nxn}$ is the product of its eigenvalues i.e.,

$$ \det(A) = \prod^n_{i=1}\lambda_i, $$

where $\lambda_i \in \mathbb{C}$ are (possibly repeated) eigenvalues of $A$.

### Theorem (Trace)

--- start-multi-column: ID_d0n4
```column-settings
Number of Columns: 2
Largest Column: standard
```

The trace of a matrix $A \in \mathbb R^{nxn}$ is the sum of its eigenvalues, i.e.,
$$

tr(A) = \sum^n_{i=1}\lambda_i,

$$

--- column-break ---

**Properties of Trace**
1. $tr(A+B) = tr(A) + tr(B)$ for $A, B \in R^{n \text{x} n}$.
2. $tr(\alpha A) = \alpha tr(A)$ for $\alpha \in \mathbb R$ and $A \in \mathbb R^{n \text{x} n}$.
3. $tr(I_n) = n$, where $I_n$ is the $n \ \text{x} \ n$ identity matrix.
4. $tr(AB) = tr(BA)$ for $A \in \mathbb R^{n \ \text{x} \ k}, B \in \mathbb R^{k \text{x} n}$.

--- end-multi-column





