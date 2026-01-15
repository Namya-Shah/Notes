---
Link:
tags:
  - ML
  - Unsupervised-Learning
---
# Brief Introduction
Divisive clustering is also known as top-down approach. Top-down clustering requires a method for splitting a cluster that contains the whole data and proceeds by splitting clusters recursively until individual data have been split into singleton clusters.
## Workflow
1. **Start with all data points in one cluster**: Treat the entire dataset as a single large cluster.
2. **Split the cluster**: Divide the cluster into two smaller clusters. The division is typically done by finding the two most dissimilar points in the cluster and using them to separate the data into two parts.
3. **Repeat the process**: For each of the new clusters, repeat the splitting process: Choose the cluster with the most dissimilar points and split it again into two smaller clusters.
4. **Stop when each data point is in its own cluster**: Continue this process until every data point is its own cluster or the stopping condition (such as a predefined number of clusters) is met.
## Implementation
- Starts with all data points as one big cluster
- Finds the largest cluster and splits it into two using KMeans
- Repeats splitting the largest cluster until reaching the desired number of clusters.
- Assigns cluster labels to each data point based on the splits.
- Returns history of clusters at each step and final labels.
- Visualizes data points colored by their final cluster.


# References
---
1. 
