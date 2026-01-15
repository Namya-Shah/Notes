---
Link: 
tags:
  - Decision-Tree
  - Random-Forest
  - Logistic-Regression
  - Linear-Regression
  - SVM
  - Gradient-Boosting
  - Supervised-Learning
  - Unsupervised-Learning
  - Book-Note
Links:
  - "[[Decision Tree]]"
---
```table-of-contents
```
# Introduction
- Machine learning has been around for decades in some specialized applications, such as *Optical Character Recognition (OCR)*. But the first ML application that really became mainstream, improving the lives of hundreds of millions of people, took over the world back in the 1900s: it was the spam filter.
> Machine Learning is the science (and art) of programming computers so they can *learn from data* 

![[Pasted image 20240906110714.png]]
> [!NOTE] Definition
> The examples that the system uses to learn are called the **training set**. Each training example is called a **training instance (or sample)**.

![[Pasted image 20240906110747.png]]
*Example for training set*
- In this case, the task T is to flag spam for new emails, the experience E is the *training data*, and the performance measure P needs to be defined; for example, you can use the ratio of correctly classified emails. This particular performance measure is called *accuracy* and it is often used in classification tasks.

> [!NOTE] Definition
> Applying ML techniques to dig into large amounts of data can help discover patterns that were not immediately apparent. This is called **data mining**.

![[Pasted image 20240906110629.png]]
# Importance of Machine Learning
Machine Learning is great for:
- Problems for which existing solutions require a lot of hand-tuning or long lists of rules: one Machine Learning algorithm can often simplify code and perform better.
- Complex problems for which there is no good solution at all using a traditional approach: the best Machine Learning techniques can find a solution.
- Fluctuating environments: a Machine Learning system can adapt to new data.
- Getting insights about complex problems and large amounts of data.

# Types of Machine Learning Systems
- Whether or not they are trained with human supervision (supervised, unsupervised, semisupervised, and Reinforcement Learning)
- Whether or not they can learn incrementally on the fly (online versus batch learning)
- Whether they work by simply comparing new data points to known data points, or instead detect patterns in the training data and build a predictive model, much like scientists do (instance-based versus model-based learning)

## Supervised Learning
- In *supervised* learning, the training data you feed to the algorithm includes the desired solutions, called ***labels***.
![[Pasted image 20240906110830.png]]
- A typical supervised learning task is ***classification***
- Another typical task is to predict a *target* numeric value, such as the price of a car, given a set of *features* (mileage, age, brand, etc.) called *predictors*. This sort of task is called *regression*. To train the system, you need to give it many examples of cars, including both their predictors and their labels (i.e., their prices).
> [!IMPORTANT] IMPORTANT
>In Machine Learning an *attribute* is a data type (e.g., "Mileage"), while a *feature* has several meanings depending on the context, but generally means an attribute plus its value (e.g., "Mileage = 15,000").

![[Pasted image 20240906111212.png]]
> [!NOTE] ABOUT REGRESSION ALGORITHMS
> Some regression algorithms can be used for classification as well, and vice versa. For example, ***Logistic Regression*** is commonly used for classification, as it can output a value that corresponds to the probability of belonging to a given class (e.g., 20% chance of being spam).

***Most Important Supervised Learning Algorithms:***
- [[K-Nearest Neighbors]]
- [[01 Notes/Attachment Notes/Linear Regression]]
- [[Logistic Regression]]
- [[Support Vector Machines]]
- [[Decision Tree]]
- [[Random Forest]]
- [[Neural Networks (Deep Learning)]]
## Unsupervised Learning
- In *unsupervised learning*, as you might guess, the training data is unlabeled. **The system tries to learn without a teacher.**
***Some Important Unsupervised Learning Algorithms:***
- *Clustering*
	- [[K-Means Clustering]]
	- [[DBSCAN]]
	- [[Hierarchical Agglomerative Clustering (HAC)]]
- *Anomaly detection and novelty detection*
	- [[One-Class SVM]]
	- [[Isolation Forest]]
- *Visualization and dimensionality reduction*
	- [[Principal Component Analysis (PCA)]]
	- [[Kernel PCA]]
	- [[Locally Linear Embedding]]
	- [[t-distributed Stochastic Neighbor Embedding (t-SNE)]]
- *Association rule learning*
	- [[Apriori]]
	- [[Eclat]]
