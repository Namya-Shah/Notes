---
Lecture Date: 2025-01-26
Presentation: 
Links: 
Subject:
  - "[[EM 619 - Machine Learning for Predictive Analysis]]"
Refernces:
  - "[[Decision Tree]]"
tags:
  - EM619
---
```table-of-contents
```
# Types of Machine Learning
- Whether a label is **present or not**
	- Label is **present** - *supervised learning* e.g., classification/regression
		- Types of labels
			- If label is continuous (real number) - regression
			- If label is discrete - classification
				- If we have two labels, say 0 and 1 or -1 and +1, we term this classification problem as **binary classification**
				- If we have more than two labels, it is **multiclass classification problem**.
	- Label is **absent** - *unsupervised learning*, e.g., clustering
- Based on the number of outputs:
	- **Single Label**
	- **Multi-Label** - There can also be more than one label in supervised learning problems. These problems are referred to as **multilabel problems**. We can have multi-label regression or classification tasks.

| Problem                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Type                                                               | Why?                                                                                                                                                                                                                                                              |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Predict **price of apartment** in a specific area in Ahmedabad given training data consisting of apartments and their prices.                                                                                                                                                                                                                                                                                                                                                                                                                                   | Supervised > Regression > (single label)                           | The required label Price is a continuous value                                                                                                                                                                                                                    |
| Predict temperatures in Ahmedabad for next 7 days given **temperatures for last two years**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Supervised > Regression > (multi-label)                            | The required output is temperature for next 7 days. Hence it is a multi-label regression problem                                                                                                                                                                  |
| Based on the loan application, predict *how much loan can be sanctioned*. For this we are **given training data of past loan applications and the sanctioned amount**.                                                                                                                                                                                                                                                                                                                                                                                          | Supervised > Regression > Single Label                             |                                                                                                                                                                                                                                                                   |
| Based on the loan application, predict *whether the loan should be approved or not*. For this we are **given training data of past loan applications and their approval status**.                                                                                                                                                                                                                                                                                                                                                                               | Supervised > Classification > Single Label (Binary Classification) | The required label is loan approved or not (1 for loan approved and 0 for not approved). One label per application hence single label classification problem. In addition to that there are only two labels 0 and 1, hence it is a binary classification problem. |
| ![Image](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdL9rOW1d-RWG7FsQ8rcop9bAMmjG4zIjrXUoozJmOtzoV3gshbwzl_wgL6RivPw2bkMscGfAS2q8MMpaS91elNipRo2CGb-Us6tEEKAcpO1Kz0Ke8C5t4IqXEtVZ9wid065EUFeg?key=MUx8O33szcqz1Vj5OprnR9hY)<br>We are given **example images where each image is annotated with fruits present in that image**. Now for a given fruit basket, we need to label it with a **set of fruits** that are present in the basket.<br><br>For this fruit basket, the actual labels would be *grapes, oranges, kiwi, pineapple, apple, blackberry*. | Supervised > Multi-label > Multi-class                             |                                                                                                                                                                                                                                                                   |
| **Customer Segmentation** - We need to group customers based on their similarity.<br><br>What is given - customer data along with their features or attributes.                                                                                                                                                                                                                                                                                                                                                                                                 | Unsupervised > Clustering                                          | The label is not provided hence it is an unsupervised learning problem.                                                                                                                                                                                           |
| Given a restaurant review from a customer, predict their rating (1 to 5). We are **given past data about customer feedback and their ratings**.                                                                                                                                                                                                                                                                                                                                                                                                                 | Supervised > Classification > Single Label > Multi-class           | There are 5 classes - 1 to 5 and hence it is a multi-class classification problem.                                                                                                                                                                                |

# Common ML Problems

| Input               | Output                 | Problem                                 |
| ------------------- | ---------------------- | --------------------------------------- |
| A set of attributes | Single/Multiple labels | Tabular data ML                         |
| Text                | Text                   | Language translation, Text generation   |
| Text                | Image                  | Image generation                        |
| Text                | Audio                  | Audio generation                        |
| Text                | Movie                  | Movie generation                        |
| Images              | Text                   | OCR, Image Captioning, Object Detection |
| Audio               | Text                   | Speech Recognition                      |
| Movie               | Text                   | Transcriptions                          |
| Text                | Sentiment              | NLP (Sentiment classification)          |
Given any input, we need to convert into a bunch of features, which should be numeric.
Text -> Features(numbers) [Natural Language Processing]
Image -> Features(numbers) [Image Processing, Computer Vision]
- Movies -> a sequence of images
Audio -> Features [Speech Processing]

Input(Text/Image/Audio) -> Neural Networks(deep learning) -> Embeddings(features)
- We use deep learning for feature engineering or feature extraction.