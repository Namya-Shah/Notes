---
Link: https://colab.research.google.com/drive/1pdPGOi-C5i0eUZO8HpnTnnzBRIsSsUKV?authuser=0#scrollTo=40DJulw1VZ2K
tags:
  - ID3
  - ML
  - CART
---
# Notes
- **ID3 (Iterative Dichotomiser 3)** uses Information Gain and entropy for splitting criteria, works with categorical features, and builds a multi-way tree. *It doesn't handle continuous data or regression tasks.*
- **CART (Classification And Regression Trees)** uses Gini Impurity for classification and can handle both classification and regression by supporting continuous features through binary splits. CART also does binary splits, which can lead to deeper trees, and it's the basis for algorithms like Random Forests.
## Differences
#### Splitting Criteria
- ID3 uses **Information Gain** (based on entropy)
- CART uses **Gini Impurity**
#### Split Type
- ID3 makes **multi-way splits** (one branch per feature value)
- CART makes **binary splits** (true/false divisions)
#### Feature Handling
- ID3 works only with **categorical features**
- CART handles both **categorical and numerical features**
#### Tree Structure
- ID3 trees tend to be **wider and shallower**
- CART trees tend to be **deeper with binary decisions**
#### Applications
- ID3 is **classification-only**
- CART supports **both classification and regression**
## When to use which
- **Use ID3 When**:
	- All features are categorical
	- You want simple, interpretable multi-way splits
	- Dealing with small datasets with clear categorical boundaries
- **Use CART when**:
	- You have mixed data types (categorical + numerical)
	- Need binary splits for better generalization
	- Want to support regression tasks
	- Planning to use ensemble methods (like Random Forests)

# References
---
2. [[Iterative Dichotomiser 3 (ID3) Algorithm]]
3. [[Hands on Machine Learning with Scikit-learn, Keras and Tensorflow#Decision Tree#The CART Training Algorithm]]
4. 
