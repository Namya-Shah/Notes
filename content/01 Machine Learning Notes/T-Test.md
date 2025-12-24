- T test is a type of inferential statistic used to determine if there is a significant difference between the means of two groups which may be related in certain features.
- It is commonly used when the test statistic would follow a normal distribution if the value of a scaling term in the test statistic were known. When the scaling term is unknown and is replaced by an estimate based on the data, the test statistics (under certain conditions) follow a student's t distribution.
# Why is it used?
- The T test is used for hypothesis testing to determine how significant the differences between two groups are, which could be related to certain features within the data.
- It is typically used when the data sets, like those involving human subjects, have unknown variances and a relatively small sample size.
# Advantages
- **Flexibility:** It can be used even when the data does not perfectly follow a normal distribution.
- **Small Sample Sizes:** Effective in handling smaller sample sizes (less than 30).
- **Two Samples:** Can be used to compare the means from two independent samples or paired samples.
# Disadvantages
- **Sensitivity to Outliers:** T tests can be overly sensitive to outliers, which can skew the results.
- **Assumption of Normality:** It assumes that the data is approximately normally distributed within each group.
- **Equal Variance Assumption:** In its most common form (independent samples T test), it assumes that the two distributions have the same variance.
# Applications
- **Academic Research:** Used to compare test results, teaching methods, and other education-related metrics.
- **Business:** Helps in comparing the performance of two different teams or assessing the impact of an intervention.
- **Medicine:** Used to analyze the effectiveness of treatments, comparing two different medication or treatments.
# Code
```python
import numpy as np
from scipy import stats

# Example Data
group1 = np.random.normal(100, 10, 25) # Sample Data, group 1
group2 = np.random.normal(100, 10, 25) # Sample Data, group 2

# T-test for two independent samples
t_stat, p_val = stats.ttest_ind(group1, group2)

# Output results
print(f"T-Statistic: {t_stat:.2f}")
print(f"P-Value: {p_val:.3f}")

# Decision based on p-value
alpha = 0.06
if p_val < alpha:
	print("Reject the null hypothesis - there is a significant difference between the groups.")
else:
	print("Fail to reject the null hypothesis - no significant difference between the groups.")
```
