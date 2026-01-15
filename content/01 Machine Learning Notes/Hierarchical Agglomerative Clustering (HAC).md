---
Link:
tags:
  - ML
  - Unsupervised-Learning
---
# Brief Introduction
It is also known as the bottom-up approach or hierarchical agglomerative clustering (HAC). Bottom-up algorithms treat each data as a singleton cluster at the outset and then successively agglomerate pairs of clusters until all clusters have been merged into a single cluster that contains all data.
## Workflow
1. **Start with individual points**: Each data point is its own cluster. For example, if we have 5 data points we start with 5 clusters each containing just one data point.
2. **Calculate distances between clusters**: Calculate the distance between every pair of clusters. Initially since each cluster has one point this is the distance between the two data points.
3. **Merge the closest clusters**: Identify the two clusters with the smallest distance and merge them into a single cluster.
4. **Update distance matrix**: After merging we now have one less cluster. Recalculate the distances between the new cluster and the remaining clusters.
5. **Repeat steps 3 and 4**: Keep merging the closest clusters and updating the distance matrix until we have only one cluster left.
6. **Create a dendogram**: As the process continues we can visualize the merging of clusters using a tree-like diagram called a dendogram. It shows the hierarchy of how clusters are merged.
## Implementation
- Start with each data point as its own cluster.
- Compute distances between all clusters
- Merge the two closest clusters based on a linkage method
- Update the distances to reflect the new cluster
- Repeat merging until the desired number of clusters or one cluster remains
- The dendogram visualizes these merges as a tree, showing cluster relationships and distances

# References
---
1. [[Hierarchical Clustering]]
