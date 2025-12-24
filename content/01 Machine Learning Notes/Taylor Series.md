Taylor series approximates a complicated function using a series of simpler polynomial functions that are often easier to evaluate. The key idea is to use a series of increasing powers to express complicated yet well-behaved (infinitely differentiable and continuous) functions.

- For univariate functions, the first-order polynomial approximates $f$ at point $P$ as a straight line tangent to $f$ at point $P$. The second-order polynomial approximates $f$ as a quadratic equation whose line passes through point $P$. Increasing powers of polynomials result in better approximations to complicated functions.
![[CleanShot 2025-01-17 at 08.48.59@2x.png]]
# Real-World Example: Optimizing Neural Networks

Taylor expansion helps in minimizing loss function (e.g., mean squared error, cross-entropy) by adjusting the network’s weights.
## Objective
Minimize the loss function $L(w)$, where $w$ represents the weights of the neural network.
## Taylor Expansion

$$
f(x+h) = f(x) + \frac{h}{1!}f'(x)+\frac{h^2}{2!}f''(x) + \cdots +\frac{h^n}{n!}f^n(x)
$$