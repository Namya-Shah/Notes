---
Lecture Date: 2024-06-06
Presentation: "[[Lecture 1.pdf]]"
Links:
  - "[[MATLAB]]"
Subject:
  - "[[EM 613 - Mathematical Models for Data Science]]"
tags:
  - Matlab
  - EM613
---
```table-of-contents
```
# Variables, Operators, & Precedence

## Variables

- Entities that store a certain data under a given name

## Operators

- Numeric
- Relational
- Special Character

## Operator Precedence
- Different operators have different hierarchy
- Operations of same precedence are carried out from left to right

| Operator        | Uses                                                                  |
| --------------- | --------------------------------------------------------------------- |
| ()              | Parantheses                                                           |
| ‘  .’           | Transpose & Elementwise Transpose                                     |
| ^  .^           | Power & Elementwise Power                                             |
| ^+   ^-         | Power with unary plus or minus                                        |
| • -   ~         | Unary plus, unary minus, and negation                                 |
| $*$,/, ./, .$*$ | Matrix multiplication, division, elementwise multiplication, division |
| +, -            | Addition, Subtraction                                                 |
| :               | Colon Operator                                                        |
| < <= > >= == ~= | Relational Operators                                                  |
| &               | Elementwise AND                                                       |
| \|              | Elementwise OR                                                        |

### Elementwise Operations (.)
- We use elementwise operations when we have a matrix. If we don’t use elementwise operator. It will throw an error.
![[CleanShot 2024-06-21 at 09.40.04@2x.png]]
# Algebraic Equation to MATLAB expressions
![[CleanShot 2024-06-21 at 09.40.21@2x.png]]

# Arrays and Matrices

1. 1D Array/Vector
    - A collection of values in either row or a column form
    - Elements of an array are separated by a space or comma
    ![[CleanShot 2024-06-21 at 09.40.47@2x.png]]
    
2. 2D Array/Matrix
    - A matrix is a collection of data, organised into rows and columns
    - Each row is separated by a semicolon ;
    
    ![[CleanShot 2024-06-21 at 09.41.10@2x.png]]
    
3. Multidimensional Array
    - Simply an array of arrays

## Row Matrix

```matlab
clc;
clear all variables;

a = [1,2,3,4,5];
b = [1,2,3.0,2^0.5];
c = [i, -i, 1+i, 1-i];
d = [j, -j, 1+j, 1-j]

% Command line

% a prints out 1 2 3 4 5
% b prints out 1.000 2.000 3.000 1.414
% c prints out 0.000 + 1.000i   0.000 - 1.000i   1.000 + 1.000i   1.000 - 1.000i
% d prints out 0.000 + 1.000i   0.000 - 1.000i   1.000 + 1.000i   1.000 - 1.000i
% size(a) prints out 1 5
```

## Column Matrix

```matlab
clc;
clear all variables;

a = [1;2;3;4;5];

% Command line

% a prints out
% 1
% 2
% 3 
% 4
% 5

% size(a) prints out 5 1
```

- We can have different types of integer matrix, float matrix, double matrix

# Creating 1-D Arrays in multiple ways

- Let A, B and C be a row-vectors of order *1 x m*.

- **Multiple ways to initialize a 1D array**
	![[CleanShot 2024-06-21 at 09.43.57@2x.png]]

- **Using colon operator**
    - Arrays that follow an arithmetic progression can be initialized using the colon (:) operator
	![[CleanShot 2024-06-21 at 09.44.19@2x.png]]

- Evenly spaced arrays can be created as follows
	![[CleanShot 2024-06-21 at 09.44.39@2x.png]]

- The arrays could be created in a decreasing trend too.
	![[CleanShot 2024-06-21 at 09.44.59@2x.png]]
- Using linspace() function
	![[CleanShot 2024-06-21 at 09.45.15@2x.png]]
# Some basic operations with arrays

- Let A and B be a row-vectors of order *1 x m*
- Let C be a column vector of order *n x 1*
- To access i$^{th}$ element of a 1D array, follow the syntax $arrayname(i)$

![[CleanShot 2024-06-21 at 09.45.40@2x.png]]

- The colon (:) operator is used to subscript arrays
![[CleanShot 2024-06-21 at 09.45.58@2x.png]]

- If the last index is unknown, **end** keyword is used
![[CleanShot 2024-06-21 at 09.46.19@2x.png]]

- Since a vector is considered as a matrix in MATLAB, the following is valid too
![[CleanShot 2024-06-21 at 09.46.35@2x.png]]


>💡 **MATLAB is case-sensitive**

