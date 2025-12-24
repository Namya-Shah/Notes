**USE CASE:** Predicting house prices, stock prices, or any continuous numerical value based on input features.
> [!NOTE]
> **THE MOST FUNDAMENTAL MACHINE LEARNING ALGORITHM**
- What is Linear Regression?
	- Linear Regression analysis is used to predict the value of a variable based on the value of another variable.
	- Other names
	    - **[[Ordinary Least Squares]]**
	    - **[[Simple Linear Regression]]**
	    - **[[Multiple Linear Regression]]**
	- Linear regression is a parametric supervised machine learning algorithm that tries to fit a line or hyperplane to data
	- Parametric → It has a model with parameters that we find values for
	- Supervised → We train the model by showing it what the correct answers should be every time it gives an output. It can then use that information to determine what good values should be for the parameters in its model
	- Find a line that fits our data or in multiple dimensions it tries to find a hyperplane that fits the data
	- **Simple Linear Regression**
	    - $y = mx + b$
	    - $\hat y = wx + b$
	    - w → weight
	    - b → bias term
	- **Multiple Linear Regression**
	    - $\hat y = w_1x_1+w_2x_2+w_3x_3+...+w_nx_n+b$
	    - n → Number of independent variables
	    - The data points will be near to the plane
- How the model learns?
	- Techniques for finding parameters $w \ \& \ b$
	    - **Ordinary Least Squares Method (Normal Equation)**
	        - A statistical method for finding the least squares coefficients
	        - It does this by solving for equations that minimize the squared error between predictions and correct values for what the model should have predicted and then those equations are called normal equations.
    - Gradient Descent
        - It is a fundamental machine learning technique for finding optimal values for parameters.
        - Gradient descent involves looking at how badly your model performs and slowly adjusting its parameters towards more optimal values by taking derivatives of the cost function.
        - A cost function represents how bad your machine learning algorithm is doing.
>[!IMPORTANT]
>***Different algorithms have different cost functions and same algorithms can have cost function written in different ways***

- **EQUATION:** $J = \frac{1}{2m} \sum^m_{i=1} (\hat y_i - y_i)^2$
    - J → Cost Function
    - m → Number of training examples that we have, it’s the number of data points that we have.
    - $\hat y_i$ → Predicted value for that data point
    - $y_i$ → Actual value for that data point. Sometimes it is called as label

> [!IMPORTANT]
> Whole cost function is sometimes called the mean squared error.
### Overview
- Linear regression is a foundational algorithm in machine learning, used for predicting a continuous varibale.
- Predicts a continuous output variable based on linear relationships between input features.
### Learning Objective
- Understand the theory behind linear regression.
- Learn to implement linear regression in Python.
#### Practice Questions
1. Implement linear regression to predict housing prices using a given dataset.
2. How would you evaluate the performance of your linear regression model?
### Short Description

Ideal for predicting continuous values. Use it for predicting house prices based on features like square footage and number of bedrooms.

Linear Regression is often overlooked in modern machine learning's ever-increasing world of complex neural network architectures, the algorithm is still widely used across a large number of domains because it is effective, easy to interpret, and easy to extend.

It is a **supervised algorithm** that learns to model a dependent variable, $y$, as function of some independent variables (aka “features”), $x_i$, by finding a line (or surface) that best “fits” the data.

### Overview

- Linear regression is a foundational algorithm in machine learning, used for predicting a continuous varibale.
- Predicts a continuous output variable based on linear relationships between input features.

### Learning Objective

- Understand the theory behind linear regression.
- Learn to implement linear regression in Python.

### Practice Questions

1. Implement linear regression to predict housing prices using a given dataset.
2. How would you evaluate the performance of your linear regression model?