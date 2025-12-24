---
Lecture Date: 2024-07-25
Presentation: "[[Lecture 13 & 14.pdf]]"
Links:
  - "[[Pre-processing Data]]"
  - "[[Continuous Data]]"
  - "[[Discrete Data]]"
  - "[[Categorical Data]]"
  - "[[Ordinal Data]]"
  - "[[Time Series Data]]"
  - "[[Outlier Detection]]"
  - "[[Normalization]]"
  - "[[Standardization]]"
  - "[[Min-Max Scaling]]"
  - "[[Mean/Median Imputation]]"
  - "[[Interpolation]]"
  - "[[IQR Method]]"
  - "[[Z-Score Method]]"
Subject:
  - "[[EM 613 - Mathematical Models for Data Science]]"
Lecturer:
  - "[[Udit Bhatia]]"
tags:
  - EM613
---
```table-of-contents
```
# Outcomes of this lecture
- Appreciate why pre-processing is needed in various data science problems.
- Understand various pre-processing techniques for different types of data.
- Write codes in Python to implement various pre-processing techniques discussed and improvised on the techniques not discussed.
# Problem Description
- **Objective:** Predict the housing price ($, INR) based on certain input features.
- **Input Features:**
	- Square Footage (sq ft)
	- Number of Bedrooms (count)
	- Neighbourhood (categorical: A, B, C)
	- Age of House (years)
- **Output:**
	- Housing Price ($, INR)
> **We should plot the raw data first. Whenever we try to plot the raw data, our scales are mismatched and outliers create significant difference for us.**

# Comparison of Raw and Processed Data

--- start-multi-column: ID_6dt6
```column-settings
Number of Columns: 2
Largest Column: standard
```

![[CleanShot 2024-07-27 at 14.21.26.png]]

--- column-break ---

- **Left:** Scatter plot and box plot on the left: Notable issues include missing values in square footage, extreme outliers (e.g., an unusually large house with 30,000 sq ft), and skewed distributions.
- **Right:** Scatter plot and box plot on the right display the data after pre-processing. Missing square footage values were imputed with the mean, outliers were capped at the 95th percentile, and numerical features were standardized.

--- end-multi-column
### One Size Does Not Fit All
- **Continuous Data:**
    - Examples: House prices, square footage.
    - Mathematical Approaches:
	    - **Scaling:** Min-Max Scaling, Standardization.
        - **Outlier Handling:** Z-score normalization, log transformation.
- **Discrete Data:**
    - Examples: Number of bedrooms, count of items.
    - Mathematical Approaches:
        - **Normalization:** Scaling discrete values to a specific range.
        - **Binning:** Converting numerical values into categorical bins.
- **Categorical Data:**
    - Examples: Type of house, color.
    - Mathematical Approaches:
        - **One-Hot Encoding:** Converting categories into binary vectors.
        - **Label Encoding:** Assigning integer values to categories.
- **Ordinal Data (Quality Data):**
    - Examples: Customer satisfaction ratings, education level.
    - Mathematical Approaches:
        - **Ordinal Encoding:** Assigning ordered integer values to categories.
        - **Normalization:** Scaling the ordinal values.
- **Time Series Data:**
    - Examples: Stock prices, weather data over time.
    - Mathematical Approaches:
        - **Differencing:** Removing trends and seasonality.
        - **Rolling Statistics:** Applying moving averages.
# Dataset Overview
![[CleanShot 2024-07-27 at 14.22.45.png]]
- If we don't standardize our data our model is going to get confused if their scale are too different.
# Pre-processing Continuous Data
## Handling Missing Values
> We never collect a single feature to determine the whole scenario. We need to generate as many features as possible.

### Mean/Median Imputation
- Replace missing values with the mean or median of the column.
- **Mean is very sensitive to outliers. If a outlier is far away from the data then the mean would shift itself from the data towards the outlier.**
- **Mean and median would coincide in normal distribution. They may not coincide for other distributions. Mean will be biased towards outliers.**
- **Median can also alter the overall behaviour of the data.**
- In mean imputed graphs, we will have highest frequency at mean.
### Interpolation
- Estimate missing values using linear or polynomial interpolation.
- We never pass `0` as an argument to fill the null values as it can be plotted on a real line and will distort our data. We will use `data['Square Footage].fillna(data['Square Footage'].mean())`.
- Interpolation gives us preserved distribution and does not change a lot from raw data.
- Interpolation assumes that variations are linear.
> When we plot on a box-plot, the raw data box-plot doesn’t change the mean-imputed box-plot. They do not change drastically but they may. We need to plot at every point as we are processing the data If it alters our box plot seriously, then we need to change the method of filling in the missing values.

- We want to preserve the quartiles, inter-quartile range and distribution to begin
- From Data Science perspective, if we have more than 5% data points missing, we discard that particular observation.
- Data Imputation is not a substitute of Data Collection
## Outlier Detection and Treatment

**Basic Meaning of Outliers**

1. Odd one out
2. Abruptly high
3. Stands out from norm
4. Out of standard range
> Generalized Models → We want to develop generalized models We don’t want these model to tell me an exact value but to generalize the dataset.

- To ensure generalisability, we want our model to be sensitive to outliers. First, we will identify the outliers and then exclude them from the analysis.
- _**Very few points far away from the average behaviour.**_
### Z-Score Method
- Calculate z-scores for each data point.
- Identify outliers as data points with z-scores beyond a threshold (e.g., $\geq 3$ or $\leq -3$).
- For Normal Distribution, we have probability highest (1 ) in the median point and when we go either left or right from that point the probability tends to go to 0.
- When calculating **Z-Score**, the value we get is the endpoint and values after the endpoint are considered as **outliers**.
### IQR Method
- Calculate the **interquartile range (IQR) → Difference in 75%ile - 25%ile**.
- Identify outliers as data points outside $1.5* \mathrm{IQR}$ above the third quartile and below the first quartile. We need to have points at least 1.5 to 3 IQR for being an outlier.
- **Outliers is a problem in a continuous data but discrete variables do not have problem with outliers**
- Outliers and extremes are two different things, while outlier doesn’t change much features it can be excluded but in extreme it may hold some important value.
- We will not model extremes with normal distribution but we will use fat tailed distribution.
## Scaling and Normalization
### Min-Max Scaling
- Rescale data to a fixed range, usually $[0,1]$.
- Formula: $x' = \frac{x - \min(x)} {\max(x) - \min(x)}$
- It is very sensitive to outliers as $x_{min},x_{max}$ can be a outlier. So, we first need to remove outlier and do this scaling that is one way to ensure that you are not sensitive to outlier.
- It makes every value positive.
### Standardization
- Rescale data to have a mean of 0 and a standard deviation of 1.
- Formula: $Z = \frac {X - \mu} {\sigma}$
