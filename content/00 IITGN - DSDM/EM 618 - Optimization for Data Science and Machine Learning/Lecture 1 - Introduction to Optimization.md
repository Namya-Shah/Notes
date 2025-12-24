---
Lecture Date: 2025-01-15
Presentation: "[[Lecture 1 Introduction to Optimization Jan 15 2025.pdf]]"
Links: 
Subject:
  - "[[EM 618 - Optimization for Data Science and Machine Learning]]"
References:
  - "[[Ant Colony Optimization]]"
  - "[[Taylor Series]]"
  - "[[Unconstrained Optimization]]"
  - "[[Hessian Matrix]]"
tags:
  - EM618
---
```table-of-contents
```

***Important Points***
- All saddle points are stationary but the inverse is not true
---
# Why Optimization for Data Science?

- Many data science and machine learning models boils down to parameter estimation that minimizes (or maximizes) an objective function (loss function, accuracy, etc.)

## Unconstrained Optimization

$$
\min_{x \in \mathbb R^d} f(x)
$$

## Constrained Optimization

$$
\min_{x \in \mathcal{X}} f(x) \quad \text{subject to constraints on } x.
$$

# Linear Regression
## Ordinary Least Squares

$$
\min_w \sum^n_{i=1}(y_i - w^Tx_i)^2
$$

$w$ → parameter

# Logistic Regression

## Binary Classification

$$
\min_w \sum^n_{i=1} [-y_i\ln(\sigma(w^Tx_i))-(1-y_i)\ln(1-\sigma(w^Tx_i))]
$$

where $\sigma(z) = \frac{1}{1+e^{-z}}$ is the sigmoid function.

- Also convex in $w$, but no closed-form solution.
- Typically solved iteratively (gradient descent, Newton’s method, etc.).

