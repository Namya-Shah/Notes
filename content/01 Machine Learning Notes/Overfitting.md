---
Topics:
  - "[[Machine Learning]]"
---
- Overfitting in ML occurs when model learn the details and noise in the training data to such extent that it performs well on training data but performs very poorly on unseen data. This happens because the model is too complex and capturing not only the true patterns in the data but also random fluctuations and errors.
### Key points to understand the overfitting
1. High training accuracy but low testing accuracy
2. Complex Models
	- Overfitting is more likely to occur with models that are too complex relative to the amount of training data.
	- Examples include deep neural nets with too many layers or decision trees with too many splits.
3. Insufficient Data
	- When there’s not enough data model can become too tailored to specifics of the training data set and that leads to overfitting.
4. Noise in the Data
	- If the training data contains a lot of noise and errors the overfitted model will just learn it and believe it is an actual pattern.
![[Pasted image 20240724234415.png]]
