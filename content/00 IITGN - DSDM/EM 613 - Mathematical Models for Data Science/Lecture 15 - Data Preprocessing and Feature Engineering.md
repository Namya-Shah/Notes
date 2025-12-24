---
Lecture Date: 2024-07-25
Presentation: 
Links:
  - "[[Dimensionality Reduction]]"
  - "[[Polynomial Features]]"
  - "[[Principal Component Analysis (PCA)]]"
Subject:
  - "[[EM 613 - Mathematical Models for Data Science]]"
tags:
  - EM613
---
```table-of-contents
```
# Outcomes of this lecture
- Understand how to expand and reduce the dimensions of data by feature engineering techniques like Polynomial Features and PCA/t-SNE, respectively.
- Understand the intuition and mathematics behind PCA (A linear dimensionality reduction technique)
- Understand the intuition and mathematics between t-SNE (A non-linear dimensionality reduction technqiue)
- Write codes in Python to implement various feature engineering techniques discussed and improvise on the techniques not discussed.

# Polynomial Features
## Why do we need Higher-order features?
- Under scenarios where the interactions between features might be significant, generating higher-order features allows capturing more complex patterns in the data.
	![[CleanShot 2024-07-27 at 21.37.06.png]]
## Introduction to Polynomial Features
- **Definition:** Polynomial features implies creating higher-power features of the existing features.
- **Purpose:** To capture non-linear relationships between features and the target variable.
- **Example:** For a feature $x$, polynomial features could be $x^2,x^3,x^4,...$. The interaction between features (say $x_1,x_2,x_3$) is defined by polynomial features like $x_1 \cdot x_2, \ x_2 \cdot x_3$ and $x_3 \cdot x_1$.
## Order of Polynomial Features
- For features $X$, do we need $X^2, X^3, ..., X^n$. Where to draw the line? How to choose the order of Polynomial Features?
- It is always possible to fit a polynomial of order $n-1$ perfectly to a set of $n$ points.
- However, we want our models to generalize. So instead of a perfect fit, we want to select order $n$ which minimizes error (MSE, MAE etc.) while improving the quality of fit ($R^2$).
- **Classification:** We use transformation to classify different 
- Doctors use feature engineering to identify the diseases.
- *Increasing order of polynomials, it increases complexity.*
- Either the model is biased or it has high variance
- Too many features lead to [[Overfitting]]
# Dimensionality Reduction
## What is Dimensionality Reduction?
- **Definition:** Dimensionality reduction is the process of reducing the number of random variables under consideration by obtaining a set of principal variables.
- **Types:**
	- **Feature Selection:** Selecting a subset of the original features.
	- **Feature Extraction:** Transforming the data into a new set of features.
## Why is Dimensionality Reduction necessary?
- **Curse of Dimensionality:** *High-dimensional spaces are sparse, making pattern recognition difficult and model training less effective.*
- **Computational Efficiency:** *Reducing dimensions decreases computational costs and improving processing time.*
- **Overfitting:** *Simplifies models to improve generalization and reduce overfitting by removing redundant and noisy features.*
- **Visualization:** *Allows for visualization of complex data in 2D or 3D spaces, making it easier to understand and interpret.*
### Example of Dimensionality Reduction
- **Scenario:** Imagine a dataset with three features: height, weight, and age.
- **Visualization:**
	- **Original Data:** Data points are scattered in a 3D space.
	- **Reduction to 2D:** Using PCA, we project the data onto a 2D plane defined by the two principal components.
