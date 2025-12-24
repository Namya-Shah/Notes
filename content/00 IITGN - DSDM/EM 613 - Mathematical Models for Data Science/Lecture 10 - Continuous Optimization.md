---
Lecture Date: 2024-06-29
Presentation: 
Links: 
Subject: 
tags:
  - EM613
---
```table-of-contents
```
# Introduction
- Optimization primarily means the object is to reduce the cost to company.
- When we drive a car, we look for optimal velocity, fuel efficiency, fastest route possible.
- We keep on getting dataset and then we use that dataset in our optimization models, which is in **live** mode.
- We have a continuous function and we keep on optimizing it to get the desired results.
## Purpose
Basic numerical methods for training machine learning models.
### Main branches of continuous optimization
1. Unconstrained optimization
	- It means no restriction
2. Constrained optimization
	- It means there is some type of restriction
3. **Special class:** Convex optimization
### Assumptions
1. Objective function is differentiable
	- Minimizing losses...
2. Aim: Minimize objective function-best value is minimum value (convention).
# Limits, continuity and differentiability
### Some questions to think about
1. Is the expression, $\frac {x-1} {x-1} = 1$ an identity? If no, then why $\lim_{x\rightarrow 1} \frac {x-1} {x-1} = 1$?
	- the expression is not identity as, for the value of $x = 1$, it is not defined
	- in the second part, we are putting limit on $x$, so we are not exactly at $1$. we are approaching $1$.
2. What is a continuous function? Recall the mathematical definition.
	- continuity at all points in the domain of the function.
	- if the function is true for all the points in the domain of the function, then its a continuous function.
3. What is a differentiable function? How do you represent it mathematically?
	- When the slope of two these two tangents are same, then the function is differentiable.
4. Are all continuous function differentiable? Are all differentiable functions continuous?
	- No, not all continuous functions are not differentiable but all differentiable functions are continuous.
5. What is an objective function? What is a constraint?
	- In terms of optimization, the function that you want to optimize is called the objective function. The function that enables you to find your objective of optimization.
	- It is the mathematical representation of the goal you are trying to achieve.
	- Constraints are limitations in terms of mathematical equations.
6. Are maxima/minima for discontinuous functions defined? If so, how?
	- It is defined. If in the neighbourhood of $A$, the values are lower than $A$, then it's a maxima otherwise it's a minima.
7. What is the curvature of a function? How is it found out?
	- There are two curvature:
		- 
# Stationary Points
## Definition
- Stationary points are the real roots of the (first) derivative.
- Points where gradient is zero.
### Example
To calculate the stationary points of a function: $l(x) = x^4+7x^3+5x^2 - 17x + 3$.
1. Determine the first derivative (gradient): $\frac {dl(x)} {dx} = 4x^3+21x^2+10x-17$.
2. Calculate stationary points

$$
4x^3+21x^2+10x-17 = 0 \implies x \in [-4.5,-1.4,0.7]
$$

# Extremum Points
## Definition
Stationary points that are either maxima or minima.
**Question:** Are all stationary points extremum points? Examples?
## Finding Minima
1. Calculate second derivative at all the stationary points.
2. Minima: second derivative is positive, Maxima: second derivative is negative.
### Previous example
Second derivative $\frac {d^2l(x)} {dx^2} = 12x^2+42x+10$. Thus, $x = -1.4$ is maxima ($\frac {d^2l(x)} {dx^2} < 0$).
# Global vs local minima
### Graphical Example
![[CleanShot 2024-06-29 at 23.14.36@2x.png]]
- **Arrows:** Negative gradients
- **Dashed line:** Global minima
# Optimisation using gradient descent
## Method
Solving for the minimum of a real-valued function $min_xf(x)$
- *The values obtained at real time are real values.*
- Assume $f$ is differentiable, and its solution in closed form cannot be found analytically.
	- *Assuming $f$ as differentiable, means considering $f$ to be differentiable at all points.*
	- *Finding the derivative and getting values is known as closed form of the function.*
- Gradient descent is a first-order optimization algorithm and can be relatively slow close to minimum.
	- *When we are close to the gradient, the value of gradient is very low because we are approaching zero.*
- The gradient points in the direction of the steepest ascent and that is orthogonal to the contour lines of the objective function.
	- *We go in the direction where the negative gradient of the function is negative.*
- Contour lines: Lines connecting same values. Isobars, isotherms etc. are examples of contour lines.
## Mathematical Framework
### Algorithm
- If for small step-size $\gamma \geq 0, f(x_1) \leq f(x_0)$ for

$$
x_1 = x_0 - \gamma((\nabla f)(x_0))^T
$$

- To find a local optimum $f(x_*)$ of a function $f$, initial guess, $x_0$ is chosen and then, iteration is performed according to

$$
x_{i+1} = x_i-\gamma_i((\nabla f)(x_i))^T
$$