*Example:*
- We have a lot of data about our blog's visitors. You may want to run *clustering* algorithm to try detect groups of similar visitors. At no point do you tell the algorithm which group a visitor belongs to: it finds those connections without your help. For example, it might you notice that 40% of your visitors are males who love comic books and generally read your blog in the evening, while 20% are young sci-fi lovers who visit during the weekends, and so on. If you use a *hierarchical clustering algorithm*, it may also subdivide each group into smaller groups. This may help you target your posts for each group.
![[Pasted image 20240906121147.png]]
- *Visualization* algorithms are also good examples of unsupervised learning algorithms: you feed them a lot of complex and unlabeled data, and they output a 2D or 3D representation of your data that can easily be plotted. These algorithms try to preserve as much structure as they can (e.g., trying to keep separate clusters in the input space from overlapping in the visualization), so you can understand how the data is organized and perhaps identify unsuspected patterns.
![[Pasted image 20240906121403.png]]
- A related task is *dimensionality reduction*, in which the goal is to simplify the data without losing too much information. One way to do this is to merge several correlated features into one. For example, a car's mileage may be very correlated with its age, so the dimensionality reduction algorithm will merge them into one feature that represents the car's wear and tear. This is called *feature extraction*.
### Important Code - Split Train Test
```python
def split_train_test(data, test_ratio):
	shuffled_indices = np.random.permutation(len(data))
	test_set_size = int(len(data) * test_ratio)
	test_indices = shuffled_indices[:test_set_size]
	train_indices = shuffled_indices[test_set_size:]
	return data.iloc[train_indices], data.iloc[test_indices]
```
The `split_train_test` function is used to split a dataset into a training set and a test set. Here's a breakdown of how it works:

2. **Input Parameters:**
   - `data`: The dataset, typically a pandas DataFrame, that you want to split into training and test sets.
   - `test_ratio`: The proportion of the data that should be allocated to the test set (e.g., if `test_ratio` is 0.2, 20% of the data will go to the test set).

3. **Process:**
   - `np.random.permutation(len(data))`: This generates a randomly shuffled array of indices from 0 to the length of the dataset.
   - `test_set_size = int(len(data) * test_ratio)`: This calculates how many data points will go into the test set, based on the total dataset size and the specified `test_ratio`.
   - `test_indices = shuffled_indices[:test_set_size]`: This selects the first `test_set_size` shuffled indices for the test set.
   - `train_indices = shuffled_indices[test_set_size:]`: The remaining indices are assigned to the training set.

4. **Output:**
   - The function returns two subsets of the dataset: 
     - `data.iloc[train_indices]`: The training set, containing the data points not assigned to the test set.
     - `data.iloc[test_indices]`: The test set, containing the data points selected based on the shuffled indices.

In summary, this function takes a dataset and splits it into training and test sets randomly, based on the ratio you specify for the test set.
# Poor Quality Data
- If your training data is full of errors, outliers, and noise (e.g., due to poor quality measurements), it will make it harder for the system to detect the underlying patterns, so your system is less likely to perform well. It is often well worth the effort to spend time cleaning up your training data.
	- If some instances are clearly outliers, it may help to simply discard them or try to fix the errors manually.
	- If some instances are missing a few features (e.g., 5% of your customers did not specify their age), you must decide whether you want to ignore this attribute altogether, ignore these instances, fill in the missing values (e.g., with the median age), or train one model with the feature and one model without it, and so on.
# Key Differences between **Manhattan Distance** and **Euclidean Distance** Norms
> **Norm:** 
- **$\ell_1$ norm (Manhattan Distance)**: Measures how far apart points are if you can only move in straight lines along the x and y axes. It sums the absolute differences and is less sensitive to large errors because it doesn't square the differences.
- **$\ell_2$ norm (Eucledian Distance)**: Measures the shortest straight-line distance between points by squaring and summing the differences. It's more sensitive to large errors because of the squaring.
# Decision Tree
**Reference**: [[Decision Tree]]
- *Decision Trees* are versatile Machine Learning algorithms that can perform both **classification** and **regression** tasks, and even **multioutput** tasks.
>[!NOTE] NOTE
>Decision Trees are also fundamental components of Random Forests.

>[!IMPORTANT] IMPORTANT
>They require very little data preparation and don't require feature scaling or centering at all.

- A node's `gini` attribute measures its *impurities*: a node is **"pure"** `(gini=0)` if all training instances it applies to belong to the same class.
## Gini Impurity

$$
G_i = 1 - \sum^n_{k=1} p_{i,k}^2
$$

