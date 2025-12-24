---
Status: Not started
---
If $p-value < significance \ value$﻿, we reject null hypothesis. But it does not mean that the alternative hypothesis is true.

If $p-value > significance\ value$﻿, we reject alternative hypothesis. But it does not mean null hypothesis is true.

![[Attachments/CleanShot_2024-08-24_at_11.47.532x 2.png|CleanShot_2024-08-24_at_11.47.532x 2.png]]

- **Type I Error:** It occurs when **null hypothesis** is _true_ but gets _rejected_.
- **Type II Error:** It occurs when **null hypothesis** is _false_ but gets _accepted_.

# Parametric vs. Non-Parametric Tests

## Spearman’s Rank Correlation vs Pearson Correlation

- **Why use parametric tests at all?**
    - _Parametric tests_ are generally more powerful than _non-parametric tests_!
- The **Spearman’s Rank Correlation** is the _non-parametric counterpart_ to the **Pearson Correlation**

### Spearman’s Rank Correlation

- It does not use **raw data,** but the **ranks** of the data

  

### Pearson Correlation

**Formula**

$r = \frac {\sum(x_i - \bar x)(y_i -\bar y)}{\sqrt{\sum(x_i - \bar x)^2 \sum(y_i - \bar y)^2}}$

> [!important]  
> Spearman’s Rank Correlation is equal to Pearson Correlation, only when ranks are used and not raw data  

## Mann Whitney U Test vs t-Test

- The **Mann Whitney U Test** is the _non-parametric counterpart_ to the **t-test for independent samples**.
- The t-test for independent sample tests whether there is a mean difference.
- For both samples, the **mean value** is calculated and it is tested whether these mean values differ significantly.
- The Mann Whitney U test, on the other hand, checks whether there is a rank sum difference.
- **How do we calculate the rank sum?**
    - For this purpose, we sort all persons from the smallest to the largest value


- **Nominal Data**
    - We can categorize and count response but cannot inhere any order.
- **Ordinal Data**
    - Allows us to rank responses but not to measure precise differences between ranks.
- **Metric Data**
    - Enables us to measure exact differences between data points.

# t-Test

- The t-test is a statistical test procedure
- It analyzes whether there is a significant difference between the means of two groups.
**Reference**:[[T-Test]]
## One Sample t-Test

- We use one sample t-test, when we want to compare the mean of a sample with a known reference mean.

### Null Hypothesis

- The sample mean is equal to the reference value.

### Alternative Hypothesis

- The sample mean is not equal to the reference value

## Independent Sample t-Test

- We use it when we want to compare the means of two independent groups or samples.
    - Drug test (A&B) for two different groups.

### Null Hypothesis

- The mean values in both groups are the same.

### Alternate Hypothesis

- The mean values in both groups are not the same.

## Paired Sample t-Test

- We use it to compare the means of two dependent groups.
    - E.g., Measuring weight of a person before and after diet.

### Null Hypothesis

- The mean of the difference between the pairs is zero.

### Alternate Hypothesis

- The mean of the difference between the pairs is not zero.

> [!important]  
> One-Sample t-test $\approx$﻿ Paired Sample t-Test  

## Assumptions for a t-Test

1. We need a suitable sample
2. Variables for which we want to test whether there is a difference between the means must be metric.
3. All metric variables should be normally distributed in all three t-test variants.
4. In the independent t-test, variances in between two groups must be approximately same/equal.

## Calculation for t-Test

1. Calculate t-Value (For One Sample t-Test)

$t= \frac{Difference \ between \ mean \ values}{Standard\ deviation\ from\ the \ mean/standard\ error}$

$t = \frac{\bar x - \mu}{\frac{s}{\sqrt n}}$

> [!important]  
> $\frac{s}{\sqrt n}$​﻿ ⇒ Standard Error  

1. Calculate t-Value (For Independent Sample t-Test)

$t = \frac{\bar x_1 - \bar x_2}{\sqrt{ \frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}}$

1. Calculate t-Value (For Paired t-Test Samples)

$t = \frac{\bar x_d - 0}{\frac{s}{\sqrt n}}$

> [!important]  
> The more the sample deviates from null hypothesis, the smaller the p-value becomes.  

## Degrees of Freedom

- In one-sample t-test/paired sample t-test
    
    $df = n -1$﻿
    
- In independent sample t-test
    
    $df = n_1 + n_2 - 2$﻿
    

> [!important]  
> $t > t_{crit}$​﻿, reject the null hypothesis.  

# Analysis of Variance (ANOVA)

## One-Way ANOVA

- It checks whether there are statistically significant differences between more than two groups.
- **It is an extension for the t-test for independent samples to more than two groups (without repeated measurement).**
- If we have more than two groups with dependent samples we use ANOVA (with repeated measurement)

### Null Hypothesis $(H_0)$﻿

- There are no differences in the population between the means of individual groups.

### Alternate Hypothesis $(H_1)$﻿

- At least two groups means differ from each other in the population.

**Research Question**

Is there a difference in the population between the different groups of the independent variable with respect to the dependent variable.

