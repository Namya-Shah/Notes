$$
\nabla^2 f(x) = \begin{pmatrix} 
\frac{\partial^2 f}{\partial x_1^2} & \cdots & \frac{\partial^2f}{\partial x_1 x_d} \\
\vdots & \ddots & \vdots \\
\frac{\partial^2 f}{\partial x_d x_1} & \cdots & \frac{\partial^2 f}{\partial x_d^2}
\end{pmatrix}
$$

**Curvature Info**
- **Positive Definite** $\Rightarrow$ local minimum region ($\nabla^2 f > 0$)
- **Negative Definite** $\Rightarrow$ local maximum region ($\nabla^2 f < 0$)
- **Indefinite** $\Rightarrow$ likely a saddle region
**Visual**
- In 2D, positive definite Hessian $\Rightarrow$ "bowl shape"
- Negative definite Hessian $\Rightarrow$ "upside-down bowl"
- Mixed signs $\Rightarrow$ "saddle" shape
**Important Points**
- If **all** eigenvalues are positive, then it is a positive definite matrix.
- If **all** eigenvalues are negative, then it is a negative definite matrix.
	In *nonconvex* (like deep nets), Hessian can be indefinite $\Rightarrow$ multiple minima, saddle points as their parameters are non-linear.