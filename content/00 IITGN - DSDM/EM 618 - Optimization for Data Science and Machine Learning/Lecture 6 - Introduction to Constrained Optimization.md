---
Lecture Date: 2025-01-31
Presentation: "[[Lecture 5 Unconstrained Methods Jan 29 2025.pdf]]"
Links: 
Subject:
  - "[[EM 618 - Optimization for Data Science and Machine Learning]]"
References:
  - "[[Armijo Principle]]"
tags:
  - EM618
  - Wolfe-Conditions
  - Quasi-Newton
  - Secant-Condition
---
> [!NOTE] NOTE
> How many times we want to update weights will depend on convergence criteria.
> Stabilization is the difference of errors which becomes smaller so we can say our algorithm is **stabilized**.

> [!IMPORTANT] IMPORTANT
> We use Armijo principle as it helps us to slow down further so that we won't jump off from the function and lose local maxima/minima.

# Wolfe Conditions
## *Equations*
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
## *Why Curvature Conditions*
- Armijo alone might pick a step that's too small.
- The *curvature condition ensures we don't undershoot too severely* - i.e., we want the slope at the new point $\nabla f(x + \alpha d)^T d$ not to be too negative.
- If it's still negative, we suspect we could step further.
**Result**: Wolfe line searches can **yield bigger $\alpha$ in practice**, improving efficiency.
> [!IMPORTANT] IMPORTANT
> Armijo & Wolfe checks on $\alpha$. Armijo checks on $\nabla f(x)$ while Wolfe checks on $\nabla^2f(x)$
## *Wolfe in Practice*
- More complex to implement than pure backtracking Armijo (since we also check slope at the trial point).
- Often used with **Conjugate Gradient** or **Quasi-Newton** methods to maintain nice theoretical properties (like positive definiteness in approximate Hessians).
- Typically yields fewer "backtracks" if done carefully.
# Quasi-Newton
- **Gradient Descent**: Simple, but can be slow (linear convergence).
- **Newton's Method**: Potentially very fast (quadratic convergence) but expensive (need $\nabla^2f$ each iteration, plus inversion or factorization).
## ***Why do we use Quasi-Newton?***
- *Approximate* the Hessian (or its inverse) using **only** gradient information (no need to compute $\nabla^2f$). 
- Achieve **faster convergence** than gradient descent, at a fraction of the cost of full Newton.
- Typically rely on **line search** (Armijo or Wolfe) to ensure stability and good updates.
> [!NOTE] NOTE
> We give up **accuracy** for reaching *gradient* ($\nabla f$) = 0
# Secant Condition
$$

f'(x + \Delta x) - f'(x) \approx f''(x) \Delta x

$$
- In multiple dimensions, the Hessian $\nabla^2 f$ generalizes $f''(x)$.
Hence for a vector step $\Delta s_k$.
$$

\nabla f(x^{(k+1)}) - \nabla f(x^{(k)}) \approx \nabla^2f(x^{(k)}) \Delta s_k

$$
If we let $B_k \approx \nabla^2f(x^{(k)})$, the condition becomes:
$$

\Delta y_k = \nabla f(x^{(k+1)}) - \nabla f(x^{(k)}) \approx B_k \Delta s_k

$$
**Interpretation**:
- For an exact **Hessian**, that equality would hold precisely (neglecting higher-order terms).
- Quasi-Newton updates $B_{k+1}$ so that it *better satisfies* $\Delta y_k \approx B_{k+1} \Delta s_k$ after each step.
## BFGS: The Classic Quasi-Newton Update
### Notation
$B_k \approx \nabla^2f(x^{(k)})$, $\Delta s_k = x^{(k+1)} - x^{(k)}$, $\Delta y_k = \nabla f(x^{(k + 1)}) - \nabla f(x^{(k)})$
### BFGS Formula (Hessian Form)
$$

B_{k+1} = B_k - \frac{B_k \Delta s_k (\Delta s_k)^T B_k}{\Delta s_k^T B_k \Delta s_k} + \frac{\Delta y_k (\Delta y_k)^T}{\Delta y_k^T \Delta s_k}

