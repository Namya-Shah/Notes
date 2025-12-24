---
Link:
tags:
  - word
---
# Notes
- The **SGD (Stochastic Gradient Descent) Classifier** is an efficient machine learning algorithm for **linear classification** that is particularly useful when dealing with **large datasets**. It is part of the **scikit-learn** library in Python.
- **Shuffling data in SGD to avoid a loop if data is ordered.**
## What is Stochastic Gradient Descent (SGD)?
- **Gradient Descent (GD)** is an optimization algorithm used to minimize the loss function in machine learning models by updating model parameters iteratively.
	- **Batch Gradient Descent (BGD)**: Uses the entire dataset for each step of optimization.
	- **Mini-batch Gradient Descent**: Uses small random subsets (mini-batches) of the dataset.
	- **Stochastic Gradient Descent**: Uses **only one data point** at a time for optimization.
- **Why use SGD?**
	- Efficient for **large-scale datasets** (big data).
	- Faster convergence in **online learning** scenarios.
	- Works well with **sparse data** (like text classification).

# References
---
1. 
