---
Created On: 2024-06-30
Links:
  - "[[Rank]]"
  - "[[Pivot]]"
  - "[[Row Echelon Form]]"
Subject:
  - "[[EM 613 - Mathematical Models for Data Science]]"
---
# Introduction
- A common approach is to construct a set of objects (symbols) and a set of rules to manipulate these objects. This is known as *algebra*. Linear algebra is the study of vectors and certain rules to manipulate vectors.
- The vectors many of us know from school are called "geometric vectors", which are usually denoted by a small arrow above the letter, e.g., $\vec{x}$ and $\vec{y}$.
- Vectors are special objects that can be added together and multiplied by scalars to produce another object of the same kind. Any object that satisfies these two properties can be considered a vector.

### Geometric Vectors
- Two geometric vectors $\vec{x}$, $\vec{y}$ can be added, such that $\vec{x} + \vec{y} = \vec{z}$ is another geometric vector. Furthermore, multiplication by a scalar $\lambda \vec{x}, \lambda \in \mathbb R$, is also a geometric vector. In fact, it is the original vector scaled by $\lambda$.
	- $\lambda$ is a scalar number so it would scale $\vec{x}$ and not change any of its properties.

- Linear algebra plays an important role in machine learning and general mathematics.

### System of Linear Equations
- Systems of linear equations play a central part of linear algebra. Many problems can be formulated as systems of linear equations, and linear algebra gives us the tools for solving them.

## General form of system of linear equations

$$
\begin{align}
a_{11}x_1 + ...+a_{1n}x_n = b_1\\
\vdotswithin{a_{11}x_1 + ...+a_{1n}x_n = b_1}\\
am_1x_1+...+a_{mn}x_n = b_m
\end{align}
$$

- The above equation is the general form of a *system of linear equations*, and $x_1,...,x_n$ are the *unknowns* of this system. Every $n$-tuple $(x_1,...,x_n) \in \mathbb R^n$ that satisfies the equation is a *solution of the linear equation system.*

## Solution of System of Linear Equations

$$
\begin{align}
x_1 + x_2 +x_3 = 3\\
x_1 - x_2 + 2x_3 = 2\\
2x_1+0x_2 +3x_3 = 1
\end{align}
$$

has **no solution**. Adding the first two equations contradicts the third equation.

$$
\begin{align}
x_1 + x_2 +x_3 = 3\\
x_1 - x_2 + 2x_3 = 2\\
0x_1+x_2 +3x_3 = 2
\end{align}$$
From the first and third equation, it follows that $x_1 = 1$. Adding first and second equation we get $2x_1+3x_3=5$, i.e., $x_3=1$. From third equation, we then get that $x_2=1$. Therefore, $(1,1,1)$ is the **only possible and unique solution**.

# Pivot Position
- The positions of the leading 1's in a row echelon form or reduced row echelon form matrix are the pivot positions of the matrix.
- **A non-zero entry in a pivot position is pivot.**
- The columns containing the leading 1's in a row echelon form or reduced row echelon form matrix are the **pivot columns** of the matrix. The rows containing the leading 1's are the **pivot rows**.

# Row Echelon Form
$$\begin{bmatrix}
1 & 0 & 2\\
0 & 1 & 4\\
0 & 0 & 0
\end{bmatrix}$$
- To be in row echelon form, a matrix must have the following properties:
	1. If a row does not consist entirely of zeros, then the first non-zero number in the rows is a 1.
		- **Some texts will exclude this restriction.**
	2. All zero rows are the bottom of the matrix
	3. In any two successive rows that do not consist entirely of zeros, the leading 1 in the lower row occurs farther to the right than the leading 1 in the higher row.
- Row Echelon form is not unique
**For reduced row echelon form:**
- **Should have above three properties**
- Each column containing a leading 1 has zeros in all its other entries.
- Reduced row echelon form is unique.
- We can have different arbitrary numbers if we have a column containing 0's.
	![[CleanShot 2024-06-30 at 17.42.12@2x.png]]
- Since the reduced row echelon form is unique, it is sometimes called **canonical form** of the matrix.
#### Some Facts
1. Every matrix has a unique reduced row echelon form; that is, regardless of whether you use Gauss-Jordan elimination or some other sequence of elementary row operations, the same reduced row echelon form will result in the end.
2. Row echelon forms are not unique; that is, different sequences of elementary row operations can result in different row echelon forms.
3. Although row echelon forms are not unique, the reduced row echelon form and all row echelon forms of a matrix $A$ have the same number of zero rows, and the leading 1's always occur in the same positions. Those are called the *pivot positions* of $A$. A column that contains a pivot position is called a *pivot column* of $A$.

# Trace
> If $A$ is a square matrix, then the ***trace*** of $A$ denoted by $tr(A)$, is defined to be the sum of the entries on the main diagonal of $A$. The trace of $A$ is undefined if $A$ is not a square matrix.

