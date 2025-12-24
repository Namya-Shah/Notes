---
Lecture Date: 2024-07-27
Presentation: 
Links:
  - "[[Variance Thresholding]]"
  - "[[F Regression]]"
  - "[[Lasso Regression]]"
Subject:
  - "[[EM 613 - Mathematical Models for Data Science]]"
tags:
  - EM613
---
```table-of-contents
```

> If you have missing data, then we don't do [[Principal Component Analysis (PCA)]]
# Feature Selection
- Feature selection is a process of selecting a subset of relevant features for model construction.
- Improves model performance by reducing overfitting, enhancing generalization, and reducing training time.
# Methods of Feature Selection
- Filter Methods
- Wrapper Methods
- Embedded Methods
# Variance Thresholding
- Variance Thresholding is a simple baseline approach to feature selection.
- Removes all features whose variance does not meet a certain threshold.
- **Features with low variance are considered less informative.**
- We remove features where it is constant and not variable as it won't affect our data.
- We do this step before standardization because after standardization, the variance will become 1.
## Mathematical Explanation
- For a feature $x_j$:

$$
\sigma_j^2 = \frac 1 n \sum^n_{i=1}(x_{ij}-\mu_j)^2
$$

- Where $\mu_j$ is the mean of the feature $x_j$:

$$
\mu_j = \frac 1 n \sum^n_{i=1}x_{ij}
$$

- A feature is selected if $\sigma_j^2 \geq \tau$, where $\tau$ is the variance threshold.
## Example
- Consider a dataset with three features and five samples:

$$
\begin{pmatrix}
1 & 2 & 0.5 \\ 1 & 2 & 0.4 \\ 1 & 2 & 0.45 \\ 1 & 2 & 0.55 \\ 1 & 2 & 0.6
\end{pmatrix}
$$

- Variances of features:

$$
\sigma_1^2 = 0, \ \sigma_2^2=0, \ \sigma_3^2 = 0.005
$$

- With $\tau = 0.01$, only feature 3 is selected.
## Benefits and Limitations
### Benefits:
- Simple to implement and understand
- Computationally efficient
### Limitations:
- Only considers variance, not feature importance.
- May remove useful features with low variance.
# F Regression
- Strictly supervised way for feature selection
- If it is good regression, we will select the feature and vice-versa
- 
## Rationale
- We will look for the relation in $x$ and $y$.
## P-Value Interpretation
- **High P-Value** ($>$ 0.005):
- **Low P-Value** ($\leq$ 0.05):
### Limitations

- Degree of randomness is entropy
# Lasso Regression
- 