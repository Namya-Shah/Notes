**Use Case:** Classification and regression tasks in various domains, including healthcare for disease diagnosis and fraud detection in finance.
# Overview
- In simple words, a *decision tree* is a structure that contains nodes (rectangular boxes) and edges (arrows) and is built from a dataset (table of columns representing features/attributes and rows corresponds to records).
- Decision Tree algorithm belongs to the family of **supervised learning** algorithms.
- The **general motive** of using Decision Tree is to create a training model which can use to predict class or value of target variables by **learning decision rules**.
- Each node is either used to *make a decision* (known as **decision node**) or *represent an outcome* (known as **leaf node**).
- **Decision trees** are powerful for both classification and regression tasks. They are intuitive and easy to interpret.
- Constructs a tree-like model by splitting data based on features to make decisions or predictions.
# Assumptions
- At the beginning, the whole training set is considered as the **root**.
- Feature values are preferred to be categorical. If the values are continuous then they are discretized prior to building the model.
- Records are **distributed recursively** on the basis of attribute values.
- Order to placing attributes as root or internal node of the tree is done by using some statistical approach.
# Sum of Product (SOP)
> The Sum of Product (SOP) is also known as **Disjunctive Normal Form**.
- For a class, every branch from the root of the tree to a leaf node having the same class is a conjunction(product) of values, different branches ending in that class form a disjunction(sum).
# Attributes Selection
- If dataset contains "**n**" attributes then deciding which attribute to place at the root or at different levels of the tree as internal nodes is a complicated step. By just randomly selecting any node to be the root can't solve the issue. If we follow a random approach, it may give us bad results with low accuracy.
- For solving this attribute selection problem, researchers worked and devised some solutions. They suggested using some *criterion* like **information gain**, **gini index** etc. These criterions will calculate values for every attribute. The values are sorted, and attributes are placed in the tree by following the order i.e., the attribute with a high value (in case of information gain) is placed at the root.
- While using information gain as a criterion, we assume attributes to be categorical, and for gini index, attributes are assumed to be continuous.
# Nodes
- The *initial node* is called the **root node**, the *final nodes* are called the **leaf nodes** and the rest of the nodes are called **intermediate or internal nodes**.
- *The root and intermediate nodes represent the decisions while the leaf nodes represent the outcomes.*
# Learning Objectives
- Learn how decision trees are built, including the concepts of entropy and information gain.
- Implement a decision tree on a classification problem.
# Practice Questions
1. Create a decision tree to predict customer churn.
2. How do decision trees handle overfitting?
![[decisiontreeclassifier.png]]
- Decision trees are the basis of a number of more complex supervised learning algorithms.
- In its simplest form, a decision tree is basically a series of yes/no questions that allow us to partition a data set in several dimensions.
![[decisiontree.png]]
- The goal of the decision tree algorithm is to create so-called leaf nodes at the bottom of the tree.