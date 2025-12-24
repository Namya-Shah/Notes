---
Lecture Date: 2025-01-29
Presentation: "[[Lecture 5 Unconstrained Methods Jan 29 2025.pdf]]"
Links: 
Subject:
  - "[[EM 618 - Optimization for Data Science and Machine Learning]]"
References:
  - "[[Armijo Principle]]"
tags:
  - Line-Search
  - EM618
  - Gradient-Descent
  - Newton-Method
  - Least-Squares
  - Armijo-Criterion
  - Wolfe-Conditions
---
```table-of-contents
```
# Quick Notes
- Least Squares & RMSE -> $l_2$ norm
- Optimization is a hiking problem
- Local Search searches for local minima and isn't capable of finding global minima
- Gradient Descent with additional check -> Armijo
- Taking an inverse of a matrix is a computationally expensive problem
- Armijo only checks that the point is near to local minima
# Introduction
- Functions can be quadratic but not necessarily convex in $f$.
	- No. of steps becomes a critical factor in the learning
# Gradient Descent

$$
w^{(k+1)} = w^{(k)}-\alpha(2w^{(k)})
$$

- $\alpha$ -> heuristic in **gradient descent**
- Requires multiple steps to reach 0, depending on $\alpha$
- In optimization: **gradient-based** methods ***converge slowly*** if the function's curvature differs a lot across directions
# Newton's Method
## Original Formula

$$
w^{(k+1)} = w^k - \frac{\nabla f}{\nabla^2f}
$$

## Example

$$
w^{(k+1)} = w^{(k)} - \frac{2w^{(k)}}{2} = 0 \quad \text{for equation} \ f(w) = w^2
$$

- Solved in one step
> [!NOTE] NOTE
> Newton's Method first rule is $\nabla^2f \neq 0$. Even if determinant is zero, we cannot use **Newton's Method**.

## 2-D Example
### Formula

$$
f(w_1, w_2) = w_1^2 +2w_2^2
$$

**SOLUTION**

$$
\nabla f = \begin{pmatrix}
2w_1 \\
4w_2
\end{pmatrix},
\nabla^2f = \begin{pmatrix}
2 & 0 \\
0 & 4
\end{pmatrix}
$$

### Newton's Method

$$
w^{(k+1)} = w^{(k)} - \begin{pmatrix}
2 & 0 \\
0 & 4
\end{pmatrix}^{-1}
\begin{pmatrix}
2w_1^{(k)} \\
4w_2^{(k)}
\end{pmatrix} = 0
$$

- One step at $(0,0)$
- **Gradient Descent**: would take many steps if $\alpha$ is small (though stable)
# Least Squares: A Perfect Quadratic Case
**Objective**:

$$
f(w) = ||Xw - y||^2 = (w^TX^T - y^T)(Xw-y)
$$

- The above norm is **L2 Norm**
**Gradient**:

$$
\nabla f(w) = 2X^T(Xw-y) = 2(X^TXw - X^Ty)
$$

**Hessian**:

$$
\nabla^2f(w) = 2X^TX \quad \text{(constant in w)}
$$

## Newton's Update

$$
w^{(k+1)} = w^{(k)} - (2X^TX)^{-1} \nabla f(w^{(k)})
$$

Since $\nabla f(w) = 2(X^TXw - X^Ty)$,

$$
w^{(k+1)} = w^{(k)} - (2X^TX)^{-1} \cdot 2(X^TXw^{(k)}-X^Ty) = w^{(k)} -(X^TX)^{-1}(X^TXw^{(k)}-X^Ty) = (X^TX)^{-1}X^Ty
$$

- Value of slope
- Seen in time series, minimization and newton method
# Logistic Regression
## Convex but Not Quadratic
**Objective**:

$$
\min_w \sum^n_{i=1}[-y_i \ln(\sigma(w^Tx_i)) - (1-y_i) \ln(1-\sigma(w^Tx_i))],
$$

with $\sigma(z) = \frac{1}{(1+e^{-z})}$.
**Notes**:
- The Hessian is *not* constant, so we can't solve in one step.
- Hessian is function of $w$.
- $\nabla^2f$ is typically well-defined but must be updated each iteration.
- Newton's method converges faster than simple gradient descent, but more expensive per iteration.
- Taking inverse becomes costly because it is non-quadratic function
# Line Search or Damping
**Newton's Method**:

$$
w^{(k+1)} = w^{(k)} - [\nabla^2f(w^{(k)})]^{-1} \nabla f(w^{(k)})
$$

In practice,

$$
w^{(k+1)} = w^{(k)} - \alpha_k[\nabla^2f(w^{(k)})]^{-1} \nabla f(w^{(k)})
$$

where $0 < \alpha_k \leq 1$.
- $\alpha_k$ becomes the check/hyperparameter.
- $\alpha_k$ -> adaptive learning rate
- $\alpha_k$ determines when to slow down
- If $[\nabla^2f(w^{(k)})]^{-1}$ is a multi-step solution, then we use $\alpha_k$ for slowing it down.
- **Equivalent to $\alpha$ of gradient descent brake: descending from hill**.
**Why?**
- If $w^{(k)}$ is **far** from optimum, the pure Newton step might overshoot.
- We adapt $\alpha_k$ via *backtracking line search* (Armijo rule) or *trust-region* methods.
# Comparing Gradient Descent and Newton's Method
- **Gradient Descent**
	- Low per-iteration cost (only need **gradient**).
	- Potentially *many* steps if the problem is ill-conditioned.
	- Heavily used in high-dimensional ML (especially with mini-batches).
