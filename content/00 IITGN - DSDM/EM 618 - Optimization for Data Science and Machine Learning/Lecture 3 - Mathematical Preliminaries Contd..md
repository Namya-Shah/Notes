---
Lecture Date: 2025-01-22
Presentation: "[[Lecture 2 Mathematical Preliminaries Jan 17 2025 (1).pdf]]"
Links: 
Subject:
  - "[[EM 618 - Optimization for Data Science and Machine Learning]]"
References: 
tags:
  - EM618
  - Quadratic-Equations
  - Hessian-Matrix
  - Eigenvalues
---
```table-of-contents
```
# Quadratic Equations
- Even if $f$ is not globally quadratic near a minimum it behaves like a quadratic if $f$ is smooth.
- $A$ must be invertible for the objective function to be quadratic
## Hessian in Quadratic

$$
\nabla^2 f(x) = A \ (const.)
$$

- If $A$ is positive definite => unique global min.
- If $A$ has negative/zero eigenvalues => not strictly convex => possibly no unique solution
### Example
- In 2D,

$$
A = \begin{pmatrix}
4 & 1 \\
1 & 3
\end{pmatrix}, \ b = \begin{pmatrix}
3 \\
2
\end{pmatrix}
$$

- Then, $\nabla^2 f(x) = A$, so $f$ if "bowl-shaped". Minimizer at $Ax = b$.
### Conclusion
- Quadratic problems are easier to solve exactly (no iterations needed if you invert $A$).
- Non-quadratic => often rely on iterative methods, but still use Hessian info *locally* (Newton)
- **RMSE is $L_2$ Norm of $Z (Z = y_i - \hat y_i)$.**
## Quadratic Functions
### General Form

$$
f(x) = \frac{1}{2}x^TAx - b^Tx + \text{const.}
$$

- Where $A$ should be symmetric
- If $A$ is positive definite => $f$ is convex
- Minimizer solves $Ax = b$
- For the first term, we use $x^T$ to make the whole term scalar and on the second term we use $b^T$ to make it scalar.

- Inflection behavior
	- When gradients change the sign
	- Gradients change sign when slope becomes zero
	- When function does not have inflection behavior -> monotonically increasing/decreasing
- Always define local minima / local maxima -> To get stationary point
- Unbounded function does not have stationary points
- #### $L_1$ Norm
	- It may have non-differentiable at some point
	- Linear Bias
		- Graph
			![[CleanShot 2025-01-24 at 00.37.22@2x.png]]
			- As the graph shows non-differentiability at one of the point
- #### $L_2$ Norm
	- Square of Errors
- Higher order norms are used for parameter estimation (Methods of L-moment -> Spatial Auto Correlation)
- PCA is related to eigenvalues
- $\alpha = \nabla^2$ -> Approximation (highly)
- $f(x) = ax^2 +bx + c$ -> Convex in nature always
- Simplex method is linear programming method
- If the objective function is quadratic, the linear solution is $x = A^{-1}b$.
- If the function is quadratic, no need to worry about Hessian

$$
f(x+h) = f(x) + h*f'(x) + \frac{h^2}{2!} * f''(x)
$$

- Suppose if $f'(x)$ is increasing, it means that the slope is increasing which identifies as maximum. For minimum, we use $x_{k+1} = x_k - \alpha \nabla(f)$ which is also known as gradient descent or descending the gradient
	- Assuming that higher order gradients don't matter
	- Here, $\alpha$ is "learning rate" or hyperparameter
- Covariance matrices are symmetric => real eigenvalues
- PCA relies on eigen-decomposition of $X^TX$ or the covariance matrix
> [!IMPORTANT] IMPORTANT
> **Hessian of real-valued functions** are **symmetric**; their **eigenvalues** tells us about **local curvature** (*min*/*max*/*saddle*)
- PCA is unconstrained optimization problem, whose solution are eigenvalues
---
# Questions
1. If $A < 0$, is it maxima?