- For suitable step-size $\gamma_i$, the sequence $f(x_0)\geq f(x_1) \geq ...$ converges to a local minimum.
> `surfc()` -> gives contour plot along with surface plot.
> `quiver`($x_1,x_2,x_3,x_4$)
> $x_1$-> base
> $x_2$-> value
> $x_3$-> magnitude at x-axis
> $x_4$-> magnitude at y-axis
## Numerical Example
Consider a quadratic equation in two dimensions

$$
f(\begin{bmatrix}
x1\\
x2
\end{bmatrix}) = [\frac {x_1} {x_2}]^T
\begin{bmatrix}
2 & 1\\
1 & 20
\end{bmatrix}
\begin{bmatrix}
x_1\\
x_2
\end{bmatrix} - \begin{bmatrix}
5\\
3
\end{bmatrix}^T
\begin{bmatrix}
x_1\\
x_2
\end{bmatrix}
$$

with gradient

$$
\nabla f (\begin{bmatrix}
x_1\\
x_2
\end{bmatrix}) = \begin{bmatrix}
x_1\\
x_2
\end{bmatrix}^T
\begin{bmatrix}
2 & 1 \\
1 & 20
\end{bmatrix} -
\begin{bmatrix}
5\\
3
\end{bmatrix}
$$

Starting from $x_0 = [-3,-1]^T$, we iterate to obtain a sequence of estimates that converge to the minimum value.
### Graphical Representation

--- start-multi-column: ID_qzy1
```column-settings
Number of Columns: 2
Largest Column: standard
```
![[CleanShot 2024-06-30 at 08.46.33@2x.png]]


--- column-break ---

The successive values of $x$ are:

$x_0 = [-3,-1]^T,$
$x_1 = [-1.98,1.21]^T,$
$x_2 = [-1.32,-0.42]^T ...$


--- end-multi-column
## Significance of step-size 1
Step-size, $\gamma$, is important because:
When the function value
- **increases** after a gradient step, $\gamma$ is too large. Undo the step and decrease $\gamma$.
- **decreases** the step could have been larger. Try increasing $\gamma$.
### Solving system of linear equations
Solution of $Ax=b$ is recast as solving $Ax-b = 0$. Objective is to find $x_*$ that minimizes the squared error

$$
||Ax-b||^2 = (Ax-b)^T(Ax-b)
$$

represented as Euclidean norm (analogous to distance). The gradient with respect to $x$ is

$$
\nabla_x = 2(Ax-b)^T A
$$

For numerical solution, use above expression in gradient descent. Otherwise, use analytical form.
## Speed of convergence
For solution of linear systems of equations, gradient descent may converge slowly.
## Condition number
Speed of gradient descent is dependent on the condition number, $\kappa = \frac {\sigma(A)_{max}} {\sigma(A)_{min}}$ where, $\sigma$ is singular value of $A$.
## Preconditioner
- Solve $P^{-1}(Ax-b) = 0$, where $P$ is the preconditioner.
- The goal is to design $P^{-1}$ so that it has better than $\kappa$ than $A$ and is easy to compete.
# Gradient descent with momentum
### Modifications
1. Introduces an additional term to remember what happened in the previous iteration. Dampens oscillations and smoothes out the gradient updates.
2. Remembers the update $\Delta x_i$ at each iteration $i$ and the next update is the linear combination of the current and previous gradients.
3. Averages out different noisy estimates of the gradient (moving average).

$$
x_{i+1} = x_i - \gamma_i((\nabla f)(x_i))^T + \alpha \Delta x_i
$$

$$
\Delta x_i = x_i - x_{i-1} = \alpha \Delta x_{i-1} - \gamma_{i-1}((\nabla f)(x_{i-1}))
$$

# Stochastic gradient descent
### Modifications
1. SGD introduces a stochastic (noisy) approximation of the gradient for minimizing an objective function.
2. Stochastic approximation is written as a sum of differentiable functions.
3. In machine learning, given $n = 1,...,N$ data points, often the objective functions are the sum of the losses $L_n$ incurred by each $n$, i.e.,

$$
L(\theta) = \sum^N_{n=1}L_n(\theta)
$$

where, $\theta$ is the parameters of interest that minimizes $L$.
# Relationship with standard gradient descent
### Details
- Standard gradient descent is a "batch" optimization method, i.e., optimization is performed using full training set by updating the vector of parameters as

$$
\theta_{i+1} = \theta_i - \gamma_i(\nabla L(\theta_i))^T = \theta_i - \gamma_i \sum^N_{i=1}(\nabla L_n(\theta_i))^T
$$

for a suitable $\gamma_i$. May lead to **expensive evaluation** of gradients.
- In the RHS term, take a sum over a smaller set of $L_n$, i.e., choose a subset of $L_n$ (mini-batch). **Extreme case:** batch size is one.
- **Justification:** RHS term is an empirical estimate of the expected value.
### Implications in machine learning
- When the learning rate (rate of convergence) decreases at an appropriate rate, and subject to relatively mild assumptions, SGD converges almost surely to local minimum.
- Approximate gradient eases practical implementation constraints. Usage of CPU/GPU, memory size, computational time etc.