- **Newton's Method**
	- Faster (often quadratic) convergence near optimum.
	- High per-iteration cost: must handle **Hessian**.
	- Often used for moderate dimensions or specialized problems (e.g., some iterative solvers or quasi-Newton approximations).
	- If we have problem as [[Linear Regression]], guarantees that we reach *optimum* in **one step**
> [!IMPORTANT] IMPORTANT
> **If we move too fast, we might start jumping from one point to another**
> **If we move too slow, it might take more computing power along with more time**

> [!NOTE]
> **In Logistic Regression, we will typically use [[Quasi-Newton Method]]**
> *When we are not given anything, we will generally start from [[Gradient Descent]]*
- Newton's Method is mathematically more superior over Gradient Descent.
![[CleanShot 2025-02-03 at 01.10.20@2x.png]]
- **Red arrows** shows use of Gradient Descent to reach the "X" point.
- For rough tracks, we need to slow down rather than acceleration for which $f'(x) + f''(x)$ is going to guide us when to slow down.
# Line Search
- Line Search provides algorithmic rule for picking $\alpha_k$.
- Avoids trial-and-error with a fixed or decaying schedule.
## The "Hiker on a Mountain" Analogy
- **Imagine a hiker** who wants to climb **down** a mountain to reach the valley floor:
	- The *direction* of steepest descent is "downhill"
	- But how *far* should they step in that direction?
- **Two extremes**:
	- Take a *huge* step: might jump off a cliff or end up climbing the next mountain (overshoot).
	- Take a *tiny* step: definitely go downhill, but might take forever to reach the bottom.
- **Line Search**: systematically tries step sizes so the hiker finds a "just right" stride each time.
## Why Not Always Take a "Full Step"?
**In math terms**: A full step might be $\alpha = 1$ if we use $-\nabla f$ as the direction. But if the *valley* is *curved*, we can overshoot:
- Instead of ending up in a lower spot, we might land in a higher region on the other side of the valley.
Hence a line search checks:
- "Is the new spot actually *lower* than the old spot, by a decent amount?"
- If *no*, we shorten the step until we're sure of making good progress downward.
## Armijo's "Good Enough" Criterion
**Armijo says**: "I don't need the **full** linear decrease --- just a fraction c."

$$
f(x+\alpha d) \leq f(x) + c \ \alpha \ f'(x) \ d, (0 < c< 1)
$$

In plain language:
- If the actual value at $x + \alpha d$ isn't low enough compared to that fraction of linear approximation, we try a smaller $\alpha$.
## Why Shrinking $\alpha$ Isn't Always Slow
- Yes, we might do multiple "tests" (halving $\alpha$, for instance).
	- This avoids overshoot, which can be *disastrous*.
	- Over many iterations, stable steps typically led to **fewer total corrections**.
- **Net effect**: It can be *faster overall* because we avoid big mistakes.
## Illustrative Example
![[CleanShot 2025-02-03 at 01.32.58@2x.png]]
## Summary of Line Search Motivation
- We have a direction that's "downhill" but we're unsure how far to step.
- By systematically testing step sizes, we avoid:
	- *Overshooting* (jumping into a higher place)
	- *Undershooting* (tiny steps that barely move)
- *Armijo* or *Wolfe* line search ensures each step is in a "just-right" zone:
	- Enough decrease in $f$.
	- Not so small that progress is negligible.
# Armijo Criterion
**Armijo (Sufficient Decrease) Condition**:

$$
f(x+\alpha d) \leq f(x) + c \alpha \nabla f(x)^T d, \quad 0 < c < 1
$$

**Basic Idea**:
- We want the **actual decrease** in $f$ to be at least a fraction $c$ of the **linear** (first-order) decrease predicted by $\nabla f (x)^Td$.
- If not, we reduce $\alpha$ and try again.
## 1D Summary
- Armijo systematically tries $\alpha_0 = 1$, then shrinks $\alpha$ by factor $\beta$ if the function decrease is insufficient.
- Freed us from guessing a single step size manually.
- In many cases, ensure stable progress each iteration.
## Armijo in Higher Dimensions
- The logic is the same: if the function at $x + \alpha d$ isn't at least a fraction $c$ better than a linear model, shrink $\alpha$.
- Prevents big overshoot.
- Simple, robust approach but can be "conservative" (sometimes smaller steps than necessary).
# Wolfe Conditions
**Two Conditions**:
1. **Sufficient Decrease**: same as Armijo

$$
	f(x+\alpha d) \leq f(x) + c_1 \alpha \nabla f(x)^Td
	$$
2. **Curvature Condition**:
$$

\nabla f(x + \alpha d)^Td \ge c_2 \nabla f(x)^T d

$$
Parameters: $0 < c_1 < c_2 < 1$

---
# Questions
- [ ] How do we determine the value of $\beta$.