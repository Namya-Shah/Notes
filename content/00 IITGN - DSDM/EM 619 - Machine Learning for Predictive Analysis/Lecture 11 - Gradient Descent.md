---
Lecture Date: 2025-03-07
Presentation: 
Links: 
Subject:
  - "[[EM 619 - Machine Learning for Predictive Analysis]]"
References: 
tags:
  - EM619
---
```table-of-contents
```
# Gradient Descent
## Introduction
- Gradient Descent is an optimization algorithm
- It is used to find the minimum of a function in unconstrained settings
- It is an iterative algorithm
- It is a first order optimization algorithm
- It is a local search algorithm/greedy
## Usage
1. Initialize $\theta$ to some random value
2. Compute the gradient of the cost function at $\theta, \nabla f(\theta)$
3. For iteration $i (i=1,2,...)$ or until convergence
	- $\theta_i \leftarrow \theta_{i-1} - \alpha \nabla f(\theta_{i-1})$
# Taylor Series
- Taylor's series is a way to approximate a function $f(x)$ around a point $x_0$ using a polynomial
- The polynomial is given by

$$
f(x) = f(x_0) + \frac{f'(x_0)}{1!}(x-x_0) + \frac{f''(x_0)}{2!}(x-x_0)^2 + ...
$$

- The vector form of the above equation is given by:
  ![[CleanShot 2025-03-07 at 12.45.07.png]]
	- where $\nabla^2f(x_0)$ is the Hessian matrix and $\nabla f(x_0)$ is the gradient vector
# Decision Trees
- *Optimal Binary Trees* are **NP-complete**
- Greedy algorithm doesn't always mean good decision tree.
- Greedy algorithm can have 