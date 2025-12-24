---
Lecture Date: 2024-06-13
Presentation: "[[Lecture 4 & 5.pdf]]"
Links:
  - "[[Linear Algebra]]"
  - "[[MATLAB]]"
Subject:
  - "[[EM 613 - Mathematical Models for Data Science]]"
tags:
  - EM613
---
```table-of-contents
```
## Decision Making
- Represent data as vectors
- Choose appropriate models
- Learn from available data to make predictions
    - Critical for decision making
![[CleanShot 2024-06-18 at 19.23.52@2x.png]]

## Data versus Vectors

- Not all data is numerical but representation in number format is a useful
- Assumption: data has been converted into a numerical representation and can be into a computer program.

## Vector Representations

- Array of numbers (Computer Science view)
- Quantity with magnitude and direction (Physics view)
- Object that obeys addition and scaling (Mathematical view)

## Model

- Process of generating data similar to data set in mind
- Simplified versions of the real (unknown) data-generating process.
- A good model: Predict accurately what would happen in the real world without performing real-world experiments.

## Putting it all together

- **Linear Algebra**: Study of vectors and matrices
- **Matrix Decomposition**: Intuitive interpretation of the data and more efficient learning.
- **Optimization**: Which direction to look for solutions. Requires calculus.

## Unusual Vectors I

**Examples**

- Geometric vectors: These are directed segments.
    - Sum of two geometric vectors is another geometric vector: $\vec z = \vec x + \vec y$
    - Multiplication by a scalar, $b$ is also a geometric vector: $b\vec x$
- Polynomials are also vectors: Can be added together or multiplied by a scalar to give another polynomial.
- Audio signals: Represented as a series of numbers. Addition of audio signals gives a new audio signal.
- **Our Focus:** Elements in $R^n$ (tuples of `n` real numbers) are also vectors. These also can be added together and multiplied by a scalar.

## Systems of linear equations

### Problem

- A company produces products $N_1,...,N_n$ for which resources $R_1,...,R_m$ are required
- To produce a unit of product $N_j,a_{ij}$ units of resource $R_i$ are needed, where $i = 1,...,m$ and $j=1,...,n$
- **Objective:** Find an optimal production plan, i.e., a plan of how many units $x_j$ of product $N_j$ should be produced if a total of $b_i$ units of resource $R_i$ are available and (ideally) no resources are left over.

### Approach

For $x_1,...,x_n$ units of the corresponding products, the total resource

$$ R_i = a_{i1}x_1 + ... + a_{in}x_n $$

is needed. An optimal production, therefore, satisfies the equations, called system of linear equations with unknowns $x_1,...,x_n$ as their solutions.

$$ a_{11}x_1+...+a_{1n}x_n = b_1 $$

$$ a_{m1}x_1+...+a_{mn}x_n = b_n $$

# Types of Solutions

## No Solution

Adding two equations contradicts the third.

$$
x_1+x_2+x_3 = 3
$$

$$
x_1-x_2+2x_3 = 2
$$

$$
2x_1+3x_3
$$

## Unique Solution
Solving the equations to get one solution which satisfy all equations.

$$
x_1+x_2+x_3 = 3
$$

$$
x_1-x_2+2x_3 = 2
$$

$$
x_2+x_3 = 2
$$

## Infinitely many solutions
More than one solution.

$$
x_1+x_2+x_3 = 3
$$

$$
x_1-x_2+2x_3 = 2
$$

$$
2x_1+3x_3 = 5
$$

# Geometrical Interpretation
- Must satisfy all equations simultaneously, the solution set is the intersection set.
## Intersection set
- Parallel lines => no intersection => No solution
- A point => one intersection => Unique solution
- Same line => many intersections => Infinite solutions
## Graphical Representation
	![[CleanShot 2024-06-18 at 13.07.41@2x.png]]
## Compact Notation
- Collect the coefficients $a_{ij}$ into vectors
	![[CleanShot 2024-06-18 at 13.08.37@2x.png]]
- Collect the vectors into matrices
	![[CleanShot 2024-06-18 at 13.10.48@2x.png]]