## Two-Way ANOVA

- Two-way ANOVA is a statistical method used to test the effect of two categorical variables (are independent variables) on a continuous variable (dependent variable).
- It takes two independent variable (called factors)
- Example
    - Gender, Education (Two independent variables/factors) → Salary (One dependent factor)
    - Gender, Therapy → Effect on blood pressure
    - University attended, field of study → Length of study
- We can answer the following questions
    - Does factor 1 have an effect on the dependent variable?
    - Does factor 2 have an effect on the dependent variable?

### Null Hypothesis

There is no significant difference between the groups of the first factor.

There is no significant difference between the groups of the second factor.

One factor has no effect on the effect of the other factor.

### Alternate Hypothesis

There is a significant difference between the groups of the first factor.

There is a significant difference between the groups of the second factor.

One factor has an influence on the effect of the other factor.

### Assumptions

For the test results to be valid, several assumptions must be met.

1. Normality
    1. The data within the groups should be normally distributed
    2. Alternatively, The residuals should be normally distributed.
    3. This can be checked with Quantile-Quantile Plot.
2. Homogeneity of Variances
    1. The variance of data in groups should be equal.
    2. We can check with ==**Levene’s test**==.
3. Independence
    1. The measurements should be independent, i.e., the measured value of one group should not be influenced by the measured value of another group.
4. Measurement Level
    1. The dependent variable should have a **metric scale level**.

  

|   |   |   |   |
|---|---|---|---|
||Drug A|Drug B||
|Male|6|4||
|Male|4|5||
|Male|7|6||
|Male|9|7||
|Male|3|5||
|**Mean**|**5.8**|**5.4**|**5.6**|
|Female|8|3||
|Female|3|5||
|Female|5|9||
|Female|8|2||
|Female|6|3||
|**Mean**|**6**|**4.4**|**5.2**|
|**Total Mean**|**5.9**|**4.9**|**5.4**|

==**Formula**==

$SS_{tot} = SS_A + SS_B + SS_{AB} + SS_{err}$

$SS_{tot}$﻿ = Total variance of the dependent variable

$SS_A$﻿ = Variance that can be explained by Factor A

$SS_B$﻿ = Variance that can be explained by Factor B

$SS_{AB}$﻿ = Variance that can be explained by the interaction of A and B

$SS_{err}$﻿ = The error variance

$SS = Sum \ of\ Squares$﻿

# Total Sum of Squares

## Formula

$SS_{tot} = \sum \sum \sum (x_{mij} - \bar G)^2$

$x_{mij}$﻿ ⇒ the values present in the table and not the mean

## Degrees of Freedom

$df_{tot} = n \ \cdot \ p \ \cdot \ q - 1$

$n$﻿ → Number of people per group

$p$﻿ → Number of groups in Factor A

$q$﻿ → Number of groups in Factor B

## Variance

$\sigma_{tot}^2 = \frac{SS_{tot}}{df_{tot}}$

# Sum of Squares between the groups

## Formula

$SS_{btw} = n \ \cdot \ \sum\sum(\overline{AB}_{ij} - {\overline G})^2$

## Degrees of Freedom

$df_{btw} = p \ \cdot \ q - 1$

## Variance

$\sigma_{btw}^2 = \frac{SS_{btw}}{df_{btw}}$

# Sum of Squares of Factor A

## Formula

$SS_A = n \cdot q \sum (\bar A_i - \bar G)^2$

$\bar A_i$﻿ ⇒ Mean value of the groups of factor A

## Degrees of Freedom

$df_A = p - 1$

## Variance

$\sigma_A^2 = \frac{SS_A}{df_A}$

# Sum of Squares of Factor B

## Formula

$SS_B = n \cdot p \sum (\bar B_i - \bar G)^2$

$\bar B_i$﻿ ⇒ Mean value of the groups of factor B

## Degrees of Freedom

$df_B = q - 1$

## Variance

$\sigma^2_B = \frac{SS_B}{df_B}$

# Sum of Squares for Interaction $(SS_{AB})$﻿

## Formula

$SS_{AB} = SS_{btw} - SS_A - SS_B$

## Degree of Freedom

$df_{AB} = (p-1) \cdot (q-1)$

## Variance

$\sigma_{AB}^2 = \frac{SS_{AB}}{df_{AB}}$

# Sum of Squares of Error $(SS_{err})$﻿

## Formula

$SS_{err} = \sum \sum \sum (x_{mij} - \overline {AB}_{ij})^2$

## Degree of Freedom

$df_{err} = (n-1) \cdot p \cdot q$

## Variance

$\sigma_{err}^2 = \frac{SS_{err}}{df_{err}}$

# F-values

$F_A = \frac{\sigma_A^2}{\sigma_{err}^2}$

$F_B = \frac{\sigma_B^2}{\sigma_{err}^2}$

$F_{AB} = \frac{\sigma_{AB}^2}{\sigma_{err}^2}$

# Repeated Measures ANOVA

## Introduction

- A repeated measures ANOVA tests whether there is a statistically significant difference between three or more dependent samples.

