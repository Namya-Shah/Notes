---
Location:
  - YouTube
Channel: 
Date: "2025-12-17 22:56"
Topics: 
tags:
  - YouTube
---
# Video
<iframe width="560" height="315" src="https://www.youtube.com/embed/glLO8cnwj6s?si=cOfLek3_aBbeqLFS" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

# Notes
- End-to-end project
	- Problem Definition
	- Data Collection
	- Feature Engineering
	- Model training
	- Deployment and Monitoring with Feedback loop
- **Problem Framing and Success Metrics**
	- Start with a business problem and then figure out if ML even the right tool for the job
	- Defining the user story, which is who this is for and what problem it solves for them.
	- It should also have ML model metric like AUC or mean squared error and most importantly, a business metric
- **Sourcing Data**
	- Rather than using clean data, try to use messy data to perform data cleaning and get real world experience
	- Use APIs to get data from publicly available datasets
		- Weather data, financial data, sports data
	- Try to web scrape data if APIs are not available
	- Niche datasets like government surveys or industry reports.
	- *Key Component:* Continuous Data Collection
	- Cron jobs to run the script every hour or every day
	- Setting up a workflow tool like AirFlow, Prefect to schedule and monitor data pulls
	- Using cloud schedulers to periodically call your data collection code
- **Data Storage**
	- A database or data lake is specifically designed for storing, organizing, and retrieving data.
	- We use different kind of databases or data lakes for different kinds of data.
	- Combination of relational database for structured data and object storage for files is extremely standard in industry.
	- Redis is used to keep data that changes quickly like session state, recent user actions, rolling counts, or cached model predictions so your system can read and write them extremly fast.
	- Advanced Data Storage Example
		- Long-term structured data in PostgreSQL
		- Files in S3
		- Real-time features and caching in Redis
- **Feature Engineering**
	- Cleaning, creating and preparing features and selecting which ones to keep
	- Involves handling things like missing values, outliers, and type conversion and standardization
	- *Avoid Data Leakage*
		- Leakage is when your features contain information that they wouldn't actually have at the time of prediction.
	- Feature Selection
		- Looking at feature importance from your model, checking correlations between features or techniques like recursive feature elimination.
- **Labelling**
	- *Your model can be as good as your labelling skills*
	- Clear Labelling Guidelines
	- Weak supervision or programmatic labelling
		- Write rules or heuristics to automatically generate labels
- **Model Training and Evaluation**
	- Proper train/val/test splits
	- Training data is what your model learns from
	- Validation or dev data is what you use to tune hyper parameters and compare different model approaches
	- Test data is what you don't touch until the very end and when you want to report final performance
	- Model Selection and Versioning
		- `model_v1.pkl`
		- `model_v2.pkl`
- **Deployment**
	- REST API
		- Most common and most professional approach
		- FastAPI and Flask
	- Batch Predictions
		- Use Case: predicting tomorrow's sales for all stores, scoring all customers for churn risk once a week and generating daily content recommendations
	- Interactive App (Web App)
		- Streamlit and Gradio
	- Docker
		- Containerization
	- CI/CD
		- Jenkins and Github Actions
	- Unit Tests
- **Monitoring and Feedback Loops**
	- Automated Alerting
- **Complete Pipelines**
	- Proper Documentation