## Representation
### Definition
- Matrices represent systems of linear equations/functions (linear mappings)
- Matrix *A* is an $m \cdot n$ tuple of elements having $m$ rows and $n$ columns, where, $m,n \in N$. Thus, $A \in \mathbb R^{mxn}$ represents:

$$\begin{bmatrix} a_{11} & a_{12} & ... & a_{1n}\\ a_{21} & a_{22} & ... & a_{2n}\\ \vdots & \vdots & \ddots & \vdots\\ a_{n1} & a_{n2} & ... & a_{nn}\\ \end{bmatrix} $$

- **Convention**: (1,$n$)-matrices are rows, ($m$,1)-matrices are columns.
# Matrix Operations
## Addition
The sum of two matrices $A \in \mathbb R^{mxn}$, $B \in \mathbb R^{mxn}$ is defined as the element-wise sum.
	![[CleanShot 2024-06-18 at 14.46.09@2x.png]]
## Multiplication
- Matrices can only be multiplied if their "inner" dimensions match.An $n$x$k$-matrix $A$ multiplied by $k$x$m$-matrix $B$ gives matrix $C$ as
	![[CleanShot 2024-06-18 at 19.08.45@2x.png]]
- Component-wise representation

	$$
	c_{ij} = \sum ^n _{l=1}a_{il}b_{lj}
	$$

- Element-wise multiplication is called **Hadamard product**.
# Properties of Matrices
## Fundamental Properties
- **Matrix multiplication is not commutative**, i.e., $AB\not=BA$.
- Associativity: ∀$A \in \mathbb R^{mxn}, B \in \mathbb R^{nxp}, C \in \mathbb R^{pxq}$, i.e., (AB)C = A(BC)
- Distributivity: ∀$A,B \in \mathbb R^{mxn},C,D \in \mathbb R^{nxp}$

$$
	(A+B)C = AC + BC
$$$$

	A(C+D) = AC + AD

$$
- Multiplication with identity matrix: ∀$A \in \mathbb R^{mxn}, i.e., I_mA = AI_n = A$
# Inverse
## Definition
- Consider matrix $A \in \mathbb R^{mxn}$. Then $B \in \mathbb R^{nxn}$ is the inverse ($A^{-1}$) of $A$ if:
$$

	AB = I_n = BA

$$
- If inverse exists, then $A$ is called **non-singular** or **invertible** or **regular** matrix. Otherwise, **singular** or **non-invertible**.
## Existence of the Inverse of a 2 x 2 matrix
	![[CleanShot 2024-06-18 at 19.19.11@2x.png]]
	if and only if, the determinant of a 2 x 2-matrix, $a_{11}a_{22} - a_{12}a_{21} \not = 0$.
# Transpose
## Definition
- For $A \in \mathbb R^{mxn}$ the matrix $B \in \mathbb R^{nxm}$ with $b_{ji} = a_{ij}$ is the transpose of $A$ denoted by $B = A^T$.
- Transpose of $A$ is obtained by writing columns of $A$ as the rows of $A^T$.
- If $A$ is invertible, then $A^T$ is also invertible.
## Symmetric Matrix

- A matrix $A$ is symmetric if $A = A^T$.
- Only square matrices ($n$ x $n$) can be symmetric.
- Sum of symmetric matrices is always symmetric.
- Product of symmetric matrix is always defined, it is generally not symmetric.

## WHY DO WE USE TRANSPOSE AND ITS APPLICATIONS?

1. **Matrix Operations**: Transposing a matrix is often necessary for certain matrix operations. For example, when multiplying two matrices, the number of columns in the first matrix must equal the number of rows in the second matrix. In some cases, taking the transpose of one of the matrices can help make the dimensions compatible for multiplication.
2. **Solving Systems of Equations**: In some cases, transposing a matrix can be useful when solving systems of linear equations using matrix operations. For example, the transpose of a coefficient matrix in a system of linear equations can be used to solve the system using methods like Gaussian elimination or LU decomposition.
3. **Orthogonality and Symmetry**: Transposing a matrix can help in identifying properties such as orthogonality or symmetry. For example, a square matrix is orthogonal if its transpose is equal to its inverse. Similarly, symmetric matrices are matrices that are equal to their transposes.
4. **Eigenvalues and Eigenvectors**: Transposing a matrix can be helpful when working with eigenvalues and eigenvectors. For example, the eigenvalues of a matrix are the same as the eigenvalues of its transpose, and the eigenvectors of a matrix and its transpose are related.
5. **Data Analysis and Machine Learning**: In fields like data analysis and machine learning, transposing matrices is often done to manipulate data in a way that is suitable for various algorithms and computations. For example, in some machine learning algorithms, it is common to transpose the feature matrix to have the features as rows and the samples as columns.

