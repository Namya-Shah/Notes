---
Link: 
tags:
  - EM614
---
# Notes

|                         | Z Test                        | T Test                   |
| ----------------------- | ----------------------------- | ------------------------ |
| **population variance** | is known                      | is unknown               |
| **distribution**        | normal distribution           | t-distribution           |
| **degrees of freedom**  | don't need                    | are needed               |
| **calculated with**     | standard error                | estimated standard error |
| **proportion testing**  | when np > 10, and n(1-p) > 10 | is not used for this     |
# Definition
## Z-Test
- It uses a normal distribution to determine whether two population means are different when the variances are known and the sample size is large. It is often used for hypothesis testing in large samples.
## T-Test
- This test also compares two means, but it is used when the variance are unknown and the sample size is small. It relies on the t-distribution, which adjusts itself for the size of the sample.
# Conditions of Use
## Z-Test
- Known population variance
- Large sample size (typically over 30)
- The sample distribution should be approximately normal
## T-Test
- Unknown population variance
- Small sample size (typically less than 30)
- The sample distribution does not need to be perfectly normal, especially for larger sample sizes.
# Distribution
## Z-Test
- Assumes that the sample distribution approximates a normal distribution as sample size increases, due to the [[Central Limit Theorem]].
## T-Test
- Uses the t-distribution, which is more spread out and has thicker tails than the normal distribution. This accounts for the extra uncertainty that comes with smaller sample sizes and unknown variances.
# Examples of Application
## Z-Test
- Testing whether the average height in a population of thousands is greater than 170 cm, assuming population variance is known.
- Comparing the proportion of voters favoring one candidate over another in large pre-election surveys.
## T-Test
- Comparing the mean scores of two classes of students on a standardized test where the number of students in each class is less than 30.
- Testing the mean amount of a chemical in a batch of a product against the standard when the variance is not known.
# When to Use Each Test
## Z-Test
- Use when you have a large sample size and know the population variance. This situation is less common in practice unless you have historical data or controlled conditions where variance is known.
## T-Test
- More commonly used in typical scenarios where the population variance is unknown and the sample size is smaller. It is versatile for testing differences in means under most practical conditions.
