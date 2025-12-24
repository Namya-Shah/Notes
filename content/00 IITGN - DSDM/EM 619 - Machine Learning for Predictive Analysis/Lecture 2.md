---
Lecture Date: 2025-01-21
Presentation: 
Links: 
Subject:
  - "[[EM 619 - Machine Learning for Predictive Analysis]]"
Professor Name: Nipun Batra Sir
References: 
tags:
  - EM619
---
```table-of-contents
```
- Precision-Recall Tradeoff
Precision
- Matthew's Correlation Coefficient
# Traditional Programming
![[CleanShot 2025-03-02 at 09.01.55.png]]
# Machine Learning
![[CleanShot 2025-03-02 at 09.02.25.png]]
# What is Machine Learning?
- A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P if its performance at tasks in T, as measured by P, improves with experience E.

In **traditional programming**, we give **rules and data** to get **answers** but in **machine learning**, we give **answers and data** to get **rules**.

## Example
![[CleanShot 2025-01-24 at 20.04.32@2x.png]]
# Generalisation
![[CleanShot 2025-03-02 at 09.05.28.png]]
# Metrics for Classification
## Accuracy
### Formula

$$
\text{Accuracy} = \frac{||y = \hat y||}{||y||}
$$

### Cases
- Cancer Screening
- Planet Detection
[[Class Imbalance]]

## Precision
![[CleanShot 2025-03-02 at 09.07.06.png]]
### Formula

$$
\text{Precision} = \frac{||y = \hat y = \text{Good}||}{||\hat y = \text{Good||}}
$$

### Definition
- "The fraction of relevant instances among the retrieved instances", i.e., "out of number of times we predict Good, how many times is the condition actually Good"
### In Reference to Confusion Matrix
![[CleanShot 2025-03-02 at 09.15.40.png]]
## Recall
![[CleanShot 2025-03-02 at 09.10.00.png]]
### Formula

$$
\text{Recall} = \frac{||y = \hat y = \text{Good}||}{||y = \text{Good}||}
$$

### Definition
- The fraction of the total amount of relevant instances that were actually retrieved.
### In Reference to Confusion Matrix
![[CleanShot 2025-03-02 at 09.16.07.png]]
# F1 - Score

$$
\text{F-Score} = \frac{2 \times \text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}}
$$

# Confusion Matrix
![[CleanShot 2025-03-02 at 09.14.45.png]]
# Matthew's Correlation Coefficient

$$
\text{Matthew's correlation coefficient} = \frac{TP \times TN - FP \times FN}{\sqrt{(TP + FP)(TP + FN)(TN + FP)(TN + FN)}}
$$

# Mean Squared Error (MSE)
![[CleanShot 2025-03-02 at 09.29.25.png]]

$$
\text{Mean Squared Error (MSE)} = \frac{\sum^N_{i=1}(\hat y_i - y_i)^2}{N}
$$

# Root Mean Squared Error (RMSE)
![[CleanShot 2025-03-02 at 09.30.40.png]]

$$
\text{Root Mean Squared Error (RMSE)} = \sqrt{\text{MSE}}
$$

# Mean Absolute Error
![[CleanShot 2025-03-02 at 09.35.19.png]]

$$
\text{Mean Absolute Error (MAE)} = \frac{\sum^N_{i=1}|\hat y_i-y_i|}{N}
$$

# Mean Error
![[CleanShot 2025-03-02 at 09.38.11.png]]

$$
\text{Mean Error (ME)} = \frac{\sum^N_{i=1}\hat y_i-y_i}{N}
$$

> [!IMPORTANT] NOTE
> Downside of using *mean error* is that **errors can get cancelled out**.
# Anscombe's Quartet
![[CleanShot 2025-03-02 at 09.40.26.png]]





---
# Questions
1. Is predicting on test set enough to say our model generalises?
	- Yes, as real world may have different outputs, so our model may not be able to predict it accurately.
2. Can we have two output variables?
	- Yes, we can have two output variables
3. 