$$
**Why this works:**
- First (negative) term *removes* old curvature info along $\Delta s_k$.
- Second (positive) term *adds* new curvature info gleaned from $\Delta y_k$.
- Over iterations, $B_{k+1}$ "learns" the local Hessian in the directions we actually move.
#### Why we often start with $B_0 = I$ (the identity)
- If we have **no prior knowledge** about the Hessian shape, a neutral default is the identity matrix $I$.
- This basically says "assume unit curvature in all directions" until we gather real gradient-based evidence otherwise.
- If we suspect the Hessian is scaled, we might choose $B_0 = \alpha I$ for some scalar $\alpha > 0$.
In practice, $B_0 = I$ is extremely common. The BFGS updates quickly shape $B_k$ into a more accurate approximation as soon as we see gradient changes $\Delta y_k$ over successive steps.
> [!NOTE] NOTE
> We don't necessarily need to take $I$ (Identity). We can assume any arbitrarily number.

> [!IMPORTANT] IMPORTANT
> `Scikit-Learn` by default uses L-BFGS algorithm as optimization solver.

## Quasi-Newton Algorithmic Flow
![[CleanShot 2025-02-03 at 17.59.28@2x.png]]
> [!IMPORTANT] IMPORTANT
> It helps **Hessian** to *update much faster*.
## Summary
- **BFGS**, **L-BFGS**: The most common quasi-Newton algorithms.
- **Initialization**: Often $B_0 = I$ (identity). If known scaling is useful, we choose $B_0 = \gamma I$.
- **Line Search**: Helps ensure $\Delta s_k^T \Delta y_k > 0$, which keeps $B_{k+1}$ positive definite.
- **Performance**: Typically *superlinear* convergence once near optimum, bridging speed between plain gradient descent and full Newton.
- **Memory Issues for Large $d$**: L-BFGS uses a limited memory approach so we never store a full $d \times d$ matrix
- **No Free Lunch**: It will have memory issues of its own.
# When to use or not use Line Search
- **Medium-scale** problems: line search is often beneficial. E.g., logistic regression with thousands or tens of thousands of parameters.
- **Very large-scale or deep neural nets**: each function/gradient evaluation can be huge. People often prefer simpler *learning rate schedules* or *adaptive methods* (Adam, RMSProp).
- **Non-smooth problems**: subgradient or proximal methods might be needed, not the standard line search.
# Python Code for GD and Armijo GD
```python
import numpy as np
import matplotlib.pyplot as plt

def f(x):
    return x**2 + 2*x + 1

def grad_f(x):
    return 2*x + 2

def gradient_descent(initial_x, learning_rate, max_iters):
    x = initial_x
    trajectory = [x]
    for _ in range(max_iters):
        x = x - learning_rate * grad_f(x)
        trajectory.append(x)
    return np.array(trajectory)

def armijo_gradient_descent(initial_x, max_iters, beta=0.5, sigma=0.1):
    x = initial_x
    trajectory = [x]
    for _ in range(max_iters):
        t = 1  # Initial step size
        while f(x - t * grad_f(x)) > f(x) - sigma * t * grad_f(x)**2:
            t *= beta  # Reduce step size
        x = x - t * grad_f(x)
        trajectory.append(x)
    return np.array(trajectory)

# Parameters
initial_x = 4.0
learning_rate = 0.4  # This makes the normal gradient descent jump around
max_iters = 10

# Compute paths
normal_gd = gradient_descent(initial_x, learning_rate, max_iters)
armijo_gd = armijo_gradient_descent(initial_x, max_iters)

# Plot function
x_vals = np.linspace(-5, 5, 100)
y_vals = f(x_vals)
plt.plot(x_vals, y_vals, label='Function f(x)')

# Plot paths
plt.plot(normal_gd, f(normal_gd), 'ro-', label='Gradient Descent')
plt.plot(armijo_gd, f(armijo_gd), 'bo-', label='Armijo Gradient Descent')

# Labels and Legend
plt.xlabel('x')
plt.ylabel('f(x)')
plt.title('Gradient Descent vs Armijo Rule')
plt.legend()
plt.grid()
plt.show()
```

## Output
![[CleanShot 2025-02-03 at 11.36.50@2x.png]]
# Constrained Optimization
- We want to maximize something but there will be resource constraints.
- In constrained optimization, we need additional theories (e.g., [[Lagrange Multiplier]] & [[Kuhn Tucker Condition]])
- 