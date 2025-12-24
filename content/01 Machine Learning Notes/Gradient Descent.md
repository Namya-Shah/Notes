---
Link: 
tags:
  - ML
  - Gradient-Descent
---
- In Machine Learning lingo, the **sum of squared residuals** is a type of **Loss Function**.
- Gradient descent is an algorithm that numerically estimates where a function outputs its lowest values. That means it finds local minima, but not by setting $\nabla f = 0$ like we've seen before.
  ![[CleanShot 2025-02-05 at 11.30.08@2x.png]]
- Think of a function $f(x,y)$ that defines some hilly terrain when graphed as a height map. We learned that the gradient evaluated at any point represents the direction of steepest ascent up this hilly terrain. The idea here is to *maximize* the function: start at a random input, and as many times as we can, take a small step in the direction of the gradient to move uphill. In other words, walk up the hill.
- To *minimize* the function, we can instead follow the negative of the gradient, and thus go in the direction of steepest descent. This is gradient descent. Formally, if we start at a point $x_0$ and move a positive distance $\alpha$ in the direction of the negative gradient, then our new and improved $x_1$ will look like this:

  $$
  x_1 = x_0 - \alpha \nabla f(x_0)
  $$

  > [!IMPORTANT] IMPORTANT
  > Gradient Descent is sensitive to the scale of features. Standardizing or normalizing inputs can speed up convergence.
- # Terminologies
- ## Cost Function
	- The cost function measures how well the model is performing; our goal is to minimize this.
- ## Learning Rate
	- The learning rate, often denoted as alpha($\alpha$), controls the size of the steps we take.
	- If it's too small, convergence is slow; too large, then we might overshoot the minimum.
- # Variants of Gradient Descent
- ## [[Batch Gradient Descent]]
	- Batch gradient descent uses the entire dataset to compute the gradient for each update. **This can be computationally expensive for large datasets.**
- ## [[Stochastic Gradient Descent (SGD)]]
	- Stochastic Gradient Descent (SGD) uses a single random data point for each update. It's faster per iteration but noisier, which can help escape local minima.
- ## [[Mini-Batch Gradient Descent]]
	- Mini-batch gradient descent is a compromise, using small subsets of data. It balances efficiency and noise.
- ## [[Nesterov Accelerated Gradient (NAG)]]
	- Nesterov Accelerated Gradient (NAG) is a variant that looks ahead before computing the gradient, leading to better convergence in practice.
- ## Adaptive Learning Rate Methods
- ### [[AdaGrad Gradient Descent]]
- AdaGrad uses squared gradients to scale the learning rate, which is good for sparse data.
- ### [[RMSProp Gradient Descent]]
- RMSProp uses an exponentially moving average to handle non-convex problems.
- ### [[Adam Gradient Descent]]
- Adam combines momentum and RMSProp, adjusting both first and second moments of gradients.
  
  > [!IMPORTANT] Common Pitfalls
  > 1. Not scaling data
  > 2. Choosing a bad learning rate
  > 3. Not checking convergence
  > *Debugging by plotting the cost function over iterations helps. If the cost fluctuates, the learning rate might be too high. If it decreases too slowly, the learning rate could be too low.*
- [[Backpropogation]] computes the gradients efficiently.
- Optimizers like [[Adam Gradient Descent]] are default choice in many cases.
- Gradient clipping is used in cases of exploding gradients, common in RNNs. Limits the gradient magnitude during backpropagation.
# References
---
1. [Khan Academy](https://www.khanacademy.org/math/multivariable-calculus/applications-of-multivariable-derivatives/optimizing-multivariable-functions/a/what-is-gradient-descent)
2. 