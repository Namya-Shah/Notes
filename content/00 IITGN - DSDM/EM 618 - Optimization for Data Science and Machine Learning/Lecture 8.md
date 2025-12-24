---
Lecture Date: 2025-02-07
Presentation: 
Links: 
Subject:
  - "[[EM 618 - Optimization for Data Science and Machine Learning]]"
References: 
tags:
  - EM618
---
```table-of-contents
```
# Why Constrained Optimization in Data Science?
- Many real-world data science problems involve constraints:
	- **Budget or capacity limits** (e.g., spending constraints in marketing campaigns).
	- **Fairness or regulatory guidelines** (e.g., no protected group may exceed certain risk).
	- **Accuracy/performance constraints** (e.g., error rates, timing limits).
- Enforcing constraints directly can be difficult
- Penalty methods offer a practical way to handle constraints by modifying the objective function.
## Common Examples
- **Regularization in Machine Learning**
	- "Penalty" on model complexity (e.g., L1 or L2) to prevent overfitting.
- 
# Misc. Points
- **Larger is the violation, larger is the penalty**
- Incentivize model for overfitting by choosing $\alpha$ very large.
- Lagrange $\lambda$ is mathematically determined
- Penalty $\lambda$ is pre-determined
- 


