#### Explain Bias-Variance Tradeoff
- The bias-variance tradeoff represents the balance between the model's ability to generalize across different datasets (bias) and its sensitivity to small fluctuations in the training set (variance). A high-bias model is too simple and under-fits the data, missing the underlying trend. A high-variance model is too complex, overfitting the data and capturing noise as if it were a real pattern. The goal is to find a sweet spot that minimizes the total error.
![[Screenshot_2024-07-08-08-29-35-45_1c337646f29875672b5a61192b9010f9.jpg]]
#### How does Gradient Descent work?
- Gradient Descent is an optimization algorithm used to minimize some function by iteratively moving in the direction of the steepest descent as defined by the negative of the gradient. In machine learning, it's used to find the parameters of a model that minimize the cost function. The learning rate determines the size of the steps taken to reach the minimum.
![[Screenshot_2024-07-08-08-31-04-17_1c337646f29875672b5a61192b9010f9.jpg]]
#### What is Regularization? Give examples.
- Regularization is a technique used to prevent overfitting by adding a penalty on the size of the coefficients. The penalty term discourages complex models and thus reduces variance without substantially increasing bias. Examples include L1 regularization (Lasso), which adds the absolute value of the magnitude of coefficients as penalty, and L2 regularization (Ridge), which adds the square of the magnitude of coefficients.
![[Screenshot_2024-07-08-08-39-29-38_1c337646f29875672b5a61192b9010f9.jpg]]
#### Explain the difference between Bagging and Boosting
- Both bagging and boosting are ensemble techniques to improve model predictions, but they work differently.

| S.No. | Bagging                                                                                               | Boosting                                                                           |
| ----- | ----------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| 1.    | The simplest way of combining predictions that belong to the same type.                               | A way of combining predictions that belong to the different types.                 |
| 2.    | Aim to decrease variance, not bias.                                                                   | Aim to decrease bias, not variance.                                                |
| 3.    | Each model receives equal weight.                                                                     | Models are weighted according to their performance.                                |
| 4.    | Each model is built independently.                                                                    | New models are influenced by the performance of previously built models.           |
| 5.    | Different training data subsets are randomly drawn with replacement from the entire training dataset. | Every new subset contains the elements that were misclassified by previous models. |
| 6.    | Bagging tries to solve the over-fitting problem.                                                      | Boosting tries to reduce bias.                                                     |
| 7.    | If the classifier is unstable (high variance), then apply bagging.                                    | If the classifier is stable and simple (high bias), then apply boosting.           |
| 8.    | Example. The Random Forest model uses Bagging                                                         | Example. The AdaBoost uses Boosting Techniques                                     |
#### Describe the ROC Curve and AUC.
- The ROC Curve (Receiver Operating Characteristic Curve) is a graph showing the performance of a classification model at all classification thresholds. It plots the True Positive Rate (TPR) against the False Positive Rate (FPR). AUC (Area Under the RoC Curve) measures the entire two-dimensional area underneath the entire ROC curve and provides an aggregate measure of performance across all possible classification thresholds. An AUC of 1 represents a perfect model; an AUC of 0.5 represents a worthless model.
![[Screenshot_2024-07-08-09-29-00-94_1c337646f29875672b5a61192b9010f9.jpg]]
#### What are Convolutional Neural Networks (CNNs) and where they are used?
- CNNs are a class of deep neural networks, most commonly applied to analyzing visual imagery. They use a mathematical operation called convolution in at least one of their layers. A key feature of CNNs is their ability to automatically and adaptively learn spatial hierarchies of features from images. CNNs are widely used in image and video recognition, recommender systems, and natural language processing.
![[Screenshot_2024-07-08-09-29-23-57_1c337646f29875672b5a61192b9010f9.jpg]]
#### How do Recurrent Neural Networks (RNNs) differ from CNNs?
- While CNNs are primarily used for spatial data (like images), RNNs are designed to work with sequence data (like text or time series). RNNs have loops allowing information to persist, meaning they can keep track of information in a sequence, making them ideal for tasks like language modelling and text generation. Unlike CNNs, RNNs can handle inputs of varying lengths.
![[Screenshot_2024-07-08-09-29-42-79_1c337646f29875672b5a61192b9010f9.jpg]]
#### Explain the concept of Transfer Learning.
- Transfer Learning involves taking a pre-trained model (trained on a large dataset) and fine-tuning it with a smaller dataset for a similar or different task. This approach allows leveraging learned feature maps without starting from scratch, saving time and computational resources. It's particularly useful in deep learning where large datasets and extensive training are usually required.
![[Screenshot_2024-07-08-09-29-55-92_1c337646f29875672b5a61192b9010f9.jpg]]