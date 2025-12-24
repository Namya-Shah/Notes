---
Lecture Date: 2025-02-19
Presentation: 
Links: 
Subject:
  - "[[EM 619 - Machine Learning for Predictive Analysis]]"
References:
  - "[[Linear Regression]]"
tags:
  - EM619
---
```table-of-contents
```
# Linear Regression
## Introduction
- Output is continuous in nature
![[CleanShot 2025-02-19 at 13.04.25@2x.png]]
![[CleanShot 2025-02-19 at 13.12.52@2x.png]]
- Demand increases, if # of occupants increases, then $\theta_2$ is likely to be positive
- Demand increases, if temperature increases, then $\theta_1$ is likely to be positive.
- Base demand is independent of the temperature and the # of occupants, but, likely positive, thus $\theta_0$ is likely positive.
![[CleanShot 2025-02-19 at 13.17.02@2x.png]]
- For a good fit model, $|\epsilon_1|, |\epsilon_2|, |\epsilon_3|, ...$ should be small
![[CleanShot 2025-02-19 at 13.43.29@2x.png]]
![[CleanShot 2025-03-06 at 10.15.38.png]]
![[CleanShot 2025-03-06 at 10.15.51.png]]
- Converting this $f(x)$ in quadratic multivariate function.

$$
f(x) = y^Ty-2y^TX\theta + \theta^TX^TX\theta
$$

### Quadratic Multivariate Function

$$
f(x) = \text{something} + 3\theta_1 - 2\theta_2 + 6 \theta_0^2 - 28 \theta_1^2
$$

$y^Ty$ -> Constant in $\theta$
$3\theta_1-2\theta_2$ -> Linear in $\theta$
$6\theta_0^2-28\theta_1^2$ -> Quadratic in $\theta$
![[CleanShot 2025-02-19 at 16.23.21@2x.png]]
- Here, the first 3 can be solved using **Linear Regression** but the 4$^{th}$ one cannot be solved using Linear Regression.
- 
# Misc. Points
- On tabular data, [[Random Forest]] and [[Ensemble Methods]] is still the best according to some research.
- In case of relationship between data points, such as pixels in an image, Neural Networks like [[Convolutional Neural Networks (CNNs)]] perform really well. For text like data points, we can build models like [[Long Short-Term Memory (LSTM)]]