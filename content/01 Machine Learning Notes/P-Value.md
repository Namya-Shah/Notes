- The P-value, or probability value, is a statistical measure that helps scientists and researchers determine the significance of their experimental results.
- It represents the probability of obtaining test results at least as extreme as the results actually observed, under the assumptions that the null hypothesis is correct.
- A low p-value (typically $\leq$ 0.05) indicates strong evidence against the null hypothesis, so it is rejected. Conversely, a high P-value suggests that the observed data is consistent with the null hypothesis.
# When to use p-value?
- p-values are used in various statistical tests, including t-tests, chi-square tests, and ANOVA, to:
	- Determine the significance of results from experiments and studies
	- Make informed decisions in hypothesis testing when comparing datasets
	- Evaluate the strength of evidence against a null hypothesis in scientific research
# Why to use p-value?
- Using p-value in statistical analysis helps researchers:
	- Quantify the evidence against a null hypothesis, providing a measure for the strength of the results.
	- Make objective decisions in hypothesis testing, reducing personal bias in interpreting data.
	- Communicate the statistical significance of results in a university understood metric.
# Advantages
- **Quantitative Measure**: Offers a precise, quantitative way to assess the strength of the experimental results.
- **Widely Accepted**: Commonly used and accepted in many scientific fields for hypothesis testing
- **Objective**: Provides an objective criterion for making decisions about the hypothesis
# Disadvantages
- **Misinterpretation**: Can be easily misinterpreted as a measure of the probability that the hypothesis is true or false.
- **Not a Measure of Effect Size**: Does not provide information about the size of the effect or the importance of a result.
# Python Code
```python
import numpy as np
from scipy import stats

# Sample Data
data = np.random.normal(loc=0, scale=1, size=30)

# Perform a one-sample t-test
t_stat, p_value = stats.ttest_1samp(data, popmean=0)

# Print the results
print("T-statistic:", t_stat)
print("P-value:", p_value)
```