# Properties of inverses and transposes

### Inverses

![[CleanShot 2024-06-19 at 08.29.24@2x.png]]

### Transposes

![[CleanShot 2024-06-19 at 08.29.45@2x.png]]

# Scalar multiplication

- Matrix $A \in \mathbb R^{mxn}$ when multiplied by a scalar ($\lambda \in \mathbb R)$ then, each element of the matrix $A$ gets “scaled” by $\lambda$, i.e., $\lambda A = K$ or $K_{ij} = \lambda a_{ij}$. For, $\lambda, \psi \in \mathbb R$ the following properties hold:

### Associativity
![[CleanShot 2024-06-19 at 09.41.37@2x.png]]
### Distributivity

![[CleanShot 2024-06-19 at 09.42.09@2x.png]]

>**The second question is not true for all mathematical quantity, e.g., log(x+y) ≠ log(x) + log(y)**
# Matrix Representation

### Example

Consider the equations:

$$ 2x_1 +3x_2+5x_3=1 $$

$$ 4x_1 - 2x_2 - 7x_3 = 8 $$

$$ 9x_1 + 5x_2 - 3x_3 = 2 $$

It can be written as:

$$ \begin{bmatrix} 2 & 3 & 5\\ 4 & -2 & -7\\ 9 & 5 & -3 \end{bmatrix} \begin{bmatrix} x_1\\ x_2\\ x_3 \end{bmatrix}

\begin{bmatrix} 1\\ 8\\ 2 \end{bmatrix} $$

### Important features

- System of linear equations can be compactly represented in their matrix form as $Ax = b$.
- Product, $Ax$, is a linear combination of the columns of $A$.

# Particular Solution

### Example

- Consider system of linear equations:

$$ \begin{bmatrix} 1 & 0 & 8 & -4\\ 0 & 1 & 2 & 12 \end{bmatrix} \begin{bmatrix} x_1\\ x_2\\ x_3\\ x_4 \end{bmatrix}

\begin{bmatrix} 42\\ 8 \end{bmatrix} $$

- If we take 42 times the first column and 8 times the second column, i.e.,
$$ b = \begin{bmatrix} 42\\ 8 \end{bmatrix} 42 \begin{bmatrix} 1\\ 0 \end{bmatrix} +8 \begin{bmatrix} 0\\ 1 \end{bmatrix} $$
- We get particular or special solution as: $\begin{bmatrix} 42 & 8 & 0 & 0 \end{bmatrix}^T$.

> If number of variables are more than the number of equations, then we have 
   infinitely many solutions. If number of equations are more than the number of variables, then most probably we will have no solutions.

> When we are talking about number of equations, we are talking about independent equations. For example, if you have two equations, then the third equation should not be found out by factorisation of first two equations.

### Important points

- This is not the only solution of this system of linear equations.
    
- To capture all the other solutions, we need to generate **0** in a **non-trivial** way using the columns of the matrix: Adding **0** to the special solution does not change the special solution.
    
- Expressing the third column using the first two columns as
    
    $$ \begin{bmatrix} 8\\ 2 \end{bmatrix} =8 \begin{bmatrix} 1\\ 0 \end{bmatrix} +2 \begin{bmatrix} 0\\ 1 \end{bmatrix} $$
    
    gives ($x_1,x_2,x_3,x_4$) = (8,2,-1,0)
    

### Scaling the solution

- Scaling of ($x_1,x_2,x_3,x_4$) = (8,2,-1,0) by $\lambda_1 \in \mathbb R$ produces **0** vector

$$ \begin{bmatrix} 1 & 0 & 8 & -4\\ 0 & 1 & 2 & 12 \end{bmatrix} (\lambda_1 \begin{bmatrix} 8\\ 2\\ -1\\ 0 \end{bmatrix})

