---
Link: 
tags:
---
# What is Customer Churn?
> [!NOTE] Definition
> Customer churn is the percentage of customers that stopped using the company's product or service during a certain time frame.
* One of the ways to calculate a churn rate is to divide the number of customers lost during a given time interval by the number of active customers at the beginning of the period.
* **Example:** If you got 1000 customers and lost 50 last month, then your monthly churn rate is 5 percent.
* *Predicting customer churn is a challenging but extremely important business problem where the cost of customer acquisition is high such as technology, telecom, finance, etc.*
* The ability to predict that a particular customer is at a high risk of churning, while there is still time to do something about it, represents a huge additional potential revenue source for companies.

# How is the Customer Churn machine learning model used in practice?
* *The primary objective of the customer churn predictive model is to retain customers at the highest risk of churn by proactively engaging with them.*
* **Example:** Offer a gift voucher or any promotional pricing and lock them in for an additional year or two to extend their lifetime value to the company.

**TWO BROAD CONCEPTS TO UNDERSTAND HERE:**
* We want a customer churn predictive model to predict the churn in advance (let's say one month in advance, three months in advance, or even six months in advance -- it all depends on the use-case). This means that you have to be extremely careful of the cut-off date i.e., You shouldn't be using any information after the cut-off date as a feature in the machine learning model, otherwise it will be leakage. The period before the cut-off date is known as the **Event**.
* Normally for customer churn prediction, you will have to work a little bit to create a *target column*, it's generally not available in the form you would want it. For example, you want to predict if the customer will churn within the next quarter, and so you will iterate through all the active customers as of your event cut-off date and check if they left the company in the next quarter or not (1 for yes, 0 for no). The quarter in this case is called **Performance Window**.
![[Pasted image 20260606184112.png]]
# Customer Churn Model Workflow
![[Pasted image 20260606184639.png]]
- A model is trained on customer churn history (event period for X features and performance window for target variable).
- Every month active customer base is passed onto **Machine Learning Predictive Model** to return the probability of churn for each customer (in business lingo, this is sometimes called a score of churn).
- The list will be sorted from highest to lowest probability value (or score as they say it) and the customer retention teams will start engaging with the customer to stop the churn, normally by offering some kind of promotion or gift card to lock in few more years.
- Customers that have a very low probability of churn (or essentially model predicts no-churn) are happy customers. No actions are taken on them.

> [!IMPORTANT]
> Code files are in `Developer/tutorials/customer-churn`


# References
---
1. [Pycaret - Customer Churn](https://pycaret.gitbook.io/docs/learn-pycaret/official-blog/predict-customer-churn-using-pycaret)
2. 
