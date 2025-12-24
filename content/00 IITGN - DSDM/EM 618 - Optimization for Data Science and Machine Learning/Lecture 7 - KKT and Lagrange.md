---
Lecture Date: 2025-02-05
Presentation: "[[Lecture 7 Lagrange Multipliers KKT Condition Feb 5 2025.pdf]]"
Links: 
Subject:
  - "[[EM 618 - Optimization for Data Science and Machine Learning]]"
Refernces:
  - "[[Karush-Kuhn-Tucker (KKT)]]"
  - "[[Lagrange & Dual Optimization]]"
tags:
  - EM618
  - KKT
  - Lagrange-Multiplier
---
```table-of-contents
```
# Some Important Points
- `Samples` -> `Iteration` -> `Epoch`
- **Example**
	- Suppose you have 3000 samples,
		- 100 Samples -> 1 Iteration
		- 10 Iterations -> 1 Epoch
		- So we have 3 Epochs in total
- In **K-Fold Cross Validation**, we make sure that each chunk becomes test data once, here we are not worried about it.
- ![[CleanShot 2025-02-07 at 15.59.55@2x.png]]
- ![[CleanShot 2025-02-07 at 16.16.35@2x.png]]
- **[[Karush-Kuhn-Tucker (KKT)]]**
	- If your constraints are inequality type, in addition to $\nabla$(Lagrange) = 0. Some dual conditions also needed to be satisfied... $\lambda g(x) = 0$.
- ![[CleanShot 2025-02-07 at 17.09.06@2x.png]]
	- For *maximization* problem, we will just use negative sign to convert it to *minimization* and then use **Lagrange Multiplier**.
	- For *constraint* $g(x) = 0$, we will call it a "**point**" solution or use "**penalty**" method
- ![[CleanShot 2025-02-07 at 17.19.28@2x.png]]
- **ill-defined optimization**
# Active Constraint
- **Example**

	$$
	\min. f(x, y) \text{ subject to } g(x,y) \le 0, x\ge 0
	$$

	- **Lagrange Equation**

		$$
		\mathcal{L} = f(x,y) + \lambda_1 g(x,y) + \lambda_2(-x)
		$$

		- Either $-x = 0 \text{ or } \lambda_2 = 0$.
# Flashcards
- **Why is constrained optimization important in Data Science?**
	- **Answer:** Real-world problems have limitations (e.g., budgets, resource caps) or requirements (e.g., sparsity in models). Solutions must lie within a **feasible set** (e.g., L1 regularization, SVM margins).
	- **Example:** Lasso Regression restricts coefficients to an L1 "diamond", forcing some to zero for sparsity.
- **What's the difference between unconstrained vs. constrained optimization?**
	- **Unconstrained**: Minimize $f(x)$ freely (gradient $\nabla f(x) = 0$).
	- **Constrained**: Minimize $f(x)$ within boundaries (gradient $\nabla f(x)$ balanced with constrained gradients).
	- **Key Insight**: Optimal points often lie on constraint boundaries, not in the interior.
- **What are active vs. inactive constraints?**
	- **Active**: A constraint exactly satisfied at the solution (e.g., $g_i(x) = 0$)
	- **Inactive**: A constraint not affecting the solution (e.g., $g_i(x) < 0$).
	- **Example**: If $x \ge 0$ and the solution is $x=0$, this constraint is active.
- **What are Lagrange multipliers?**
	- Coefficients that "weight" the influence of constraints on the solution. They balance $\nabla f(x)$ with gradients of active constraints.
	- **Simple Analogy:** If you're pushing a box up a hill (minimize effort), Lagrange multipliers tell you how much the slope (constraint) affects your push.
- **What are the KKT conditions?**
	- **Stationarity**

	$$
		\nabla f + \sum \lambda_i \nabla g_i + \sum \mu_j \nabla h_j
	$$

	- **Primal Feasibility**: $x$ satisfies all constraints
	- **Dual Feasibility**: Lagrange Multipliers $\lambda_i \ge 0$.
	- **Complementary Slackness**: $\lambda_i g_i (x) = 0$ (inactive constraints have $\lambda_i = 0$).
	- **Purpose**: Systematic way to find optimal points under constraints.

- **How does Lasso regression use constraints?**
	- **Formulation**: Minimize $||y - Xw||^2$ subject to $||w||_1 \le \lambda$.
	- **Why**: The L1 constraint enforces sparsity (many $w_i = 0$) for simpler models.
	- **Geometric View**: Solutions lie on the surface/edges of an L1 "diamond".
- **What are common methods to handle constraints?**
	- **Penalty Methods**: Add a cost for violating constraints (e.g., $loss + \alpha \cdot \text{violation}$).
	- **Barrier Methods**: Block solutions from approaching boundaries (e.g., $\log(g(x))$) to penalize near-constraint edges
	- **Projection Methods**: After each optimization step, "project" $x$ back into the feasible set (e.g., clamping values to $x \ge 0$).
- **How do SVMs use constrained optimization?**
	- **Goal**: Maximize margin $\frac{1}{||w||}$ between classes.
	- **Constraint**: $y_i(w^Tx_i+b) \ge 1$ for all data points.
	- **Result**: The optimal hyperplane balances margin width and correct classification.