\lambda_1(8c_1+2c_2-c_3) = 0 $$

### Scaling fourth column

Expressing the fourth column using the first two columns generates set of non-trivial versions of **0**, for $\lambda_2 \in \mathbb R$, as $$ \begin{bmatrix} 1 & 0 & 8 & -4\\ 0 & 1 & 2 & 12 \end{bmatrix} (\lambda_2 \begin{bmatrix} -4\\ 12\\ 0\\ -1 \end{bmatrix} )

\lambda_2(-4c_1+12c_2-c_4) = 0 $$
# General Solution

## Linear combination of particular solutions

By putting also these together we get the general solutions as:

$$ x = \begin{bmatrix} 42\\ 8\\ 0\\ 0 \end{bmatrix}

- \lambda_1 \begin{bmatrix} 8\\ 2\\ -1\\ 0 \end{bmatrix} +\lambda_2 \begin{bmatrix} -4\\ 12\\ 0\\ -1 \end{bmatrix} \forall\ \lambda_1,\lambda_2 \in \mathbb R $$

> 📌 The number of parameters that you will require to get a solution is the **number of variables - number of equations**.

### Approach

The general approach consists of the following three steps:

1. Find a particular solution to $Ax = b$.
2. Find all solutions to $Ax = 0$.
3. Combine the solutions from previous steps to get the general solution. Neither the general nor the particular solution is unique.

# Elementary transformations

## Meaning

Transforming system of linear equations into simpler form by keeping the solution set same.

- Exchange of two equations (rows in the matrix representing the system of equations).
- Multiplication of an equation (row) with a constant $\lambda$.
- Addition of two equations (rows).

### Consider system of linear equations

$$ -2x_1+4x_2-2x_3+4x_5 = -3\\ 4x_1-8x_2+3x_3-3x_4+x_5 = 2\\ x_1-2x_2+x_3-x_4+x_5=0\\ x_1-2x_2-3x_4+4x_5=a $$

### Build augmented matrix

Convert this system of equations into the compact matrix notation $Ax=b$ and build the augmented matrix.

$$ \begin{bmatrix} \begin{array}{ccccc|c} -2 & 4 & -2 & -1 & 4 & -3\\ 4 & -8 & 3 & -3 & 1 & 2\\ 1 & -2 & 1 & -1 & 1 & 0\\ 1 & -2 & 0 & -3 & 4 & a \end{array} \end{bmatrix} $$

### Row swapping
![[CleanShot 2024-06-19 at 09.43.55@2x.png]]
### Addition, multiplication, subtraction
![[CleanShot 2024-06-19 at 09.44.19@2x.png]]
![[CleanShot 2024-06-19 at 09.44.30@2x.png]]
![[CleanShot 2024-06-19 at 09.44.39@2x.png]]
# Row-Echelon Form

### Augmented matrix is in the row-echelon form

$$ x_1-2x_2+x_3-x_4+x_5=0\\ x_3-x_4+3x_5=-2\\ x_4-2x_5=1\\ 0=a+1 $$

### Particular solution

For $a = -1$ this system can be solved. A particular solution is $$ \begin{bmatrix} x_1\\ x_2\\ x_3\\ x_4\\ x_5 \end{bmatrix}

\begin{bmatrix} 2\\ 0\\ -1\\ 1\\ 0 \end{bmatrix} $$

### General solution

- The general solution, the set of all possible solutions is

$$ x = \begin{bmatrix} 2\\ 0\\ -1\\ 1\\ 0 \end{bmatrix} +\lambda_1 \begin{bmatrix} 2\\ 1\\ 0\\ 0\\ 0 \end{bmatrix} +\lambda_2 \begin{bmatrix} 2\\ 0\\ -1\\ 2\\ 1 \end{bmatrix} $$

# Reduced row-echelon form

## Definition

A matrix is in reduced row-echelon form if:

1. It is in row-echelon form.
2. Every pivot is 1.
3. The pivot is the only non-zero entry in its column.

## Gaussian Elimination

An algorithm that performs elementary transformations to bring a system of linear equations into reduced row-echelon form.

# The Minus-1 Trick

### Trick in action

