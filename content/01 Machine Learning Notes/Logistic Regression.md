---
Link: 
tags:
  - ML
---
# Notes
**Use Case:** Binary Classification problems like spam email detection, customer churn prediction.
### Overview
- Logistic regression is used for binary classification problems, such as spam detection or predicting whether a customer will make a purchase.
- Classifies input data into discrete categories using a logistic function to model the probabilities.
### Learning Objectives
- Grasp the concept of logistic regression and its difference from linear regression.
- Practice implementing logistic regression on a binary classification problem.
#### Practice Questions
1. Use logistic regression to classify emails as spam or not spam.
2. Discuss how changing the threshold value affects the model's performance.
## Cost Function
- The cost (or loss) function commonly used for logistic regression is the binary cross-entropy loss (also known as log loss):

$$
J(\theta) = - \frac{1}{m}\sum^m_{i=1}[y^{(i)}\log(h(x^{(i)})) + (1-y^{(i)})\log(1-h(x^{(i)}))]
$$

where,
- $m$ is the number of training samples,
- $y^{(i)}$ is the true label of sample $i$,
- $h(x^{(i)})$ is the predicted probability for sample $i$.
# References
---
1. [Cost Function](https://chatgpt.com/c/67a97a79-cf18-800f-9167-da21b887343d)