![[CleanShot 2024-07-28 at 17.05.13.png]]
### Benefits of Dimensionality Reduction
- **Simplified Models:** Easier to interpret and analyze with fewer features.
- **Improved Performance:** Faster training times and reduced computational resources.
- **Enhanced Generalization:** Less overfitting due to the removal of noise and redundant features.
- **Better Visualization:** High-dimensional data projected into 2D or 3D spaces for easier understanding.
### Real World Example on Dimensionality Reduction
[PCA on Iris Dataset](https://colab.research.google.com/drive/1BObQRfOib4Xjb-2FrZYbTlj10rxwZ2Nz?usp=sharing)
# Principal Component Analysis
***To learn this, you need to know [[Lecture 8 - Singular Value Decomposition]]***
- **Definition**
	- PCA is a statistical technique used to simplify a dataset by reducing its dimensions while retaining most of the original variability.
- **Objective**
	- Transform the data into a new coordinate system where the greatest variance comes to lie on the first coordinate (principal component), the second greatest variance on the second coordinate, and so on.
- **Genesis**
	- Developed by Karl Pearson in 1901
	- Later independently formulated by Harold Hotelling in the 1930s.
- **Applications**
	- Data Compression
	- Noise Reduction
	- Data Visualization
	- Feature Extraction
- *Robust to outliers*
- *It is a data pre-processing. This features will be fed into a machine learning model.*
- *It is a data transformation approach*
- *PCA is a last step before it is fed into the machine learning model*
- *We can't get the original data back but we can get the covariance matrix*
## Key Concepts of PCA
- **Variance and Covariance:**
	- Variance measures the spread of data points.
	- Covariance indicates the direction of the linear relationship between data points.
- **Eigenvalues and Eigenvectors:** 
	- Eigenvalues represent the magnitude of the variance in the direction of the eigenvector.
	- Eigenvectors represent the direction of the new feature space.
- **Principal Components:**
	- Linear combinations of the original variables.
	- Ordered by the amount of variance they capture from the data.
- **Dimensionality Reduction:** 
	- Reduce the number of dimensions by selecting the top $k$ principal components.
	- Retains most of the variability in the dataset.
### Step 1: Standardization
- **Purpose:** To ensure each feature contributes equally to the analysis.
- **Formula:**

$$
X_{std}=\frac {X-\mu} \sigma
$$

- Where:
	- $X$ is the original data matrix.
	- $\mu$ is the mean of each feature.
	- $\sigma$ is the standard deviation of each feature.
### Step 2: Covariance Matrix Calculation
- **Purpose:** To understand the relationships between features.
- **Formula:**

$$
C = \frac 1 {N-1} X_{std}^T X_{std}
$$

- Where:
	- $C$ is the covariance matrix.
	- $N$ is the number of observations.
	- $X_{std}$ is the standardized data matrix.
### Step 3: Eigenvalue and Eigenvector Calculation
- **Purpose:** To find the directions of maximum covariance.
- **Eigenvalue Problem:**

$$
Cv_i = \lambda_iv_i
$$

- Where:
	- $C$ is the covariance matrix
	- $v_i$ is the $i-th$ eigenvector.
	- $\lambda_i$ is the $i-th$ eigenvalue.
> ***Spectral Decomposition Theorem***
> Any symmetric matrix $A$ can be decomposed into a set of eigenvalues and eigenvectors:
> $A = V\Lambda V^T$
> Where $V$ is a matrix of eigenvectors and $\Lambda$ is a diagonal matrix of eigenvalues.
### Step 4: Principal Component Selection
- **Purpose:** To reduce dimensionality by selecting the top $k$ eigenvectors.
- **Procedure:**
	- Sort the eigenvalues in descending order.
	- Select the top $k$ eigenvectors corresponding to the largest eigenvalues.
- **Principal Components Matrix:**

$$
V_k = [v_1,v_2,...,v_k]
$$

### Step 5: Projection
- **Purpose:** To transform the data into the new coordinate system defined by the principal components.
- **Formula:**

$$
X_{pca} = X_{std}V_k
$$

- Where:
	- $X_{pca}$ is the projected data matrix.
	- $V_k$ is the matrix of the top $k$ eigenvectors.

## Projection Example in Cartesian Coordinates
- Consider a standardized data point $x_{std} = [x_1,x_2]^T$.
- Principal Component 1 (PC1) is $v_1 = [v_{11}, v_{12}]^T$.
- **Projection onto PC1:**

$$
z_1 = x_{std} \ \cdot \ v_1 = x_1v_{11} + x_2v_{12}
$$

- Principal Component 2 (PC2) is $v_2 = [v_{21}, v_{22}]^T$.
- **Projection onto PC2:**

$$
z_2 = x_{std} \ \cdot v_2 = x_1v_{21} + x_2v_{22}
$$

- **Projected Point:**

$$
x_{pca} = [z_1, z_2]^T
$$

## Example
![[CleanShot 2024-07-30 at 10.14.37.png]]
### Step 1: Standardization
- Calculate the mean ($\mu$) and standard deviation ($\sigma$) for each feature.
	- **Mean:**

$$
\mu = (2.25 \quad 2.48 \quad 2.75 \quad 3.07)
$$

	- **Standard Deviation:**

$$
\sigma = (0.85 \quad 0.83 \quad 0.81 \quad 0.73)
$$

	- **Standardized Data Matrix:**

$$
X_{std} =
\begin{pmatrix}
0.29 & -0.10 & 0.68 & 0.72\\
-2.06 & -2.14 & -1.79 & -1.77\\
-0.06 & 0.51 & 0.07 & 0.18\\
-0.41 & -0.34 & -0.43 & -0.37\\
1.00 & 0.63 & 1.42 & 1.27\\
0.24 & 0.26 & 0.07 & -0.11
\end{pmatrix}
$$

### Step 2: Covariance Matrix Calculation
- Compute the covariance matrix C.
- **Formula:**

$$
C = \frac 1 {N-1} X_{std}^T X_{std}
$$

- **Covariance Matrix:**

$$
C = \begin{pmatrix}
1.00 & 0.93 & 0.96 & 0.91\\
0.93 & 1.00 & 0.89 & 0.83\\
0.96 & 0.89 & 1.00 & 0.94\\
0.91 & 0.83 & 0.94 & 1.00
\end{pmatrix}
$$

### Step 3: Eigenvalue and Eigenvector Calculation
- Solve the eigenvalue problem $Cv_i = \lambda_i v_i$.
- **Eigenvalues:**

$$
\lambda_1 = 3.76, \ \lambda_2 = 0.23, \ \lambda_3 = 0.01, \ \lambda_4 = 0.00
$$

- **Eigenvectors:**

$$
v_1 = \begin{pmatrix} 0.51 \\ 0.50 \\ 0.51 \\ 0.47 \end{pmatrix}, \ v_2 = \begin{pmatrix} -0.48 \\ -0.18 \\ 0.61 \\ 0.60 \end{pmatrix}, \ v_3 = \begin{pmatrix} 0.29 \\ -0.64 \\ -0.14 \\ 0.69 \end{pmatrix}, \ v_4 = \begin{pmatrix} -0.64 \\ 0.54 \\ -0.56 \\ 0.01 \end{pmatrix}
$$

#### Spectral Decomposition Theorem
Any symmetric matrix $A$ can be decomposed into a set of eigenvalues and eigenvectors:

$$A = V\Lambda V^T$$

Where $V$ is a matrix of eigenvectors and $\Lambda$ is a diagonal matrix of eigenvalues.
- **Symmetric Matrix:** The theorem applies to symmetric matrices, which are equal to their transpose.

$$
A = A^T
$$

- **Eigenvalues:** The diagonal elements of $\Lambda$ represent the eigenvalues of $A$.
- **Eigenvectors:** The columns of $V$ are the eigenvectors of $A$.
- **Orthogonal Matrix:** The matrix $V$ is orthogonal, meaning $V^TV=I$.
- **Decomposition:** This decomposition expresses $A$ in terms of its eigenvalues and eigenvectors, providing insights into its structure.
#### Principal Component Selection
- Select the top $k$ eigenvectors. Here, we choose the top 2 for visualization.
- **Principal Component Matrix:**

$$
V_2 = [v_1,v_2] = \begin{pmatrix} 0.51 & -0.48 \\ 0.50 & -0.18 \\ 0.51 & 0.61 \\ 0.47 & 0.60 \end{pmatrix}
$$

### Step 5: Projection
- Project the standardized data onto the principal components.
- **Formula:**

$$
X_{pca} = X_{std}V_2
$$

- **Project Calculation:** For the first observation:

$$
x_{std}^{(1)} = \begin{pmatrix} 0.29 \\ -0.10 \\ 0.68 \\ 0.72 \end{pmatrix}
$$

$$
x_{pca}^{(1)} = x_{std}^{(1)}\cdot V_2 = (0.29 \quad -0.10 \quad 0.68 \quad 0.72) \ \cdot \ \begin{pmatrix} 0.51 & -0.48 \\ 0.50 & -0.18\\ 0.51 & 0.61\\ 0.47 & 0.60\end{pmatrix} = \begin{pmatrix} 0.90\\ 0.85 \end{pmatrix}
$$

## Alternative PCA Techniques
- **Singular Value Decomposition (SVD):**
	- Uses the singular value decomposition of the data matrix.
	- More numerically stable than eigenvalue decomposition.
	- Directly decomposes the centered data matrix $X$ into $U \Sigma V^T$.
- **Kernel PCA:**
	- Extends PCA to nonlinear dimensionality reduction.
	- Uses kernel functions to project data into higher-dimensional space where linear separability is possible.
	- Useful for complex datasets where linear PCA fails.
- **Incremental PCA (IPCA):**
	- Handles large datasets by processing data in mini-batches.
	- Suitable for out-of-core learning scenarios.
	- Computes a low-rank approximation of the data.
## Advanced PCA Variants
- **Sparse PCA:**
	- Introduces sparsity in the principal components.
	- Useful for high-dimensional data with many irrelevant features.
	- Achieved through regularization techniques.
- **Robust PCA:**
	- Decomposes the data matrix into low-rank and sparse components.
	- Handles outliers and noise in the data.
	- Useful in applications like background subtraction in video surveillance.
- **Probabilistic PCA (PPCA):**
	- Assumes a probabilistic model for the data.
	- Estimates the principal components using maximum likelihood estimation.
	- Useful for missing data imputation and latent variable models.

$$
[\frac{\partial L}{\partial a} = 2a + \lambda = 0 \implies \lambda = -2a]
[\frac{\partial L}{\partial b} = 8b + 3\lambda = 0 \implies 8b - 6a = 0 \implies 4b = 3a \implies b = \frac{3a}{4}]
$$
