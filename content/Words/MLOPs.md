---
Link:
tags:
  - word
Created On: 2025-12-24
Links:
Subject:
---
# Notes
![[Pasted image 20251224184510.png]]
- MLOps is a set of practices that aims to deploy and maintain machine learning models in production reliably and efficiently.
- **Post-deployment woes**: 
	- Accounting for latency
		- 53% of visitors are abandoned if a mobile site takes longer than 3 seconds to load
	- Fairness
		- Microsoft created a Twitter bot to learn from users. It quickly become a racist. It started supporting bad ideologies after deployment
	- Lack of explainability & auditability
		- Explaining predictions is hard and also have to make sure it is authentic enough to trust this
	- Painfully slow
		- 36% said they spend quarter of their time deploying ML models
- **Model-Centric**
	- Holding the data fixed and iteratively improving the model (Hyperparameter Tuning)
- **Data-Centric**
	- Holding the model fixed and iteratively improving the data
## What is the business problem we are trying to solve?
- **The cost of wrong predictions**
	- The cost of incorrect predictions can be quite high. Overstock leads to wasted resources and possible write-offs for unsold products. Understock, on the other hand, results in missed sales opportunities and unsatisfied customers.
- **Breaking Down the Sales Forecasting Process**
	- Data Gathering
	- Historical Sales Analysis
	- Market Trend Analysis
	- Actual Forecasting
- **Identifying AI/ML Opportunities**
	- AI/ML could be useful in the actual forecasting task, where it could analyze past sales data and market trends to predict future sales with higher accuracy than traditional methods.
- **Estimating the ROI of AI/ML Implementation**
	- The ROI could be estimated by comparing the potential increase in sales and decrease in wasted resources due to improved forecasts, against the costs of developing and maintaining the AI/ML solution.
- **Prioritizing Tasks for AI/ML Implementation**
	- In this case, there's primarily one task that could benefit from AI/ML, which is actual forecasting. Therefore, we prioritize it for implementation.
## Understanding the Machine Learning Canvas
- A tool with ten blocks that helps us structure and plan our ML application development.
- ### Value Proposition
	- Defining the problem, its importance, and our end-user persona.
	- Geoffrey Moore's Value Positioning Statement Template: For (target customer) who (need), our (product/service) is (product category) that (benefit).
- ### Data Sources
	- Identifying potential sources of data, including internal databases, APIs, open datasets, and more.
	- Considering hidden costs such as data storage and purchasing external data.
- ### Prediction Task
	- Deciding the ML task: Supervised or Unsupervised? Anomaly Detection? Classification, regression or ranking?
	- Thinking about input, output, and the degree of model complexity
- ### Feature Engineering
	- Working with domain experts to extract features from raw data sources
- ### Offline Evaluation
	- Setting up metrics to evaluate system performance pre-deployment
	- Understanding model prediction errors and their impacts
- ### Decisions
	- Using predictions to make decisions: How will the end-user interact with our predictions?
	- Possible hidden costs, including human intervention.
- ### Collecting Data
	- Collecting new data for model re-training and preventing model decay
	- Cost considerations for data collection and the role of humans in data labeling
- ### Building Models
	- Deciding frequency of model re-training and associated hidden costs.
	- Planning for changes in tech stack and scaling
- ### Live Evaluation and Monitoring
	- Setting up metrics to track system performance post-deployment
	- Understanding the correlation between model metrics and business metrics
- ### When not to implement AI/ML?
	- Identifying situations where AI/ML may not be the best solution
## Workflow of Machine Learning-based Software Development
- Three main artifacts:
	- Data
	- ML Model
	- Code
- Three main phases:
	- Data Engineering
	- ML Model Engineering
	- Code Engineering
- ### Data Engineering Introduction
	- Data acquisition and data preparation
	- Most resource and time-consuming phase
	- Prevents propagation of data errors to the next phase
	- **Data Ingestion:** Collection of data from different sources
	- **Exploration and Validation:** Understanding data content and structure
	- **Data Wrangling:** Formatting and cleaning the data
	- **Data Labeling:** Assigning categories to data points
	- **Data Splitting:** Division of data into training, validation and test datasets
- ### Model Engineering Introduction
	- Core of the ML workflow: writing and executing ML algorithms
	- Obtaining the ML model
	- **Model Training:** Applying ML algorithms on training data
	- **Model Evaluation:** Validating the model pre-deployment
	- **Model Testing:** Final acceptance test using test dataset
	- **Model Packaging:** Exporting model into a consumable format for business application
- ### Model Deployment Introduction
	- **Model Serving:** Addressing the ML model in a production environment
	- **Model Performance Monitoring:** Observing performance on live, unseen data
	- **Model Performance Logging:** Recording every inference request



# References
---
1. [[ZenML]]