- $p_{i,k}$ is the ratio of class $k$ instances among the training instances in the i$^{th}$ node.
> [!NOTE] NOTE
> Scikit-Learn uses the **CART** algorithm, which produces only *binary trees*: nonleaf nodes always have two children (i.e., questions only have yes/no answers). However other algorithms such as **ID3** can produce Decision Trees with nodes that have more than two children.
- ![[CleanShot 2025-02-06 at 08.55.12@2x.png]]
- ![[CleanShot 2025-02-06 at 08.52.18@2x.png]]
- `Figure 6-2` shows this Decision Trees' decision boundaries. The **thick vertical line** represents the decision boundary of the root node (depth 0): petal length = 2.45 cm.
- Since the left area is pure (only *Iris-Setosa*), it cannot be split any further.
- However, the right area is impure, so the `depth-1` right node splits it at petal width = 1.75 cm (represented by dashed line). Since `max_depth` was set to 2, the Decision Tree stops right there. However, if you set `max_depth` to 3, then the two depth - 2 nodes would each add another decision boundary (represented by dotted lines).
> [!IMPORTANT] IMPORTANT
> **Decision Trees** are fairly intuitive and their decisions are easy to interpret. Such models are often called *white box models*.
> In contrast, **Random Forests** or **Neural Networks** are generally considered *black box models*.
- Decision Trees have *simple classification rules* that can even be applied manually if need be.
### Gini Impurity or Entropy
- By default, **Gini impurity** is used.
- We can use *entropy* impurity by setting `criterion='entropy'`.
- Entropy in Machine Learning is frequently used as an impurity measure: a set's entropy is zero when it contains instances of only one class.
- **Gini impurity** is slightly faster to compute, so it is a good default. However, when they differ, **Gini impurity** tends to isolate the most frequent class in its own branch of the tree, while **entropy** tends to produce slightly more balanced trees.
## Estimating Class Probabilities
A Decision Tree can also estimate the probability that an instance belongs to a particular class $k$: first it traverses the tree to find the leaf node for this instance, and then it returns the ratio of training instances of class $k$ in this node.
- We use `tree_clf.predict_proba` to predict the probabilities of the classes.
## The CART Training Algorithm
- CART -> **Classification And Regression Tree**
- Decision Trees -> "**growing**" trees
- The algorithm first splits the training set in two subsets using a single feature $k$ and a threshold $t_k$ (e.g., "petal length $\le$ 2.45 cm").
- **How does it choose $k$ and $t_k$?**
	- It searches for the pair ($k$,$t_k$) that produces the purest subsets (weighted by their size). The cost function that the algorithm tries to minimize is given by

	$$
	J(k,t_k) = \frac{m_{\text{left}}}{m}G_{\text{left}} + \frac{m_{\text{right}}}{m}G_{\text{right}}
	$$

	Where,
		$G_{\text{left/right}}$ measures the impurity of the left/right subset,
		$m_{\text{left/right}}$ is the number of instances in the left/right subset.
- **CART** algorithm is a *greedy algorithm*: it greedily searches for an optimum split at the top level, then repeats the process at each level. It does not check whether or not the split will lead to the lowest possible impurity several levels down.
- **A greedy algorithm often produces a reasonably good solution, but it is not guaranteed to be the optimal solution.**
- ? Finding the optimal tree is known to be an *NP-Complete* problem: it requires $O(exp(m))$ time, making the problem intractable even for fairly small training sets. This is why we must settle for a "reasonably good" solution.
- Decision Tree requires going through roughly $O(\log_2(m))$ nodes. Since each node only requires checking the value of one feature, the overall prediction complexity is just $O(\log_2(m))$, independent of the number of features. Due to which the predictions are very fast even when dealing with large datasets.
- The training algorithm compares all features (or less if `max_features` is set) on all samples at each node. This results in a training complexity of $O(n \times m \log(m))$. For small training sets, Scikit-Learn can speed up training by presorting the data (set `presort = True`), but this slows down training considerably for larger training sets.
# Regularization Hyperparameters
- If Decision Trees are left unconstrained, the tree structure will adapt itself to the training data, fitting it very closely, and most likely overfitting it. Such a model is often called **nonparametric model**.
	- Not because it does not have any parameters (it often has a lot) but because the number of parameters is not determined prior to training, so the model structure is free to stick closely to the data.
- A **parametric model** such as a linear model has a predetermined number of parameters, so its degree of freedom is limited, reducing the risk of overfitting (but increasing the risk of underfitting).
- To avoid overfitting the training data, you need to restrict the Decision Tree's freedom during training. This is called **regularization**.
- The regularization hyperparameters depend on the algorithm used, but generally you can at least restrict the maximum depth of the Decision Tree.
- In Scikit-Learn, this is controlled by the `max_depth` hyperparameter (the default value is `None`, which means unlimited). Reducing `max_depth` will regularize the model and thus reduce the risk of overfitting.
- The `DecisionTreeClassifier` class has a few other parameters that similarly restrict the shape of the Decision Tree: `min_samples_split` (the minimum number of samples a node must have before it can be split), `min_samples_leaf` (the minimum number of samples a leaf node must have), `min_weight_fraction_leaf` (same as `min_samples_leaf` but expressed as a fraction of the total number of weighted instances), `max_leaf_nodes` (maximum number of leaf nodes), and `max_features` (maximum number of features that are evaluated for splitting at each node).
- **Increasing `min_*` hyperparameters** or **reducing `max_*` hyperparameters will regularize the model**.
- Other algorithms work by first training the Decision Tree without restrictions, then *pruning* (deleting) unnecessary nodes. A node whose children are all leaf nodes is considered unnecessary if the purity improvement it provides is not *statistically significant*.
- Standard statistical tests, such as the $\chi^2 \ test$, are used to estimate the probability that the improvement is purely the result of chance (which is called the *null hypothesis*). If this probability, called the *p-value*, is higher than a given threshold (typically 5%, controlled by a hyperparameter), then the node is considered unnecessary and its children are deleted. The pruning continues until all unnecessary nodes have been pruned.
---
- [ ] #todo Learn about NP problems
- [ ] 