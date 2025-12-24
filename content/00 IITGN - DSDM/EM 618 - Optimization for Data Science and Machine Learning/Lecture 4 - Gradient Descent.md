---
Lecture Date: 2025-01-24
Presentation: "[[Lecture 4 Fundamentals of Unconstrained Optimization Jan 24 2025.pdf]]"
Links: 
Subject:
  - "[[EM 618 - Optimization for Data Science and Machine Learning]]"
References: 
tags:
  - Gradient-Descent
  - Newton-Method
  - EM618
---
```table-of-contents
```

# Gradient Descent
- We use $\nabla f(w)$ (the gradient) to find the direction of steepest **ascent**.
- We move **opposite** to that direction (steepest descent)
- It is applicable to **any kind of function**, not necessarily *convex* or *concave* function.
- To decide **number of iterations**, we check the function's error and then our error and determine the minima point where they are in a straight line. The number on the x-axis is the number of iterations.
## Update Rule (in vector form)

$$
w^{(k+1)} = w^{(k)} - \alpha \nabla f(w^{(k)})
$$

- $\nabla f(w^{(k)})$ -> Direction part, gradient with respect to $w$
- $\alpha$ -> magnitude for the next gradient
- $w^{(k+1)}$ -> sensitivity of objective function with respect to $b$.
- *Our objective function in machine learning is typically going to be **loss function**, which we want to minimize*.
- $\alpha$ should be slow enough not to miss the valley

 $$
x_{new} = x_{old} - \alpha \frac{\partial f}{\partial \theta}
$$

	- Here, $\alpha$ should be controlled
- $\alpha$ -> **knob** -> control of learning hyperparameter
- **Heuristic** can work but isn't *guaranteed* to work, but generally it works.
- **No line search method tells you if the curvature is global maxima/minima**.
	- Use **TEST FOR CONVEXITY** for finding maxima/minima.
![[CleanShot 2025-01-31 at 11.40.40@2x.png]]
**Interpretation**:
- We move in the direction $- \nabla f(w^{(k)})$, the steepest descent direction.
- $\alpha > 0$ is the step size (learning rate)
**Key Issue**:
- If $\alpha$ is **too large**, we might *overshoot*
- If $\alpha$ is **too small**, *convergence* is *very slow*
## Gradient Descent: Multivariate
### Geometric meaning of $\nabla f$:
- $\nabla f(w)$ points to the direction of steepest increase
- Its magnitude is how fast $f$ increases in that direction.
### Update formula

$$

w^{(k+1)} = w^{(k)} - \alpha \nabla f(w^{(k)})

$$

### Algorithmically
1. Compute gradient $g^{(k)} = \nabla f(w^{(k)})$.
2. Update: $w^{(k+1)} = w^{(k)} - \alpha \nabla g^{(k)}$
3. Repeat until **convergence** (*heuristic*).
## Choosing the Step Size $\alpha$
- If $\alpha$ is *too large*, the method may **overshoot** and even **diverge**
- If $\alpha$ is *too small*, convergence is ***guaranteed*** but can be **extremely slow**.
- Often we use
	- A fixed small $\alpha$
	- A decaying $\alpha$ schedule (in machine learning)
	- A **line search** method to choose $\alpha$ at each step
## Use of Gradient Descent
- Uses only the *first derivative* (gradient) to decide direction.
- If the function is very curved, convergence might be slow (zig-zag in narrow valleys).
## Newton's Idea
- Use the *second derivative* (Hessian) to get local quadratic approximation.
- Move more directly toward the minimizer of that local quadratic model.
- Newton suggested that rather than heuristically determining $\alpha$, to use curvatures to slow down or speed it up. (**Changing the $\alpha$ mathematically for curvature rather than heuristically**).
**Advantages**:
- Quadratic convergence near the optimum if Hessian is positive definite.
- Often fewer iterations than gradient descent.
**Drawback**:
- Forming/inverting the Hessian is expensive for large $d$.
- A "full" Newton step might be too large if far from optimum, so we often do a line search or trust region approach.
### Formula

$$

w^{(k+1)} = w^{(k)} - [\nabla^2 f(w^{(k)})]^{-1} \nabla f(w^{(k)})

$$

- We can consider $[\nabla^2 f(w^{(k)})]^{-1}$ <- $\alpha$.
- $[\nabla^2 f(w^{(k)})]^{-1}$ -> **Inverse of Hessian Matrix**
---
# Questions
- [x] How do we use line search method to find $\alpha$ for step?