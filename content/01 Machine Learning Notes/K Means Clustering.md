---
Link:
tags:
  - ML
  - Unsupervised-Learning
---
# Brief Introduction

**K-Means Clustering** groups similar data points into clusters without needing labeled data. It is used to uncover hidden patterns when the goal is to organize data based on similarity.
* Helps identify natural groupings in unlabeled datasets
* Works by grouping points based on distance to cluster centers
* Commonly used in customer segmentation, image compression, and pattern discovery.
* Useful when you need structure from raw, unorganized data
## Working
`k` represents the number of groups or clusters we want to classify our items into.
To calculate the similarity we will use Euclidean distance as a measurement.
**Steps:**
1. **Initialization:** We begin by randomly selecting k cluster centroids.
2. **Assignment Step:** Each data point is assigned to the nearest centroid, forming clusters.
3. **Update Step:** After the assignment, we recalculate the centroid of each cluster by averaging the points within it.
4. **Repeat:** This process repeats until the centroids no longer change or the maximum number of iterations is reached.
> [!NOTE]
> We have to initialize the centroids at a far distance so that we will find the centroids to converge in the center
## Why use?
> K-Means is popular in a wide variety of applications due to its simplicity, efficiency and effectiveness.
1. **Data Segmentation**: One of the most common uses of K-Means is segmenting data into distinct groups. For example, businesses use K-Means to group customers based on behavior, such as purchasing patterns or website interaction.
2. **Image Compression**: K-Means can be used to reduce the complexity of images by grouping similar pixels into clusters, effectively compressing the image. This is useful for image storage and processing.
3. **Anomaly Detection**: K-Means can be applied to detect anomalies or outliers by identifying data points that do not belong to any of the clusters.
4. **Document Clustering**: In natural language processing (NLP), K-Means is used to group similar documents or articles together. It's often used in applications like recommendation systems or news categorization.
5. **Organizing Large Datasets**: When dealing with large datasets, K-Means can help in organizing the data into smaller, more manageable chunks based on similarities, improving the efficiency of data analysis.
## Challenges
* **Choosing the Right Number of Clusters (`k`)**: One of the biggest challenges is deciding how many clusters to see
* **Sensitive to Initial Centroids**: The final clusters can vary depending on the initial random placement of centroids.
* **Non-Spherical Clusters**: K-Means assumes that the clusters are spherical and equally sized. This can be a problem when the actual clusters in the data are of different shapes or densities.
* **Outliers**: K-Means is sensitive to outliers, which can distort the centroid and, ultimately, the clusters.
# References
---
1. 