- Consider matrix $A \in \mathbb R^{3x5}$ which is already in reduced row-echelon form
	![[CleanShot 2024-06-19 at 10.08.53@2x.png]]
- Augment this matrix to a 5x5 matrix by adding rows of the form at the places where the pivots on the diagonal are missing.

### General Solution

- From this form, read out the solutions of $Ax= 0$ by taking the columns of $\~A$, which contain -1 on the diagonal.
![[CleanShot 2024-06-19 at 09.45.06@2x.png]]
## Calculating the Inverse

### Objective

To compute the inverse $A^{-1}$ of $A \in \mathbb R^{nxn}$, we need to find matrix $X$ that satisfies $AX=I_n$. Then, $X = A^{-1}$.

### Approach

- Write the simultaneous linear equations of the form, $AX=I_n$.
    
- Solve for $X = \begin{bmatrix} \begin{array}{c|c|c} x_1 & ... & x_n \end{array} \end{bmatrix}$ using augmented matrix notation for a compact representation of this set of systems of linear equations to obtain
    
    $$ \begin{bmatrix} \begin{array}{c|c} A & I_n \end{array} \end{bmatrix} \rightsquigarrow ... \rightsquigarrow \begin{bmatrix} \begin{array}{c|c} I_n & A^{-1} \end{array} \end{bmatrix} $$
    
- Bring augmented equation system into reduced row-echelon form. The inverse is obtained on the right-hand side of the equation system.
    
- Thus, determining the inverse of a matrix is equivalent to solving systems of linear equations.
    

# Inverse using Gaussian Elimination

### Objective

Find inverse of

$$ A = \begin{bmatrix} 1 & 0 & 2 & 0\\ 1 & 1 & 0 & 0\\ 1 & 2 & 0 & 1\\ 1 & 1 & 1 & 1 \end{bmatrix} $$

### Approach

- Write down the augmented matrix: 
$$\begin{bmatrix} \begin{array}{cccc|cccc} 1 & 0 & 2 & 0 & 1 & 0 & 0 & 0\\ 1 & 1 & 0 & 0 & 0 & 1 & 0 & 0\\ 1 & 2 & 0 & 1 & 0 & 0 & 1 & 0\\ 1 & 1 & 1 & 1 & 0 & 0 & 0 & 1 \end{array} \end{bmatrix}$$
- Reduce to row-echelon form by Gaussian elimination. The inverse is obtained on the RHS.

$$ \begin{bmatrix} \begin{array}{cccc|cccc} 1 & 0 & 0 & 0 & -1 & 2 & -2 & 2\\ 0 & 1 & 0 & 0 & 1 & -1 & 2 & -2\\ 0 & 0 & 1 & 0 & 1 & -1 & 1 & -1\\ 0 & 0 & 0 & 1 & -1 & 0 & -1 & 2 \end{array} \end{bmatrix} $$

# Algorithms for solving a SLE

### Using pseudo-inverse

Solving a system of linear equations of the form $Ax=b$.

- Determine the inverse $A^{-1}$, such that the solution of $Ax=b$ is given as $x = A^{-1}b.$
- This is only possible if $A$ is a square matrix and invertible.
- Else use the transformation:
	$Ax = b \Leftrightarrow A^TAx = A^Tb \Leftrightarrow x = (A^TA)^{-1}A^Tb$
- $(A^TA)^{-1}A^T$ is called the **Moore-Penrose pseudo-inverse**.
> **_Pseudo-inverse and Inverse of a square matrix would be same._**
```MATLAB
dmat = [1,2,1,2;1,-1,4,1];
b = [1;1];

emat = transpose(dmat)*dmat;
ymat = transpose(dmat)*b;
x1 = emat\ymat;
disp(x1);
x2 = pinv(dmat)*b;
disp(x2);
% This will have different values as it has infinitely many solutions
```

### Using iteration
- Let $x_*$ be a solution of $Ax = b$. The key idea of these iterative methods is to setup an iteration of the form$$x^{(k+1)}=Cx^{(k)}+d$$
	for suitable $C$ and $d$ that reduces the residual error $||x^{(k+1)}-x_*||$ in every iteration and converges to $x_*$. We will introduce norms $||\cdot||$, which allow us to compute similarities between vectors.