![[CleanShot 2024-06-30 at 20.51.22@2x 1.png]]
# Cancellation Law
### Failure of the Cancellation Law
![[CleanShot 2024-06-30 at 21.27.28@2x.png]]

# Gaussian Elimination
- It is a sequence of elementary row operations done to transform a matrix into row echelon form. 

# Homogeneous Linear Systems
- A system of linear equations is said to be ***homogeneous*** if the constant terms are all zero.
- Every homogeneous system of linear equations is consistent because all such systems have $x_1 =0,x_2=0,...,x_n = 0$ as a solution. This solution is called the ***trivial solution***. If there are other solutions, they are called ***nontrivial solution***.
- **There is one case in which a homogeneous system is assured of having nontrivial solutions - namely, whenever the system involves more unknowns than equations.**
> If a homogeneous linear system has $n$ unknowns, and if the reduced row echelon form of its augmented matrix has $r$ nonzero rows, then the system has $n-r$ free variables.
> A homogeneous linear system with more unknowns than equation has infinitely many solutions.
# Zero Product with Non Zero Factors
![[CleanShot 2024-06-30 at 22.11.11@2x.png]]
> If $R$ is the reduced row echelon form of an $n \ \text{x} \ n$ matrix $A$, then either $R$ has a row of zeros or $R$ is the identity matrix $I_n$.

# Inverse of a matrix
> If $A$ is a square matrix, and if a matrix $B$ of the same size can be found such that $AB = BA = I$, then $A$ is said to be ***invertible (or non-singular)*** and $B$ is called to be an **inverse** of $A$. If no such matrix $B$ can be found, then $A$ is said to be **singular**.

$$

A=\begin{bmatrix}
2 & -5\\
-1 & 3
\end{bmatrix}

$$
$$

A^{-1} =
\begin{bmatrix}
3 & 5\\
1 & 2
\end{bmatrix}

$$
> *An invertible matrix has exactly one inverse.*
> If $B$ & $C$ are both inverses of the matrix $A$, then $B = C$

The matrix $A$
$$

A = \begin{bmatrix}
a & b\\
c & d
\end{bmatrix}

$$
is invertible if and only if $ad - bc \not= 0$, in which case the inverse is given by the formula
$$

A^{-1} = \frac 1 {ad-bc} \begin{bmatrix}
d & -b\\
-c & a
\end{bmatrix}

$$
- To find the value of two variables
$$

\begin{bmatrix}
a & b\\
c & d
\end{bmatrix}
\begin{bmatrix}
x\\
y
\end{bmatrix}=
\begin{bmatrix}
u\\
v
\end{bmatrix}

$$
$$

\begin{bmatrix}
x\\
y
\end{bmatrix}= 
\begin{bmatrix}
a & b\\
c & d
\end{bmatrix}^{-1}
\begin{bmatrix}
u\\
v
\end{bmatrix}

$$
$$

x = \frac {du-bv}{ad-bc} \quad, \quad y=\frac {av-cu}{ad-bc}

$$
- If $A$ and $B$ are invertible matrices with same size, then $AB$ is invertible and
$$

(AB)^{-1} = B^{-1}A^{-1}

$$
- A product of any number of invertible matrices is invertible, and the inverse of the product is the product of the inverses in the reverse order.
- If a product of matrices is singular, then at least one of the factors must be singular.
- If $A$ is invertible and $n$ is a non-negative integer, then:
	- $A^{-1}$ is invertible and $(A^{-1})^{-1} = A$.
	- $A^n$ is invertible and $(A^n)^{-1} = A^{-n}=(A^{-1})^n$.
	- $kA$ is invertible for any non-zero scalar $k$, and $(kA)^{-1} = k^{-1}A^{-1}$.
#### Square of Matrix Sum
- It is only in the special case where $A$ and $B$ *commute* (i.e., $AB=BA$) that we can go step further and write
$$

(A+B)^2 = A^2 + 2AB + B^2

$$
## Transpose of a Matrix
> The transpose of a product of any number of matrices is the product of the transposes in reverse order.

> If $A$ is an invertible matrix, then $A^T$ is also invertible and $(A^T)^{-1} = (A^{-1})^T$
# Row Equivalent Matrix
- Matrices $A$ and $B$ are said to be **row equivalent** if either can be obtained from the other by a sequence of elementary row operations.
- A matrix $E$ is called an **elementary matrix** if it can be obtained from an identity matrix by performing a *single elementary row operation*.
### Number of Solutions of a Linear System
> A system of linear equations has zero, one or infinitely many solutions. There are no other possibilities.


# Singular Matrices
- A square matrix with a row or column of zeros is singular.
$$

\begin{bmatrix}
1 & 4 & 0\\
2 & 5 & 0\\
3 & 6 & 0
\end{bmatrix}

$$

# Rank
- Rank of a matrix can be determined by reduced row echelon form. The number of non-zero rows in the reduced row-echelon form is the **rank of the matrix**.