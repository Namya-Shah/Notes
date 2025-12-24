---
Lecture Date: 2025-03-04
Presentation: 
Links: 
Subject:
  - "[[EM 619 - Machine Learning for Predictive Analysis]]"
References: 
tags:
  - EM619
---
```table-of-contents
```
# Question: Predict the water demand of the IITGN campus
![[CleanShot 2025-03-04 at 10.26.51.png]]
- Demand increases, if # of occupants increases, then $\theta_2$ is likely to be positive.
- Demand increases, if temperature increases, then $\theta_1$ is likely to be positive.
- Base demand is independent of the temperature and # of occupants, but, likely positive, thus $\theta_0$ is likely positive.
# Normal Equation
## Generalized Linear Regression Format
- Assuming $N$ samples for training.
- # of features = $M$
![[CleanShot 2025-03-04 at 10.30.37.png]]

$$
\hat Y = X \theta
$$

# Good Fit
- $|\epsilon_1|, |\epsilon_2|, |\epsilon_3|, |\epsilon_i|$ should be small.
- minimize $\epsilon_1^2 + \epsilon_2^2 + \cdots + \epsilon_N^2$ -> $L_2$ Norm
- minimize $|\epsilon_1| + |\epsilon_2| + \cdots + |\epsilon_n|$ -> $L_1$ Norm
- $f(\theta) = y^Ty - 2y^TX\theta + \theta^TX^TX\theta$
# Basis Functions
- Linear regression only refers to linear in the parameters
- We can perform an arbitrary nonlinear transformation $\phi(x)$ of the inputs $x$ and then linearly combine the components of this transformation.
- $\phi: \mathbb{R}^D \rightarrow \mathbb{R}^K$ is called the basis function.
- Some Examples of Basis Functions
	- Polynomial basis: $\phi(x) = \{1,x,x^2,x^3,...\}$
	- Fourier basis: $\phi(x) = \{1, \sin(x), \cos(x), \sin(2x), \cos(2x), ... \}$
	- Gaussian basis: $\phi(x) = \{1, \exp(-\frac{(x-\mu_1)^2}{2\sigma^2}), \exp(-\frac{(x-\mu_2)^2}{2\sigma^2},...\}$
	- Sigmoid basis: $\phi(x) = \{1, \sigma(x-\mu_1), \sigma(x-\mu_2), ... \}$ where $\sigma(x) = \frac{1}{1+e^{-x}}$
- 