# Heuristic / Metaheuristic Approaches
- Combines cognitive intelligence with social intelligence as seen in birds when they fly in groups.
- Genetic Algorithms, Particle Swarm Optimization, Differential Evolution
- Particularly useful when:
    - The objective function is non-differentiable or [black-box](https://www.wikiwand.com/en/articles/Black_box)
    - We aim for a global search over highly nonconvex landscapes
    - Gradient information is costly or impossible to obtain
- Often used in hyperparameter tuning, feature selection, and other discrete or complex optimization tasks within data science.

# Local vs. Global Minima (Unconstrained)

- **Local Minima:** A point $x^*$ is a local min if there exists a neighborhood around $x^*$ such that

$$
f(x^*) \le f(x) \quad \text{for all} \ x \ \text{in that neighborhood}
$$

- **Global Minima:** A point $x^*$ is a global min if

$$
f(x^*) \le f(x) \quad \text{for all} \ x \ \text{in the entire domain}
$$

- *We can convert maximization problem into minimization problem by adding a "-" sign before the equation and vice versa*
- In data science, we often settle for local minima when $f$ is nonconvex (like neural nets).
- If $f$ is convex, local minima coincide with the global minimum simplifying the search.
# Stationary Points and Gradients (Unconstrained)
- A stationary point $x^*$ is one where

$$
    \nabla f(x^*) = 0
    $$

- For a **local minimum**, we often want $\nabla^2 f(x^*)$ (the Hessian) to be positive semidefinite.
- If $f$ is nonconvex, stationary points might be local maxima or saddle points, so checking the Hessian can help classify them.
**Relevance**
- Many data science losses are smooth enough to have a gradient.
- If the function is convex, any stationary point is also a global min.
# Saddle Point
- A saddle point is a specific type of stationary point that is **not a local minimum or maximum**. At a saddle point, the function has a flat tangent plane (the derivative is zero), but the function curves in different directions. This means that in some directions, it behaves like a local maximum, while in others, it behaves like a local minimum.
## Key Differences

| **Feature**    | **Stationary Point**                                   | **Saddle Point**                                                  |
| -------------- | ------------------------------------------------------ | ----------------------------------------------------------------- |
| **Definition** | Point where the first derivative is zero               | A stationary point that is neither a local minimum nor maximum    |
| **Curvature**  | Could be concave up, concave down or flat              | Curvature changes direction; up in one direction, down in another |
| **Example**    | f(x)=x^2 at x=0 (local minimum)                        | f(x,y) = x^2-y^2 at (0,0) (saddle point)                          |
| **Nature**     | Can be a local minimum, local maximum, or saddle point | Specifically indicates a mixed behavior, not extremum             |

---
# Quiz
- What does the gradient of a function represent?
	- The gradient of a function $\nabla f(x)$ represents the vector of partial derivatives of $f(x)$, pointing in the direction of the steepest ascent.
- Explain the role of Hessians in optimization.
	- Hessians capture second-order curvature information of a function, which helps determine the nature of stationary points (e.g., minimum, maximum, or saddle point). They are also used in Newton's method for quadratic approximations.
- For the function $f(x_1, x_2) = x_1^2 + 2x_1x_2 + 3x_2^2$, calculate the gradient and Hessian matrix.
	- Gradient
	$$\nabla f(x_1,x_2) = \begin{bmatrix}
                2_x1 + 2x_2 \\
                2_x1 + 6x_2
            \end{bmatrix}
		$$
	- Hessian
	$$
	\nabla^2 f(x_1,x_2) = \begin{bmatrix}
                2 & 2 \\
                2 & 6
            \end{bmatrix}
	$$
- What does it mean if the Hessian of a function is positive definite?
	- If the Hessian of a function is positive definite, it implies that the function is locally convex, and the stationary point is a local minimum.
- Compute the $L_1$-norm and $L_2$-norm of the vector $x = (3,4)$.
	- $L_1$-norm $= |3| + |4| = 7$
	- $L_2$-norm $= \sqrt{3^2 + 4^2} = \sqrt{9 + 16} = \sqrt{25} = 5$ 
- What is optimization in the context of data science?
	- Optimization is the process of making a system as effective or functional as possible.
- Common methods used in optimization
	- Gradient Descent
	- Linear Programming
	- Genetic Algorithms
- Goal of Optimization
	- Minimize the loss function to improve model accuracy.
- Significance of parameter estimation in machine learning
	- Minimizing or maximizing an objective function, impacting model performance.
- What heurestic methods can be incorporated when gradient information is unavailable?
	- Evolutionary algorithms
- How can you distinguish between convex and nonconvex problems?
	- By analyzing the shape of the function and its critical points.
- What does $f(x)$ represent in optimization problems in data science?
	- A loss function or error metric that needs to be minimized
- What is the objective of **Ordinary Least Squares** in linear regression?
	- To minimize the sum of the squared differences between observed and predicted values.
- Why is linear regression considered a fundamental building block for supervised learning?
	- It provides a simple and interpretable model for predicting outcomes based on input features.
- What does 'w' represent in the context of linear regression?
	- The parameters of the linear model
- What is the objective function for binary classification in logistic regression?
	- The objective function is: $\min_w \sum (-y_i ln(\sigma(w^T x_i)) - (1-y_i)ln(1-\sigma(w^T x_i)))$
- What is the sigmoid function used in logistic regression?
	- The sigmoid function is defined as $\sigma(z) = \frac{1}{(1+e^{(-z)})}$ 
- Is the logistic regression object function convex?
	- Yes, the objective function in logistic regression is convex in w
- Why is there no closed-form solution for logistic regression?
	- The optimization problem is non-linear due to the sigmoid function
- What are evolutionary algorithms commonly used for in data science?
	- They are often used in parameter tuning, feature selection, and complex optimization tasks.
- What types of problems are evolutionary algorithms particularly useful for?
	- They are useful for non-differentiable objective functions and global searches over nonconvex landscapes.
- Name three types of evolutionary algorithms mentioned
	- Genetic Algorithms
	- Particle Swarm Optimization
	- Differential Evolution
- Why might gradient information be costly or impossible to obtain in certain optimization tasks?
	- In some complex or black-box functions, the gradient may not be available or may require significant computational resources to calculate.
- What is characteristic of the landscapes where evolutionary algorithms are applied?
	- They often involve highly in nonconvex landscapes
- Why do data scientists often settle for local minima?
	- Data scientists often settle for local minima because many functions, like those in neural networks, are nonconvex.
- What is a stationary point in the context of optimization?
	- A stationary point $x^*$ is where the gradient of the function, $\nabla f(x^*)$, equals zero.
- What role does the Hessian matrix play in classifying stationary points?
	- The Hessian matrix helps determine if a stationary point is a local minimum, local maximum, or saddle point based on its definiteness.
- What is the relationship between convex functions and stationary points?
	- For convex functions, any stationary point is also a global minimum.
- What is constrained optimization?
	- Constrained optimization is the process of minimizing or maximizing a function subject to constraints on the variables.
- Why can't we simply set the derivative of the function to zero in constrained optimization?
	- Because the feasible region may restrict the possible values of x, making some solutions invalid.
- What are Lagrange multipliers used for in constrained optimization?
	- Lagrange multipliers are used to find the local maxima and minima of a function subject to equality constraints.

---

# Questions

1. **Given that it is stationary point, what is sufficient condition?. Why?**

$$

    \frac{\nabla^2 f}{\nabla x^2} > 0 : minima
    $$

$$
f(x+h) = f(x) + \frac{h}{1!} f'(x) + \frac{h^2}{2!} f''(x)
	$$
$\frac{h}{1!} f'(x)$ = 0 for it to be stationary. We remove it.
$$

f(x+h) = f(x) + \frac{h^2}{2!} f''(x)

$$
$$

f(x+h) - f(x) = \frac{h^2}{2!} f''(x)

$$
- If $f(x+h) - f(x) < 0$ then it is **maxima**
- If $f(x+h) - f(x) > 0$ then it is **minima**
