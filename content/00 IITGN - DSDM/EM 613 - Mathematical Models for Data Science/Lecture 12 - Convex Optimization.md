---
Lecture Date: 2024-07-04
Presentation: "[[Convex Optimization.pdf]]"
Links:
  - "[[Convex Optimization]]"
  - "[[Linear Programming]]"
  - "[[Constrained Optimization]]"
  - "[[Lagrange & Dual Optimization]]"
Subject:
  - "[[EM 613 - Mathematical Models for Data Science]]"
tags:
  - EM613
---
```table-of-contents
```
# Convex Optimization
- **Advantage:** Global optimally is guaranteed.
### Convex optimization problem
1. $f(\cdot)$ is a convex objective function.
2. Constraints involving $g(\cdot)$ and $h(\cdot)$ are convex sets.
### Convex set
- A set $C$ is a convex set if for any $x,y \in C$ and for any scalar $\theta$ with $0 \leq \theta \leq 1$, we have $\theta x + (1-\theta)y \in C$.
- **Straight line connecting any two elements of the set lie inside the set.**
# Convex function
## Definition
- Let function $f:\mathbb R^D \rightarrow \mathbb R$ be a function whose domain is a convex set.
- $f$ is a convex function if for all $x, y$ in it domain, and for any scalar $\theta$ with $0 \leq \theta \leq 1$, we have

$$
f(\theta x \ + \ (1-\theta)y) \leq \theta f(x) \ + (1-\theta)f(y)
$$

### Relationships
- A concave function is the negative of a convex function.
- Imagine a convex function as a bowl-like object. Pour water to fill it up. Resulting set is convex set called **epigraph of the convex function.**
# Differentiable convex functions
### Relationship with gradient

--- start-multi-column: ID_yy6e
```column-settings
Number of Columns: 2
Largest Column: first
```

If function: $f: \mathbb R^n \rightarrow \mathbb R$ is differentiable then, it is convex if and only if
1. For any two points $x,y$

$$
f(y) \ge f(x) \ + \nabla_xf(x)^T(y-x)
$$

also known as **Jensen's inequality.**
2. $\nabla_x^2 f(x)$ is a positive semidefinite.
> $f$ must be twice differentiable in this case.




--- column-break ---

![[CleanShot 2024-07-07 at 21.40.36@2x.png]]


--- end-multi-column
# Determining convexity of function

--- start-multi-column: ID_a2wg
```column-settings
Number of Columns: 2
Largest Column: standard
```

The negative entropy $f(x) = xlog_2x$ is convex for $x > 0$.
- Illustrate definitions of convexity, using two points $x=2$ and $x=4$.
- To prove convexity of $f(x)$, all point $x$ must be tested.

--- column-break ---

![[CleanShot 2024-07-07 at 21.43.56@2x.png]]

--- end-multi-column
# Calculating convexity of function
### Using definition 1
- Consider $\theta = 0.5$ (midway between two points).
- Then, $\mathrm{LHS} = f(0.5 \cdot 2 + 0.5 \cdot 4) = 3 \log_23 \approx 4.75$
- $\mathrm {RHS} = 0.5(2\log_22) + 0.5(4\log_24) = 1 + 4 = 5$.
- Thus, $f(\theta x + (1-\theta)y) \le \theta f(x) + (1-\theta)f(y)$ is satisfied.
### Using definition 2
- $f(x)$ is differentiable, the derivative of $f(x)$ is $\nabla_x(x\log_2x) = \log_2x+\frac {1} {\ln 2}$.
- $\mathrm {LHS} = f(4) = 8$ & $\mathrm {RHS} = f(2) + \nabla f(2)\cdot(4-2) = 2 + (1 + \frac {1} {\ln 2})\cdot 2 \approx 6.9$.
- Thus, Jensen's inequality is satisfied.
# Constrained Optimization
### Generalization
Jensen's inequality is a whole class of inequalities for taking non-negative weighted sums of convex functions.
### Definition
A constrained optimization problem is called a convex optimization problem if
1. $\min_xf(x)$ is to be found.
2. Subjected to $g_i(x) \le 0 \ \forall i = 1,...,m$ and $h_j(x) = 0 \ \forall j = 1,...,n$.
> All functions $f(x)$ and $g_i(x)$ are convex, and all $h_j(x) = 0$ are convex sets.

# Linear Programming
### Special case of constrained optimization
All the functions are linear, i.e.,
1. Find $\min_{x \in R^d} c^Tx$
2. Subjected to $Ax \le b$
Here, $A \in \mathbb R^{m \ \text{x} \ d}$ & $b \in \mathbb R^m$. This is known as a **linear program** with $d$ linear program variables and $m$ linear constraints. Optimization problem $\implies$ Primal problem
### Lagrange and Lagrange multiplier

$$
\mathcal{L}(x,\lambda) = c^Tx + \lambda^T(Ax-b) = (c+A^T\lambda)^Tx - \lambda^Tb
$$

where, $\lambda$ is the vector of non-negative Lagrange multipliers.
# Primal vs. Dual Problem
### Dual Lagrangian
- Derivative of $\mathcal{L}(x,\lambda)$ with respect to $x$ and setting it to zero gives: $c + A^T\lambda = 0$.
- The dual Lagrangian is: $\mathcal{D}(\lambda) = -\lambda^Tb$.
### Dual optimization problem
1. Find $\max_{x \in \mathbb{R}^m} -b^T\lambda$
2. Subjected to $c + A^T\lambda = 0$
3. With $\lambda \ge 0$
This is also a **linear program**, but with $m$ variables.
# Linear Programming
### Linear Programming Demo
1. Find $\min_{x \in \mathbb R^2}- \begin{bmatrix} 5 & 3 \end{bmatrix}\begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$ (**Objective Function**)
2. Subjected to $\begin{bmatrix} 2 & 2 \\ 2 & -4 \\ -2 & 1 \\ 0 & -1 \\ 0 & 1 \end{bmatrix}\begin{bmatrix} x_1 \\ x_2 \end{bmatrix}\ge \begin{bmatrix}33\\ 8\\ 5\\ -1\\ 8\end{bmatrix}$ (**Constraints**)
### Graphical Solution

--- start-multi-column: ID_a18z
```column-settings
Number of Columns: 2
Largest Column: standard
```

#### Key observations
1. The objective function (contour) is linear.
2. Constraints are legends.
3. Optimal value is $\star$.
#### Points to ponder
1. What does the shaded area represent?
2. Why is $\star$ the minimum value?
3. Can the minima lie in the shaded region?

--- column-break ---

![[CleanShot 2024-07-07 at 22.15.02@2x.png]]


--- end-multi-column

