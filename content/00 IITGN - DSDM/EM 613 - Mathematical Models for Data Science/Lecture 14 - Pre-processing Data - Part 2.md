---
Lecture Date: 2024-07-27
Presentation: "[[Lecture 13 & 14.pdf]]"
Links:
  - "[[Log Transformation]]"
  - "[[Box-Cox Transformation]]"
  - "[[Label Encoding]]"
  - "[[One-Hot Encoding]]"
  - "[[Ordinal Encoding]]"
  - "[[Binning]]"
Subject:
  - "[[EM 613 - Mathematical Models for Data Science]]"
tags:
  - EM613
---
```table-of-contents
```

> Transformations may destroy your original feature space. Once the transformation takes place, the original feature space cannot be inverted back. Example: Washing a shirt in a detergent still can retrieve the original feature space but washing a shirt in an acid destroys it.

## Log Transformation

- Apply a logarithmic transformation to reduce skewness.
- Formula: $x' = \log(x)$
- We **avoid data manipulation**, and prefer **data transformation**. Suppose we have a value of 4 and to fit a context we make it 8.

### When to use Log Transformation?
#### Appropriate Scenarios
- Data with positive [[skewness]].
- Data with heteroscedasticity (non-constant variance).
- Data spanning several orders of magnitude.
- **Normal distribution has 0 skewness**
- When we do regression, the data that is fitted and left off should be normally distributed.
#### Examples

- Financial data (e.g., income, stock prices).
- Biological data (e.g., growth rates, population sizes).
- **Homoscedasticity**
    - Mean-stationary
    - Variance-stationary
- **Heteroscedasticity → Homoscedasticity**
    - Taming the variance
    - Using log for the same
- It is doing transformation on our feature space X to get the desirable results.
> **Limitation:** We can't use log transformation in Categorical data.
> **Constant Variance Time Series:** Frequency of electricity received at home.
> *We can use addition or subtraction as first order transformation.*
### Box-Cox Transformation
- Box-Cox transformation is a family of power transformations that aim to stabilize variance and make the data more normally distributed.
- First, we take data and then we find **max. likelihood of $\lambda$**
- If $\lambda = 0$, we do log transformation and if $\lambda \not= 0$, we do polynomial transformation.
- It forces data to behave like normal distribution.
- $\lambda$ can be any value but if $y$ is negative, you can't apply box-cox transformation.
- Make everything positive and then only apply box-cox transformation
- Any negative number ($y$) to the power a decimal number is always a complex number so we can't apply box-cox transformation.
- ***Real world example***
	- When a coffee falls on a white shirt,
		- Putting the white shirt in water: Addition **(STEP 1)**
		- If Step 1 doesn't work, Applying detergent: Log Transformation **(STEP 2)**
		- If Step 2 doesn't work, Applying bleach: Box-Cox Transformation **(STEP 3)**
- **Mathematical Formula**
	![[CleanShot 2024-07-27 at 14.42.36.png]]
### When to use Box-Cox transformations over log transformation
**Flexibility in Transformation:**
- Box-Cox transformation can handle a variety of transformations, not just logarithmic.
- The optimal $\lambda$ can be any real number, allowing for more tailored transformations.
### Positive Values Only
**Requirements:**
- Both Box-Cox and log transformations require positive data.
- Box-Cox can be adjusted for different ranges and scales.
> We would first transform and remove outlier. But in some cases, if you are sure about outliers then you can remove them first.
## Pre-processing Discrete and Categorical Data
### Example:
- Consider a dataset of student grades in different subjects.
- Grades are categorical values: A, B, C, D, and F.
- We need to preprocess these grades for data analysis and feature engineering.
## Encoding Discrete and Categorical Data
### Why Encoding is Necessary
- Data analysis often requires numerical input.
- Categories need to be converted
### Common Encoding Techniques
- Label Encoding
- One-Hot Encoding
- Ordinal Encoding
### Label Encoding
#### Definition
- Assigns a unique integer to each category.
#### Example
- Grades: A, B, C, D, F
- Encoded: 0, 1, 2, 3, 4
#### Usage in Data Analysis
- Useful for statistical models that require numerical input.
- Enables correlation analysis between categorical variables and numerical outcomes.
### One-Hot Encoding
#### Definition
- Converts each category into a new binary feature.
- There is only one value that is 1 and no other value. Other values are 0.
- **Each feature is 1 if the category is present, otherwise 0.**
#### Example
- Grades: A, B, C, D, F
- Encoded: $[1,0,0,0,0],[0,1,0,0,0],[0,0,1,0,0],[0,0,0,1,0],[0,0,0,0,1]$

$$











A = \begin{bmatrix}
1\\
0\\
0\\
0\\
\vdots
\end{bmatrix},\quad
B =\begin{bmatrix}
0\\
1\\
0\\
0\\
\vdots
\end{bmatrix},
\quad
Z = \begin{bmatrix}
0\\
0\\
0\\
\vdots \\
1
\end{bmatrix}

$$

- **If we have a long sentence, then the one-hot encoding becomes very large and it becomes expensive operation memory-wise.**
#### Usage in Data Analysis
- Useful for visualizing relationships between categories and numerical outcomes.
- Facilitates the use of statistical models that handle binary variables.
### Ordinal Encoding
#### Definition
- Assigns an integer to each category based on their order.
#### Example
- Grades: A, B, C, D, F
- Encoded: 4, 3, 2, 1, 0
#### Usage in Data Analysis
- Maintains the ordinal relationship between categories.
- Enables regression analysis where the order of categories matters.
## Binning
### Binning as a pre-processing technique
- **Equal-width binning:** Divides the range into intervals of equal size.
- **Equal-frequency binning:** Each bin has the same number of observations.
- **Custom binning:** Bins defined based on domain knowledge or specific criteria.
### Usefulness
- Reduces the effects of minor observation errors.
- Handles outliers effectively.
- Simplifies models by reducing the number of distinct values.
### Binning followed by encoding
- Binning can be followed by encoding to convert bins into numerical values.
- Useful for models that require numerical input.
## Choosing the Right Encoding Technique
### Considerations
- Nature of the Data: Ordinal vs Nominal
- Impact on Analysis: How the encoding affects the interpretation of results.
- Data Size: One-Hot encoding can lead to a large number of features.
### Example
- Grades (Ordinal): Ordinal Encoding
- Countries (Nominal): One-Hot Encoding
## Conclusions
- Pre-processing enhances the performance of data science models and understanding of the system being modeled.
- The selection of pre-processing techniques must be driven by the specific property of data that needs to be addressed.