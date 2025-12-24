---
Link: 
tags:
  - ML
  - Lasso-Regression
  - Ridge-Regression
  - L1-Norm
  - L2-Norm
---
# Notes
- *Lasso Regression* uses **L1-Norm** while *Ridge Regression* uses **L2-Norm**
- For a constant point such as (1,0), when we use Lasso Regression, it will form a square/diamond shape. When we want to convert it to Ridge Regression, we will penalize it heavily to keep the values near to (1,0) (i.e., the starting point).
## Example
**Ridge Regression** is like telling the cook: "Use all spices, but be careful with each one." So the cook uses tiny amounts of every spice. Maybe a pinch of salt, a tiny bit of pepper, a dash of paprika - everyone gets to play, just in small amounts.

**Lasso Regression** is like telling the cook: "Only use the most important spices." So the cook might end up using just salt and pepper, completely ignoring the other spices. But they might use these chosen spices in larger amounts than Ridge would.

Choosing a regression is dependent on the data and regularization strength. In context of cooking, data is recipe of your dish and regularization strength is spice rules of your dish.
## Lasso Regression (L1-Norm)
- It creates diamond/rhomboid contours, which tend to force some coefficients exactly at zero at the corners. This leads to sparse solutions with fewer non-zero coefficients.
### Equation

$$
\text{L1-Norm} = |x_1| + |x_2| + |x_3| + \dots + |x_n|
$$

## Ridge Regression (L2-Norm)
- It creates circular/spherical contours around the coefficients, shrinking them proportionally towards zero. This tends to result in many small but non-zero coefficients.
### Equation

$$
\text{L2-Norm} = \sqrt{x_1^2 + x_2^2 + x_3^2 + \dots + x_n^2}
$$

## Some Important Points
- Due to these geometric properties, Lasso typically produces a simpler model with fewer active features. However, the "area" or total magnitude of impact from the remaining non-zero coefficients isn't necessarily smaller or larger than Ridge - it depends entirely on your specific dataset, the true underlying relationships, and the regularization strength ($\lambda$) chosen for each method.
# References
---
1. Claude
