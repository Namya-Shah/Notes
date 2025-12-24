---
Link: 
tags:
  - ML
---
# Notes
## What is Data Preprocessing?

- Real-world datasets are generally messy, raw, incomplete, inconsistent, and unusable. It can contain manual entry errors, missing values, inconsistent schema, etc. Data preprocessing is the process of converting raw data into a format that is understandable and usable. It is a crucial step in any data science project to carry out an efficient and accurate analysis. It ensures that data quality is consistent before applying any Machine Learning or Data Mining techniques.

## Why Data Preprocessing

The main objective of this step is to ensure and check the quality of data before applying any Machine Learning or Data Mining methods, here are some of its benefits:

- Accuracy
- Completeness
- Consistent
- Timeliness
- Trustable
- Interpretability

## Key steps in Data Preprocessing

![[Screenshot_2024-07-11-22-57-28-63_1c337646f29875672b5a61192b9010f9.jpg]]

## Data Cleaning

### Handling Missing Values:

- Input data often contains missing or NULL values.
- Techniques include removing rows/columns with NULL values or imputing using mean, mode, regression, etc.

### De-noising

- Process of removing noise from data.
- Techniques: binning features, regression for noise reduction, clustering for outlier detection, etc.

## Data Integration

### Entity Identification Problem:

- Identifying corresponding objects/features from multiple databases.

### Schema Integration:

- Merging multiple database schemas into a single schema.

### Detecting and Resolving Data Value Concepts:

- Ensuring consistency in data representation across databases, e.g., date formats.

## Data Reduction

### Dimensionality Reduction:

- Reducing the number of features in the dataset, e.g., through PCA.

### Numerosity Reduction

- Reducing data volume by alternative representations, e.g., regression modeling.

### Data Compression

- Compressing data, either lossless or lossy.

## Data Transformation

### Smoothing:

- Removing noise to identify important features and patterns.

### Aggregation:

- Summarizing large data volumes for better understanding, e.g., monthly sales data.

### Discretization:

- Converting continuous variables into intervals/bins for easier analysis, e.g., age groups.

### Normalization

- Converting numeric variables into specified ranges, e.g., Min-Max Normalization, Standardization

## Applications of Data Preprocessing

- Data Preprocessing is important in the early stages of a Machine Learning and AI application development lifecycle. A few of the most common usage or application include:
    - Improved accuracy of ML models
    - Reduced costs
    - Visualization

# References
---
1. 
