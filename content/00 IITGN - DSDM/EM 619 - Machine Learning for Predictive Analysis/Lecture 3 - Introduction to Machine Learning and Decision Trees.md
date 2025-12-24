---
Lecture Date: 2025-01-25
Presentation: 
Links:
  - "[[Decision Tree]]"
Subject:
  - "[[EM 619 - Machine Learning for Predictive Analysis]]"
Professor Name: Ashish Tendulkar Sir
tags:
  - EM619
---
```table-of-contents
```
# Introduction
## Traditional Programming
![[CleanShot 2025-02-02 at 16.32.43@2x.png]]
**Components of ML algorithm**
- **Training data**
	- Input, Output
		- Features, Label (x, y)
- **Model**
	- label = function(features)
	- **label = weight$_0$ + weight$_1$ * feature$_1$ + weight$_2$ * feature$_2$ + ... + weight$_m$ * feature$_m$**
	- Determine weights or a weight vector
- **Loss Function/Objective Function**
	- e.g., difference between actual label (from training set) and predicted label.
		- Absolute difference between actual label and predicted label
		- Square of a difference between actual and predicted labels.
		- Sum up these errors across all training examples. **We want to achieve minimum error on the training set.**
	- Now that we have a model and loss function, we can test how well different weight vectors perform on the loss function. There are infinite weight vectors.
		- e.g., weight0 = 0, weight1 = 0, weight2 = 0, ..., weightm = 0
		- weight = $[0,0,0,...,0]$
	- Loss depends on the weight vector
		- e.g., loss = (predicted - actual)$^2$
		-            = ((weight$_0$ + weight$_1$ * feature$_1$ + weight$_2$ * feature$_2$ + ... + weight$_m$ * feature$_m$) - actual label)
		- By changing the values of weights, we obtain different value of loss. Hence we can say that loss is a function of weights.
- **Optimization Procedure**
	- Optimize loss function with respect to weights (also called as parameters) of the model.
	- e.g., Gradient Descent algorithm

> [!note] Note
**There can be multiple models based on values of hyper-parameters and we need a way to select the most effective model - this is model selection.** E.g., fixing optimal depth of decision tree.

After applying optimization algorithm, we obtain weights of the model. Now we need a way to evaluate the model.
- **Evaluation Criteria**
**Logistic Regression Model:** sigmoid(weight$_0$ + weight$_1$ * feature$_1$ + weight$_2$ * feature$_2$)
**When you start training the model**
- *Observe loss curves*
	- If your *loss curve* is going down with each iteration, it means the model is learning
	- If *loss* is not going down, we need to finetune the learning rate
	- If the *loss* is reducing very slowly, increase the learning rate.
After you train the model

| Training Loss | Test Loss                                               | Interpretation              |
| ------------- | ------------------------------------------------------- | --------------------------- |
| Low           | Low                                                     | Just right fit (Good model) |
| High          | High                                                    | [[Underfitting]]            |
| Low           | Test loss reduces initially and then it starts going up | [[Overfitting]]             |
> [!IMPORTANT] IMPORTANT
> **What can you do when you detect that the model that you trained is underfitting?**
> We need to bring in polynomial features - in other words we need to increase the capacity of the model to fit more complex decision boundaries.
> ==GETTING MORE DATA DOES NOT HELP IN ADDRESSING UNDERFITTING SITUATION==

> [!IMPORTANT] IMPORTANT
> **What can you do when you detect that the model that you trained is overfitting?**
> Get more data.
> Reduce complexity of the model.

# Decision Trees
- We use DT both for classification as well as regression problems.
## Components of Decision Tree Model
- **Training Data**
	- Features, label (real number for regression, discrete value for classification)
- **Model**
	- Decision Tree Classifier
	- Decision Tree Regressor
- **Loss function**
- **Optimization procedure**
- **Evaluation criteria**
## Different Scenarios
- Discrete features and discrete label (*classification)
- Continuous features and discrete label (*classification*)
- Discrete features and continuous label (*regression*)
- Continuous features and continuous label (*regression*)
When it comes to construction of a decision tree, we really need to take two decisions:
1. Which features to choose for the current node?
2. How do we split the tree on the values of this node?
# Entropy
## Formula

$$
\text{Entropy} = -\text{p(yes)} * \log_2 \text{p(yes)} - \text{p(no)} * \log_2 \text{p(no)}
$$

Information Gain helps us find out the reduction in impurity by partitioning data on a particular attribute.
- For outlook, we get three partitions,
	- Outlook = Sunny(5), # Yes = 2, # No = 3
	- Outlook = Rain(5), # Yes = 3, # No = 2
	- Outlook = Overcast(4), # Yes = 4, # No = 0
- Entropy
	- Outlook = Overcast => Entropy = 0
	- Outlook  = Sunny => Entropy = $-\frac{3}{5}*\log(\frac{3}{5}) - \frac{2}{5}*\log(\frac{2}{5})$
	- Outlook = Rain => Entropy = $-\frac{2}{5}*\log(\frac{2}{5}) - \frac{3}{5}*\log(\frac{3}{5})$
# Information Gain

$$
\text{Gain(Entire Set, Attribute)} = \text{Entropy(Entire Set)} - \sum_{\text{values of attribute}} \frac{\text{No. of examples with attribute = v}}{\text{No. of total examples}}* \text{entropy (attribute with value = v)}
$$

Writing Rules from learnt decision tree
- if (Outlook = SUNNY and Humidity = HIGH) then play = NO
- if (Outlook = SUNNY and Humidity = NORMAL) then play = YES
- if (Outlook = OVERCAST) then play = YES
- if (Outlook = RAIN and Wind = WEAK) then play = YES
- if (Outlook = RAIN and Wind = STRONG) then play = NO