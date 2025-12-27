---
Link:
tags:
  - ML
---
# Notes
## Train-Test Split
- First and foremost, split the data into training and test sets to validate the model's performance on unseen data.
```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)
```
## Cross-Validation
- Use cross-validation to get a more reliable estimate of the model's performance.
```python
from sklearn.model_selection import cross_val_score
from sklearn.ensemble import RandomForestClassifier

clf = RandomForestClassifier()
scores = cross_val_score(clf, X, y, cv=5)
```
## Regularization
- Apply regularization methods like L1 or L2 regularization to add some form of penalty to the model.
For Ridge Regression (L2)
```python
from sklearn.linear_model import Ridge

ridge = Ridge(alpha=1.0)
ridge.fit(X_train, y_train)
```
For Lasso Regression (L1)
```python
from sklearn.linear_model import Lasso

lasso = Lasso(alpha=1.0)
lasso.fit(X_train, y_train)
```
## Dropout
- Introduce dropout layers in neural networks to randomly set a fraction of input units to 0 during training.
```python
from keras.models import Sequential
from keras.layers import Dense, Dropout

model = Sequential([
	Dense(64, activation='relu', input_shape=(X_train.shape[1],)),
	Dropout(0.5),
	Dense(1, activation='sigmoid')
])
```
## Early Stopping
- Stop training when the model's performance starts to degrade on a held-out validation dataset.
```python
from keras.callbacks import EarlyStopping

early_stopping = EarlyStopping(monitor='val_loss', patience=2)
model.fit(X_train, y_train, epochs=50, validation_split=0.2, callbacks=[early_stopping])
```
## Ensemble Methods
- Use ensemble methods like Random Forest or Gradient Boosting to average out biases and reduce variance.
```python
from sklearn.ensemble import RandomForestClassifier

rf = RandomForestClassifier(n_estimators=50)
rf.fit(X_train, y_train)
```
## Feature Selection
- Reduce the dimensionality of the data by selecting only the most important features.
```python
from sklearn.feature_selection import SelectKBest, f_classif

selector = SelectKBest(score_func=f_classif, k=5)
X_new = selector.fit_transform(X, y)
```

# References
---
1. [[Train-Test Split]]
2. [[Cross-validation]]
3. [[Regularization]]
4. [[Dropout]]
5. [[Early Stopping]]
6. [[Ensemble Methods]]
7. [[Feature Selection]]