- What are dependent samples?
    
    In a dependent sample, the same participants are measured multiple times under different conditions or at different time points. We therefore have several measurements from each person involved.
    
    ==**EXAMPLE**==
    
    ![[Attachments/image 2.png|image 2.png]]
    

> [!important]  
> In a dependent sample, the same test units are measured several times under different conditions.  

## Purpose

- In the gym example, physical fitness is the dependent variable and time is the independent variable and time points as levels.

## Null Hypothesis

There are no differences between the dependent groups

- In our example, null hypothesis states that the training has no influence on physical fitness (i.e., physical fitness does not change over time).

## Alternate Hypothesis

There are differences between the dependent groups

- In our example, alternate hypothesis assumes that the training program does have an influence on physical fitness (i.e., physical fitness does change over time).

## Assumptions

1. Normality
    1. The dependent variable should be approximately normally distributed.
    2. Tested using QQ plot or Kolmogorov-Smirnov Test
2. Sphericity
    1. The variances of the differences between all combinations of factor levels (time points) should be the same.
    2. Tested using Mauchly’s Test of Sphericity
        1. If the result in p-value is greater than 0.05, we can assume that the variances are equal and the assumption is not violated.
        2. If the assumptions is violated, adjustments such as Greenhouse-Geisser or Huynh-Feldt can be made.

## Analysis of Variance

|   |   |   |   |   |
|---|---|---|---|---|
|**Case**|**Start**|**Middle**|**End**|**Mean**|
|1|7|9|8|8|
|2|2|3|3|2.7|
|3|5|7|6|6|
|4|6|6|4|5.3|
|5|4|7|5|5.3|
|6|7|8|4|6.3|
|7|4|6|4|4.7|
|8|5|3|7|5|
|**Mean**|**5**|**6.1**|**5.1**|**5.4**|

### Mean value of all data

$G = \frac{\sum x}{N}$

### Mean of the time points

$A_i = \frac{\sum^{Group}x}{n_{Group}}$

### Mean value of cases

$P_i = \frac{\sum^{VP}x}{p}$

### Sum of squares within subjects

$QS_{in} = \sum^{Groups} \sum^{VP} (x_{mi} - P_i)^2$

### Sum of squares treatment

$QS_{treat} = n \sum^{Groups}(A_i - G)^2$

### Sum of squares error

$QS_{error} = \sum^{Groups} \sum^{VP}(x_{mi} - A_i - P_m + G)^2$

$QS_{error} = QS_{in} -QS_{treat}$

### Mean Square of treatment

$MQ_{treat} = \frac{QS_{treat}}{df_{treat}}$

$df_{treat} = g - 1$

$MQ_{error} = \frac {QS_{error}}{df_{error}}$

$df_{error} = (n - 1) \cdot (g-1)$

g → Number of groups

n → Number of cases

  

# Mixed Model ANOVA

- A mixed model ANOVA is a **statistical method** used to analyze data that involve both **between-subjects factors** and **within subject factors**.

![[image 1.png]]

- In the above image, 18 participants are randomly divided into 3 groups (A,B,C). This is an example of **between-subjects factor**.

![[Attachments/image 2 2.png|image 2 2.png]]

- In the above image, we can see diet A has the 6 participants assigned to it at the start. Then we measure the diet from (start, 2 weeks, 4 weeks) which is known as **within-subjects factor**.

> [!important]  
> A mixed model ANOVA is also called a 2-way ANOVA with repeated measures  

## Null Hypothesis

### _Within Subject_

The mean values of the different measurement time points do not differ. (There are no significant differences between the “groups” of the within subject factor).

### _Between Subject_

The mean values of the different groups of the between subject factor do not differ.

### _Interaction_

One factor has no influence on the effect of the other factor.

## Assumptions

1. Normality
    1. Dependent variable should be normally distributed within the groups.
    2. Important when the sample size is small
    3. When the sample size is large, ANOVA is somewhat robust to violations of normality
2. Homogeneity of Variances
    1. Variances in each group should be equal.
    2. Needs to be true for both the within-subjects and between-subjects factors.
    3. **Levene’s test can be used to check the assumption**
3. Homogeneity of Covariances (Sphericity)
    1. This applies to the within-subjects factor
    2. The variances of the differences between all combinations of the different groups are equal.
    3. **These assumption can be tested using Mauchly’s test of sphericity.**
        1. When this assumption is violated, adjustments to the degrees of freedom, such as **Greenhouse-Geisser** or **Huynh-Feldt** can be used.
4. Independence of Observations
    1. The observations are independent of each other. **Fundamental assumption in ANOVA and is usually assured by the study design.**
5. No Significant Outliers
    1. Outliers can have a disproportionate effect on ANOVA, potentially leading to misleading results.

# Parametric Tests vs. Non-Parametric Tests

## Parametric Test

- Parametric tests are used when the data is normally distributed

## Non-Parametric Test

- Non-Parametric Tests are used when the data is not normally distributed

  

> [!important]  
> If possible, always use Parametric tests