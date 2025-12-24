---
Lecture Date: 2024-08-01
Presentation: 
Links:
  - "[[Lasso Regression]]"
Subject:
  - "[[EM 613 - Mathematical Models for Data Science]]"
tags:
  - EM613
---
```table-of-contents
```
# Lasso Regression
- Lasso (Least Absolute Shrinkage and Selection Operator) is a regression method that performs both variable selection and regularization.
- It aims to enhance the prediction accuracy and interpretability of the statistical model.
- **Lasso Regression + Elastic net + ridge**: Embedded approaches for feature selection
- [[Lecture 16#Variance Thresholding]] is a filter method
- [[Lecture 16#F Regression]] is a wrapper method.
## Introduction
- **Penalise the large coefficients!**
- Lasso (Least Absolute Shrinkage and Selection Operator) is a regression method that performs both variable selection and regularization.
- It aims to enhance the prediction accuracy and interpretability of the statistical model.
- ***Why do we penalize the large coefficients?***
	- If some feature is getting importance, try to drop it and then see how it affects the other features.
	- Collinearity or multi-collinearity. If we have two features that are linear to each other. When we do PCA, it will remove one of the two feature.
> *Models should be generalizable and scalable*
- 