# Creating 2D Matrices in multiple ways

- Let A, B, and C be a row-vectors of order `m x m`
- Let C be a matrix of order `p x q`
- Multiple ways to initialize a matrix

![[CleanShot 2024-06-21 at 09.46.51@2x.png]]

- Matrix can be created by concatenating multiple arrays of same size

![[CleanShot 2024-06-21 at 09.47.40@2x.png]]

- A bigger matrix can be created by concatenating smaller matrices

![[CleanShot 2024-06-21 at 09.47.56@2x.png]]
# Some basic operations with matrices
- Let A and B be a matrices of order $m * n$
- Let C be a matrix of order $p * q$
- Conjugate transpose of a matrix
	![[CleanShot 2024-06-21 at 09.50.14@2x.png]]
# Matrix Operations

- Let A and C be a matrices of order `m x n`
- Let B be a matrix of order `p x q`
- Matrix multiplication
    - Matrices A and B can be multiplied if `n = p`
	    ![[CleanShot 2024-06-21 at 09.51.26@2x.png]]
	    ![[CleanShot 2024-06-21 at 09.51.43@2x.png]]
- The ***.*** operator is used to specify elementwise operation
    - Elementwise operations can be performed on matrices of same dimensions only
        
        ![[CleanShot 2024-06-21 at 09.52.03@2x.png]]
        ![[CleanShot 2024-06-21 at 09.52.18@2x.png]]

# Matrix manipulations and operations

- Let A and B be a matrices of order `m x n`
- Let C be a matrix of order `*p* x *q*`
- Reshaping a matrix
    - $reshape(A,[m,n])$ reshapes the matrix $A$ into a matrix of size `*m* x *n`* columnwise
    - Gives an error if the matrix $A$ does not contain `*mn`* elements
	    ![[CleanShot 2024-06-21 at 09.52.49@2x.png]]
    
- Repeating a matrix using $repmat()$
    - $repmat(a,[m,n])$ creates a larger matrix where $m$ rows and $n$ columns of the matrix $a$ are present
	    ![[CleanShot 2024-06-21 at 09.53.05@2x.png]]
    

# Inbuilt Special Matrices

- Matrix with all entries as 1
    
    ![[CleanShot 2024-06-21 at 09.53.21@2x.png]]
    
- Null matrix
    
    ![[CleanShot 2024-06-21 at 09.53.36@2x.png]]
    
- Magic matrix
    
    ![[CleanShot 2024-06-21 at 09.53.52@2x.png]]
    
- Diagonal matrix
    
    ![[CleanShot 2024-06-21 at 09.54.08@2x.png]]
    
- Identity matrix
    
    ![[CleanShot 2024-06-21 at 09.54.22@2x.png]]
    

# Some useful inbuilt commands/keywords

| Keywords           | Commands                                     |
| ------------------ | -------------------------------------------- |
| clc                | Clears the command window                    |
| clear variablename | Clears the variable ‘variablename’           |
| clf                | Clears the contents of a figure              |
| format style       | Sets the output display style                |
| figure             | Opens a new figure window                    |
| close figurename   | Closes the figure ‘figurename’               |
| print              | Prints the current figure                    |
| save               | Saves the current variables in the workspace |

## Mathematical functions & Trigonometrical functions

| Mathematical Functions | Used as                     |
| ---------------------- | --------------------------- |
| sin(x)                 | Sine                        |
| cos(x)                 | Cosine                      |
| tan(x)                 | Tangent                     |
| asin(x)                | Arc Sine                    |
| acos(x)                | Arc Cosine                  |
| atan(x)                | Arc Tangent                 |
| log(x)                 | Natural Logarithm           |
| log10(x)               | Logarithm base-10           |
| exp(x)                 | Exponential                 |
| sqrt(x)                | Square Root                 |
| abs(x)                 | Absolute Value              |
| sgn(x)                 | Signum Function             |
| max(x)                 | Maximum Value               |
| min(x)                 | Minimum Value               |
| ceil(x)                | Round towards +∞            |
| floor(x)               | Round towards -∞            |
| round(x)               | Round to nearest integer    |
| rem(x,y)               | Remainder after division    |
| inv(A)                 | Inverse of matrix A         |
| conj(x)                | Complex conjugate           |
| pi                     | π                           |
| i j                    | Imaginary Root  ( sqrt(−1)) |
| Inf                    | ∞                           |
| NaN                    | Not a Number                |
- ceil(x) → if you write ceil(4.5), the answer would be 5
- floor(x) → if you write floor(4.5), the answer would be 4