---
Lecture Date: 2025-02-18
Presentation: 
Links: 
Subject:
  - "[[EM 618 - Optimization for Data Science and Machine Learning]]"
References:
  - "[[Gradient Descent]]"
tags:
  - EM618
---
```table-of-contents
```
# Why Move to Constrained Optimization?
- **Real-world limitations**: Parameter bounds, resource budgets, domain restrictions.
- **Regularization**: Impose certain norms or structure on solutions.
- **Physical or domain constraints**: Non-negativity, sum constraints, equality constraints, etc.
# Linear Regression

$$
y_i \approx w^Tx_i + b_i, \ i\text{ = 1,...,n}
$$

- $x_i \in \mathbb{R}^d$ are feature vectors.
- $w \in \mathbb{R}^d$ are the regression coefficients.
- $b$ is an intercept (often merged into $w$ by augmenting a constant feature).
## Least Squares

$$
\min_{w,b} \sum^n_{i=1}(y_i - (w^Tx_i+b))^2
$$

- This measures the sum of squared residuals.
- We want to find $w$ and $b$ that minimize the sum.
- $\div, \times, +$ of constants do not change nature of optimization problem.
- $w$: Invariable by choice of constants.
## Matrix Notation for Linear Regression
- Let $X$ be an $n \times d$ matrix whose $i$-th row is $x_i^T$.
- Let $y$ be an $n \times 1$ vector with entries $y_i$.
- Then the objective can be written as:

$$
\min_w ||y-Xw||_2^2 = (y-Xw)^T(y-Xw)
$$

- The equation is L2-Norm and square of error.
### Expanding the Objective Function

$$
||y - Xw||_2^2 = (y-Xw)^T(y-Xw) = y^Ty - 2y^T(Xw)+(Xw)^T(Xw)
$$

- Commonly used for deriving the optimal solution via gradient = 0.

$$
\nabla_wf(w) = \nabla_w[y^Ty - 2y^TXw + w^TX^TXw]
$$

- $y^Ty$ is constant with respect to $w$.
- $-2y^TXw$ gradient is $-2X^Ty$.
- $w^TX^TXw$ gradient is $2X^TXw$.
### Setting Gradient to Zero

$$
\nabla f(w) = -2X^Ty + 2X^TXw=0
$$

Rearranging,

$$X^TXw = X^Ty$$

**Normal Equations.**$$w = (X^TX)^{-1}X^Ty$$

- For the solutions to exist, $(X^TX)^{-1} \ne 0$.
- $X^TX$ should be invertible (or full column rank)
- This is the **Ordinary Least Squares (OLS)** solution
- No constraints on $w$ in standard linear regression.
- Geometric interpretation: $w^*$ projects $y$ onto the column space of $X$.
- Minimizes the sum of squared orthogonal distances to the data points.
- **No explicit bound** on the size of $w$: can lead to large coefficient values if columns are nearly collinear or if $d$ is large.
### Overfitting: Potential Issue
- In high-dimensional settings, OLS might "overfit" the training data.
- Coefficients can become very large, leading to poor generalization.
- **Regularization** addresses this by constraining $w$.
# Unconstrained Linear Regression
- Standard linear regression is a prime example of **unconstrained** optimization.
- Closed-form solution is found via normal equations.
- Next: We impose constraints (or equivalently, **penalties**) to tackle overfitting or domain restrictions.
## Why Constrain the Coefficients?
- **Overfitting**: Large or erratic coefficients do not generalize well.
- **Interpretability**: Some domains want simpler or sparser models.
- **Domain Knowledge**: Certain parameters may need to be non-negative or bounded.
- **Stability**: In ill-posed problems (e.g., $d >> n$), constraints can stabilize solutions.
# Misc. Notes
- For **linear regression** like problems, we don't need to use gradient descent like algorithm to obtain our $\theta$.
- 
