---
Link: 
tags:
  - KKT
  - ML
---
# Notes
- The **Karush-Kuhn-Tucker (KKT)** conditions are fundamental in solving constrained optimization problems. They extend Lagrange multipliers to handle both equality and inequality constraints.
## Conditions
For a point $x^*$ to be optimal, it must satisfy:
1. Stationarity

	$$
	\nabla f(x^*) + \sum^p_{i=1} \lambda_i \nabla h_i(x^*) + \sum^m_{j=1} \mu_j \nabla g_j(x^*)
	$$

2. Primal Feasibility

	$$
	h_i(x^*) = 0, g_j(x^*) \le 0 \ \forall i,j
	$$

3. Dual Feasibility

	$$
	\mu_j \ge 0 \ \forall j
	$$

4. Complementary Slackness

	$$
	\mu_j g_j (x^*) = 0 \ \forall j
	$$

## Example

$$
f(x,y) = x^2 + y^2
$$

**Constraint**: $x + y \ge 1$
**Lagrangian**: $\mathcal{L} = x^2 + y^2 + \mu(1-x-y)$
**Applying KKT**
1. Stationarity

	$$
	\frac{\partial \mathcal{L}}{\partial x} = 2x - \mu = 0 \implies x = \frac{\mu}{2}
	$$

	$$
	\frac{\partial \mathcal{L}}{\partial y} = 2y - \mu = 0 \implies y = \frac{\mu}{2}
	$$

	Thus, $x=y$
2. Primal Feasibility

	$$
	1 - x - y \le 0 \implies x + y \ge 1
	$$

3. Complementary Slackness
	If $\mu > 0$, then $1 - x - y = 0 \implies x + y = 1$.
4. Solve
	From $x=y$ and $x+y=1$, we get $x=y=0.5$, $\mu = 1$.
***Visualization***: The optimal point $(0.5,0.5)$ lies where the circle $x^2 + y^2$ touches the line $x+y=1$.
## Key Notes
- **Active vs. Inactive Constraints**: If $g_j(x^*) < 0$, then $\mu_j = 0$ (inactive).
- **Convexity**: KKT conditions are **sufficient** for optimality in convex problems.
- **Constraint Qualification**: Ensures KKT necessity
# References
---
- Deepseek
