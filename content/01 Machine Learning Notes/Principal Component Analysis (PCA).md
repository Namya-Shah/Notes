---
Link: 
tags:
  - ML
---
# Notes
**Use Case:** Dimensionality reduction to simplify complex datasets while preserving important information.
- Principal Component Analysis (PCA) is a technique used in statistics and data science to reduce the dimensionality of a dataset while retaining most of the variability present in the data. It is used to identify patterns in data, to compress it for storage or transmission, and to reduce noise.
- PCA works by finding the linear combinations of variables in a dataset that explain the maximum amount of variance in the data. These linear combinations are called principal components, and they are ordered by the amount of variance they explain. The first principal component explains the most variance, the second explains the next most, and so on.
- To perform PCA, the data is first standardized to have zero mean and unit variance. Then, the covariance matrix of the standardized data is computed. The principal components are then calculated by finding the eigenvectors and eigenvalues of the covariance matrix. The eigenvectors are the principal components, and the eigenvalues represent the amount of variance explained by each component.
## Steps for PCA Algorithm
1. **Getting the dataset**
	- Firstly, we need to take the input dataset and divide it into two subparts X and Y, where X is the training set, and Y is the validation set.
2. **Representing data into a structure**
	- Now we will represent our dataset into a structure. Such as we will represent the two-dimensional matrix of independent variable X. Here each row corresponds to the data items, and the column corresponds to the Features. The number of columns is the dimensions of the dataset.
3. **Standardizing the data**
	- In this step, we will standardize our dataset. Such as in a particular column, the features with high variance are more important compared to the features with lower variance.
	- If the importance of features is independent of the variance of the feature, then we will divide each data item in a column with the standard deviation of the column. Here we will name the matrix as Z.
4. **Calculating the Covariance of Z**
	- To calculate the covariance of Z, we will take the matrix Z, and will transpose it. After transpose, we will multiply it by Z. The output matrix will be the Covariance matrix of Z.
5. **Calculating the Eigen Values and Eigen Vectors**
	- Now we need to calculate the eigenvalues and eigenvectors for the resultant covariance matrix Z. Eigenvectors or the covariance matrix are the directions of the axes with high information. And the coefficients of these eigenvectors are defined as the eigenvalues.
6. **Sorting the Eigen Vectors**
	- In this step, we will take all the eigenvalues and will sort them in decreasing order, which means from largest to smallest. And simultaneously sort the eigenvectors accordingly in matrix P of eigenvalues. The resultant matrix will be named as P*.
7. **Calculating the new features or Principal Components**
	- Here we will calculate the new features. To do this, we will multiply the P* matrix to the Z. In the resultant matrix Z*, each observation is the linear combination of original features. Each column of the Z* matrices are independent of each other.
8. **Remove less or unimportant features from the new dataset**
	- The new feature set has occurred, so we will decide here what to keep and what to remove. It means, we will only keep the relevant or important features in the new dataset, and unimportant features will be removed.
## Common Terms
- **Dimensionality**: It is the number of features or variables present in the given dataset. More easily, it is the number of columns present in the dataset.
- **Correlation**: It signifies how strongly two variables are related to each other. Such as if one changes, the other variables also gets changed. The correlation value ranges from -1 to +1. Here, -1 occurs if variables are inversely proportional to each other, and +1 indicates that variables are directly proportional to each other.
- **Orthogonal**: It defines that variables are not correlated to each other, and hence the correlation between the pair of variables is zero.
- **Eigenvectors**: If there is a square matrix M, and a non-zero vector v is given. Then v will be an eigenvector if Av is the scalar multiple of v.
- **Covariance Matrix**: A matrix containing the covariance between the pair of variables is called the Covariance matrix.
# References
---
1. 
