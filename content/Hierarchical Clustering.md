---
Link: 
tags:
---
# Brief Introduction
Hierarchical clustering is an unsupervised learning method used to group similar data points into clusters based on their distance or similarity. Instead of choosing the number of clusters in advance, it builds a tree-like structure called a dendogram that shows how clusters merge or split at different levels. It helps identify natural groupings in data and is commonly used in pattern recognition, customer segmentation, gene analysis and image grouping.

A **dendogram** is like a family tree for clusters. It shows how individual data points or groups of data merge together. The bottom shows each data point as its own group and as we move up, similar groups are combined. The lower the merge point, the more similar the groups are. It helps us see how things are grouped step by step.
![[Pasted image 20260109101202.png]]
* At the bottom of the dendogram the points P,Q,R,S, and T are all separate.
* As we move up, the closest points are merged into a single group.
* The lines connecting the points show how they are progressively merged based on similarity
* The height at which they are connected shows how similar the points are to each other; the shorter the line the more similar they are.
## Distance Metrics in Hierarchical Clustering
* Minimum Distance
* Maximum Distance
* Group Average
* Ward's Method
## Applications of Hierarchical Clustering
* Portfolio Construction & Optimization
* Sector and Industry Analysis
* Pairs Trading Strategies
* Market Structure Understanding
* Dynamic Asset Allocation
* Algorithmic Trading
* Behavioral Finance Analysis
## Example
Imagine we have four fruits with different weights: an apple (100g), a banana (120g), a cherry (50g) and a grape (30g). Hierarchical clustering starts by treating each fruit as its own group.
* Start with each fruit as its own cluster.
* Merge the closest items: grape (30g) and cherry (50g) are grouped first
* Next, apple (100g) and banana (120g) are grouped.
* Finally, these two clusters merge into one.
Finally all the fruits are merged into one large group, showing how hierarchical clustering progressively combines the most similar data points.
## Types of Hierarchical Clustering
1. [[Hierarchical Agglomerative Clustering (HAC)]]
2. [[Hierarchical Divisive Clustering (HDC)]]
## Computing Distance Matrix
- While merging two clusters we check the distance between two every pair of clusters and merge the pair with the least distance/most similarity.
- There are different ways of defining Inter Cluster distance/similarity. Some of them are:
	- **Min Distance**
		- Find the minimum distance between any two points of the cluster.
	- **Max Distance**
		- 
	- **Group Average**
		- 
	- **Ward's Method**
		- 

# References
---
1. 
