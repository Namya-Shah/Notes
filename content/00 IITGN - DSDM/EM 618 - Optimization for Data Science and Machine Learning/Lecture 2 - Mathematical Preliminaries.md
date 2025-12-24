---
Lecture Date: 2025-01-23
Presentation: "[[Lecture 2 Mathematical Preliminaries Jan 17 2025.pdf]]"
Links: 
Subject:
  - "[[EM 618 - Optimization for Data Science and Machine Learning]]"
References: 
tags:
  - EM618
  - Vectors
  - Dot-Product
  - L1-Norm
  - L2-Norm
  - Linf-Norm
  - Ln-Norm
---
```table-of-contents
```
# Vectors
- Objective functions are user-defined
# Dot Product

$$

x^Ty = \sum^d_{i=1}x_iy_i

$$

**Interpretation**
- If vectors are aligned, dot product is large positive.
- If perpendicular, dot product is zero.
- If opposite directions, negative.

# L1 & L2 Norms
## $l_1$ - Norm

$$

||x||_1 = \sum^d_{i=1}|x_i|

$$

**Meaning**: sum of absolute values
## $l_2$ - Norm

$$

||x||_2 = \sqrt{x_1^2 + x_2^2 + ... + x_d^2}

$$

**Meaning**: ordinary distance from origin
## $l_n$ - Norm

$$

||x||_n = \begin{pmatrix}
\sum^d_{i=1} |x_i|^n
\end{pmatrix}^\frac{1}{n}

$$

## $l_\infty$ - Norm

$$

||x||_\infty = \max_i |x_i|

$$

---
# Quiz
- **How does overfitting relate optimization in data science?**
	- Overfitting occurs when a model is too complex and captures noise instead of the underlying pattern, often due to excessive optimization on training data.
- **What are the key characteristics of the graph of a quadratic function?**
	- The graph of a quadratic function is a parabola that opens upwards or downwards, depending on the sign of the coefficient 'a'.
- **How can quadratic functions be used in optimization problems?**
	- Quadratic functions can be used in optimization problems to find maximum or minimum values, which is essential for resource allocation and decision-making.
- **What is a Taylor expansion?**
	- A Taylor expansion is a mathematical representation of a function as an infinite sum of terms calculated from the values of its derivatives at a single point.
- **How is a Taylor expansion useful in optimization?**
	- A Taylor expansion can simplify the optimization of functions by approximating them locally around a point, allowing for easier calculations of minima or maxima.
> [!important]
> Covered till Quadratic Equations
