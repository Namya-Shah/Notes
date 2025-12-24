- The algorithm iteratively (repeatedly) dichotomizes (divides) features into two or more groups at each step.
- Developed by **Ross Quinlan** (*1980s*)
- ID3 remains a fundamental algorithm formula
- *ID3 uses a **top-down greedy approach** to build a decision tree.*
	- In simple words, *top-down greedy approach* means that we start building the tree from the top and the greedy approach means that at each iteration we select the best feature at the present moment to create a node.
- *==Most generally ID3 is only used for classification problems with nominal features only.==*
- Decision Trees divide the input data recursively according to features to arrive at a decision.
- Every internal node symbolizes a feature, and every branch denotes a potential result of that feature.
- Every leaf node makes a judgement call or forecast
- **To optimize information acquisition or limit impurity, the best feature is chosen at each stage of creation**
- Overfitting can be avoided by [[pruning]]
- *Decision trees mimic human decision-making processes by recursively splitting data based on different attributes to create a flowchart-like structure for classification or regression.*
- ***The goal is to make the final subsets as homogeneous as possible. By choosing features that offer the greatest reduction in entropy or uncertainty, ID3 iteratively grows the tree.***
- The procedure keeps going until a **halting requirement** is satisfied, like *minimum subset size or maximum tree depth*.
# How ID3 Works
- Objective is to explain the relationship between attributes in the data and their corresponding class variables
## Selecting the Best Attribute
- Entropy and Information Gain to determine the attribute that best separates the data.
- **Entropy measures the impurity or randomness in the dataset.**
- Algorithm -> Entropy of each attribute -> selects the most significant information gain
## Creating Tree Nodes
- The chosen attribute is used to split the dataset into subsets based on its distinct values.
- For each subset, ID3 recurses to find the next best attribute to further partition the data, forming branches and new nodes accordingly.
## Stopping Criteria
- Recursion continues till one of the stopping criteria is met
	- When all instances in a branch belong to the same class
	- When all attributes have been used for splitting
## Handling Missing Values
- Uses strategies to handle missing attributes
	- **Strategy 1:** Mean/Mode Substitution
	- **Strategy 2:** Majority Class Values
## Tree Pruning
- [[pruning]] is a technique to prevent overfitting
# Mathematical Concepts
## 1. Entropy
- A measure of disorder or uncertainty in a set of data is called *entropy*.
- Entropy of a dataset is the measure of disorder in the target feature of the dataset.
- ***Entropy is calculated for the target column.***
- Used to measure a dataset's disorder or impurity.
- **Objective is to *minimize* entropy**
- ### Mathematical Equations

$$
H(S) = \sum^n_{i=1} p_i * log_2(p_i)
$$

## 2. Information Gain
- A measure of how well a certain quality reduces uncertainty is called *information gain*.
- It calculates the reduction in the entropy and measures how well a given feature separates or classifies the target classes. The feature with the **highest Information Gain** is selected as the *best* one.
- **Objective is to *maximize* information gain**
- Information Gain measures the effectiveness of an attribute $A$ in reducing uncertainty in set $S$.
- ### Mathematical Formula

$$
IG(A, S) = H(S) - \sum_{v \in values(A)} \frac{|S_v|}{|S|} \ \cdot H(S_v)
$$

	- Where, $|S_v|$ is the size of the subset of $S$ for which attribute $A$ has value $v$.
## 3. Gain Ratio
- Gain Ratio is an improvement on Information Gain that considers the inherent worth of characteristics that have a wide range of possible values.
- ### Mathematical Formula

$$
GR(A, S) = \frac{IG(A, S)}{\sum_{v \in values(A)} \frac{|S_v|}{S} \cdot log_2(\frac{|S_v|}{|S|})}
$$

