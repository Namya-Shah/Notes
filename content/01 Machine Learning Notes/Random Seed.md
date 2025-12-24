---
Link: 
tags:
  - ML
---
# Notes
[How to use Random Seeds Effectively - Towards Data Science](https://towardsdatascience.com/how-to-use-random-seeds-effectively-54a4cd855a79#:~:text=A%20random%20seed%20is%20used,data%20science%20and%20other%20fields.)
```table-of-contents
```
# Introduction
- Random seed acts like the initial points or starting point of an algorithm.
- We can control the process of generating random integer numbers and so we can see that it is not totally random. So it is called pseudo random number generation and not totally! Because they're not totally random. And we can control it.
# Difference between Numpy and Random module?
```python
import numpy as np
np.random.seed(0) # To sustain the randomness
np.random.randint(1,6,size=2)
```
- In NumPy, the second integer is non-inclusive.
```python
import random
random.seed(0)
x = []
for i in range(2):
	a = random.randint(1,6)
	x.append(a)
print(a)
```
- In Random module, the second integer is inclusive
> Both of the above example will have different output. For Numpy module, it will be different than the Random module.
# What is a Random Seed?
- A random seed is used to ensure that results are producible.
- *In other words, using the parameter makes sure that anyone who re-runs your code will get the exact same outputs.*
- Reproducibility is an extremely important concept in data science and other fields.
- Depending on your specific project, you may not even need a random seed.
- However, there are 2 common tasks where they are used:
	1. Splitting data into training/validation/test sets: random seeds ensure that the data is divided the same way every time the code is run
	2. Model training: algorithms such as random forest and gradient boosting are non-deterministic (for a given input, the output is not always the same) and so require a random seed argument for reproducible results.
> **In addition to reproducibility, random seeds are also important for benchmarking results. If you are testing multiple versions of an algorithm, it's important that all versions use the same data and are as similar as possible (except for the parameters you are testing).**
- When modelling, we want our training, validation, and test data to be as similar as possible so that our model is trained on the same kind of data that it's being evaluated against. Note that this does **not** mean that any of these 3 data sets should overlap! They should not. But we want the observations contained in each of them to be broadly comparable.
## Cons of Random Seed
- First, in both cases, the survival distribution is substantially different between the training and validation sets. This will likely negatively affect model training.
- Second, these outputs are very different from each other. If, as most people do, you set a random seed arbitrarily, your resulting data splits can vary drastically depending on your choice.
### How to convert categorical data into dummy/indicator variables
- `pandas.get_dummies` is used to convert categorical variable into dummy/indicator variables. 
- Each variable is converted in as many 0/1 variables as there are different values. Columns in the output are each named after a value; if the input is a DataFrame, the name of the original variable is prepended to the value.
> **Model performance variance due to random seed choice should be taken into account when communicating results with stakeholders.**
## Best Practices for Random Seed
- For data splitting, stratified samples should be used so that the proportions of the dependent variable are similar in the training, validation, and test sets. This would eliminate the varying survival distributions above and allows a model be trained and evaluated on comparable data.
- The `train_test_split` function can implement stratified sampling with 1 additional argument. Note that if a model is later evaluated against data with a different dependent variable distribution, performance may be different than expected.
- Using the `stratify` argument, the proportion of objects is similar in the training and validation sets. We use a random seed as we still want reproducible results.
- **For model training**
	- While testing different model specifications, a random seed should be used for fair comparisons but I don't think the particular seed matters too much.
	- However, before reporting performance metrics to stakeholders, the final model should be trained and evaluated with 2-3 additional seeds to understand possible variance in results. This practice allows more accurate communication of model performance. For a critical model running in a production environment, it's worth considering running that model with multiple seeds and averaging the result.


# References
---
1. 
