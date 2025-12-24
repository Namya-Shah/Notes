Google Colab: [Notebook Link](https://colab.research.google.com/drive/1iGnAO15evnBBW3Kge9mpbA0c_oH6deBY?usp=sharing)
# Question 1
## Part 1: Importance of Standardization in Machine Learning

$$

z = \frac {value - mean} {standard \ deviation}

$$

- It rescales data to have a mean of 0 and standard deviation of 1
- It is useful when the features have large differences in their ranges. It treats every feature same irrespective of their values.
- It is more useful when you have large number of outliers as *standardization scales the data based on the standard deviation.*
- When we have different units in data (e.g., pounds, meters, miles, etc.), we use standardization to establish a proper working ML model.
- Machine learning estimators required **standard normally distributed data** to behave properly without causing bad effects on the estimator.
- If a feature has a variance larger than others, then it might dominate other imporant features and make the estimator unable to learn from other features correctly.
- It is used for different purposes (e.g., clustering, knn, svm, regression models, lasso and ridge regressions, etc.).
## Part 2: Difference in visualization between PCA and t-SNE
- PCA preserves global structure whereas t-SNE preserves local structure.
- Due to preserving global structure, PCA has its plots scattered all over the plane which maximizes its variance whereas due to preserving local structure, t-SNE has its points closer to each other.
- As PCA performs dimensionality reduction, it will retain the global variance while compromising the local relationships which are often lost after projection.
- In t-SNE, as it preserves local relationship, the data points in the high-dimensional space are likely to stay the same in low-dimensional space.
- **Difference in visualization:** In PCA, the plots are spread out and in t-SNE it forms a oval-shape structure where it retains all the scatters.
## Part 3: Classifier's performance using accuracy and impact of dimensionality reduction
- As from classification report, we can see that t-SNE has low accuracy than PCA.
- `Accuracy(PCA) -> 0.93`
- `Accuracy(t-SNE) -> 0.52`
### Impact of Dimensionality Reduction
- *Dimensionality Reduction* is used to preserve most important information while removing irrelevant information.
- *Dimensionality Reduction* helps in generalizing the model for complex datasets by reducing the features.
- It also removes noise present in the dataset due to which we need to compromise in accuracy.
# Question 2
## Part 1: Describe the dataset
- **Total Samples:** 569
- **Classes**
	- Malignant
	- Benign
- **Samples in Malignant Class:** 212
- **Samples in Benign Class:** 357
- **Dimensions/Features:** 30
- *There are no missing values in this dataset*
- There are ten real features:
	- Radius
	- Texture
	- Perimeter
	- Area
	- Smoothness
	- Compactness
	- Concavity
	- Concave Points
	- Symmetry
	- Fractal Dimension
## Part 2
- ANOVA F-test is a statistical method used to compare mean of three or more groups to see if there is a significant difference among them.
- **Formula**

$$

\frac{MSB}{MSE}

$$

MSB = Between Mean Sum of Squares

$$
MSB = \frac{\sum(y_i - \hat y_i)^2}{n} = \frac{SSB}{n}
$$

MSE = Error Mean Sum of Squares

$$
MSE = \frac{\sum(y_i - \hat y_i)^2}{n - 2} = \frac {SSE} {n - 2}
$$

- **ANOVA is suitable for continuous data because:**
	- Continuous data gives us accurate calculation of means and variability.
	- ANOVA expects to have normally distributed data, and continuous data is generally normally distributed.
	- ANOVA is sensitive to mean difference, it detects if we have small difference in means of groups
## Part 3
### CHI-SQUARE TEST EXPLANATION
- It is a non-parametric test that is performed on categorical (nominal or ordinal) data.
- It helps in finding the relationship between the features.
- It compares the observed frequencies under a specific hypothesis to assess if there is a statistically significant difference.
### MATHMEMATICAL FORMULA FOR CHI-SQUARE TEST

$$\chi^2 = \sum \frac{(O_i - E_i)^2}{E_i}$$

$\chi^2$ = chi squared value
$O_i$ = observed value
$E_i$ = expected value
#### TO CALCULATE EXPECTED FREQUENCY

$$E_i = \frac{\text{Row Total} \ \times \ \text{Column Total}} {\text{Grand Total}}$$

#### DETERMINE CHI-SQUARE STATISTIC AND STATISTICAL SIGNIFICANCE
- After calculating Chi-square value, we find degrees of freedom.

$$
df = n-1
$$

> Here, `df` -> degrees of freedom , `n` -> no. of samples
- We find critical value from the chi-square table. Critical value depends on degree of freedom ($df$) and significance value ($\alpha$).
- After we find critical value, we compare it with chi-square statistic.
	- If $\chi^2 > \text{critical value}$, we reject null hypothesis
	- If $\chi^2 < \text{critical value}$, we do not reject null hypothesis
#### IMPORTANCE OF FEATURE SELECTION FOR DISCRETE DATA
- If we have large number of data, there is a high possibility that some of the features are inter-linked which are not necessary for implementing. So we use feature selection to identify the most important features in the dataset.
#### CHI-SQUARE TEST HELPS IDENTIFY THE MOST IMPORTANT FEATURES IN OUR DATASET
- Features with high chi-square statistics are more informative because they have strong relation with target variable.
- Features with higher statistic and lower p-values are considered important.
# Question 3
## Discussion
- **What does the Chi-Square score represent in the context of feature selection?**
	- Chi-Square score represent the dependence between a categorical feature and the target variable.
- **How can the Chi-Square test be used to improve the performance of machine learning models?**
	- Identifies relevant categorical features and neglects the features that are linear.
	- It reduces overfitting by elimination irrelevant features.
	- It can lead to simpler models with fewer features, making them easier to interpret.
- **What are the limitations of using the Chi-Square test for feature selection?**
	- It is very sensitive to sample size. With large sample size, even irrelevant features can appear significant.
	- If only tells us if the two variables are related to one another. It does not imply that one has any effect on the other.
- **Identify which features are most important and how this information can be used in feature selection for machine learning models.**
	- *Ten most important features*
		- Mean Radius
		- Mean Texture
		- Mean Perimeter
		- Mean Area
		- Mean Smoothness
		- Mean Compactness
		- Mean Concavity
		- Mean Concave Points
		- Mean Symmetry
		- Mean Fractal Dimension
$X(3) \mid X(2) = \frac{1}{2} \sim N\left(\frac{1}{2},4\right)$ 