# Steps
1. Calculate the Information Gain of each feature
2. Considering that all rows don't belong to the same class, split the dataset S into subsets using the feature for which the ***Information Gain*** is *maximum*.
3. Make a decision tree node using the feature with the maximum Information Gain.
4. If all rows belong to the same class, make the current node as a leaf node with the class as its label.
5. Repeat for the remaining features until we run out of all features, or the decision tree has all leaf nodes.
# Python Formula
```python
[from collections import Counter
import numpy as np](<from collections import Counter
import numpy as np

# collections for the Counter class to count occurences
# numpy for the numerical operations and array handling

class Node:
    def __init__(self, feature=None, value=None, results=None, true_branch=None, false_branch=None):
        """
        # The feature attribute signifies the feature used for splitting, while value stores the specific value of that feature for the split.
        # In case of a leaf node, results holds class labels.
        # The node also has branches, with true_branch and false_branch representing the branches for values that are True and False for the feature, respectively.
        """
        self.feature = feature # Feature to split on
        self.value = value # Value of the feature to split on
        self.results = results # Stores class labels if node is a leaf node
        self.true_branch = true_branch # Branch for values that are True for the feature
        self.false_branch = false_branch # Branch for values that are False for the feature

    def entropy(data):
        """
        # The entropy function calculates the entropy of the given dataset.
        # The function first counts the number of occurrences of each class label in the dataset using `np.bincount`.
        # It then calculates the probability of each class label by dividing the counts by the total number of data points.
        # The entropy is calculated using the formula: -p*log2(p) for each class label, where p is the probability of the class label.
        # The entropy is the sum of these values.
        """
        counts = np.bincount(data)
        probabilities = counts / len(data)
        entropy = -np.sum([p*np.log2(p) for p in probabilities if p %3E 0])
        return entropy
    
    def split_data(X, y, feature, value):
        """
        # The split_data function splits the dataset based on the given feature and value.
        # It returns two subsets of the dataset: one where the feature value is less than or equal to the given value, and the other where the feature value is greater than the given value.
        # The function uses numpy to filter the rows based on the feature and value.
        # It returns the subsets of the dataset as numpy arrays.
        # The function is used to split the dataset at each node of the decision tree.
        """
        true_indices = np.where(X[:, feature] %3C= value)[0]
        false_indices = np.where(X[:, feature] > value)[0]
        true_X, true_y = X[true_indices], y[true_indices]
        false_X, false_y = X[false_indices], y[false_indices]
        return true_X, true_y, false_X, false_y
    
    def build_tree(X, y):
        """
        # The build_tree function builds the decision tree using the ID3 algorithm.
        # Checks if the labels in the current subset are homogeneous. If so, it creates a leaf node with the corresponding class label.
        # Otherwise, it iterates through all the features and values, calculating the information gain for each split and identifying the one with the highest gain.
        # The function then recursively calls itself on the subsets created by the best split.
        # The function returns the root node of the decision tree.
        # The process continues until no further splits are possible, resulting in leaf nodes with class labels.
        """
        if len(set(y)) == 1:
            return Node(results=y[0])
        
        best_gain = 0
        best_criteria = None
        best_sets = None
        n_features = X.shape[1]
        
        current_entropy = entropy(y)
        
        for feature in range(n_features):
            feature_values = set(X[:, feature])
            for value in feature_values:
                true_X, true_y, false_X, false_y = split_data(X, y, feature, value)
                true_entropy = entropy(true_y)
                false_entropy = entropy(false_y)
                p = len(true_y) / len(y)
                gain = current_entropy - p * true_entropy - (1 - p) * false_entropy
                if gain > best_gain:
                    best_gain = gain
                    best_criteria = (feature, value)
                    best_sets = (true_X, true_y, false_X, false_y)
                
        if best_gain > 0:
            true_branch = build_tree(best_sets[0], best_sets[1])
            false_branch = build_tree(best_sets[2], best_sets[3])
            return Node(feature=best_criteria[0], value=best_criteria[1], true_branch=true_branch, false_branch=false_branch)
        return Node(results=y[0])
    
    def predict(tree, sample):
        """
        # The predict function predicts the class label for a given sample using the decision tree.
        # It recursively traverses the tree based on the feature values of the sample until it reaches a leaf node.
        # If it is a leaf, it returns the class labels.
        # Otherwise, it determines the next branch to traverse based on the feature value of the sample compared to the node's splitting criteria.
        # The function then calls itself with the appropriate branch until a leaf node is reached, providing the final predicted class labels for the input sample.
        """
        if tree.results is not None:
            return tree.results
        else:
            branch = tree.false_branch
            if sample[tree.feature] <= tree.value:
                branch = tree.true_branch
            return predict(branch, sample)
        

    X = np.array([[1,1],[1,0],[0,1],[0,0]])
    y = np.array([1,1,0,0])

    # Building the tree
    decision_tree = build_tree(X,y)

    sample = np.array([1,0])
    prediction = predict(decision_tree, sample)
    print(f"Prediction for sample {sample}: {prediction}")
```


---

# Questions
- [ ] 