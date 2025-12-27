---
Link:
tags:
  - Interview
---
1. What do you mean by Convolutional Neural Network?
	- A Convolutional Neural Network (CNN, or ConvNet) is another type of neural network that can be used to enable machines to visualize things.
	- CNN's are used to perform analysis on images and visuals. These classes of neural networks can input a multi-channel image and work on it easily with minimal preprocessing required.
	- These neural networks are widely used in:
		- Image recognition and Image classification
		- Object detection
		- Recognition of faces, etc.
2. Why do we prefer Convolutional Neural Networks (CNNs) over Artificial Neural Networks (ANNs) for image data as input.
	- Feedforward neural networks can learn a single feature representation of the image but in the case of complex images, ANN will fail to give better predictions, this is because it cannot learn from pixel dependencies present in the image.
	- CNN can learn multiple layers of feature representations of an image by applying filters, or transformations.
	- In CNN, the number of parameters for the network to learn is significantly lower than the multilayer neural networks since the number of units in the network decreases, therefore reducing the chance of overfitting.
	- Also, CNN considers the context information in the small neighborhood and due to this feature, these are very important to achieve a better prediction in data like images. Since digital images are a bunch of pixels with high values, it makes sense to use CNN to analyze them. CNN decreases their values, which is better for the training phase with less computational power and less information loss.
3. Explain the different layers in CNN
	- **Input Layer**
		- The input layer in CNN should contain image data. Image data is represented by a three-dimensional matrix. We have to reshape the image into a single column.
		- For example, suppose we have an MNIST dataset and you have an image of dimension 28 x 28 = 784, you need to convert it into 784 x 1 before feeding it into the input. If we have "k" training examples in the dataset, then the dimension of input will be (784, k).
	- **Convolutional Layer**
		- To perform the convolution operation, this layer is used which creates several smaller picture windows to go over the data.
	- **ReLU Layer**
		- This layer introduces the non-linearity to the network and converts all the negative pixels to zero. The final output is a rectified feature map.
	- **Pooling Layer**
		- Pooling is a down-sampling operation that reduces the dimensionality of the feature map.
	- **Softmax/Logistic Layer**
		- The softmax or logistic layer is the last layer of CNN. It resides at the end of the FC layer. Logistic is used for binary classification problem statement and softmax is for multi-classification problem statement.
	- **Output Layer**
		- This layer contains the label in the form of a one-hot encoded vector.
4. Explain the significance of the RELU Activation function in Convolution Neural Network
	- RELU Layer - After each convolution operation, the RELU operation is used. Moreover, RELU is a non-linear activation function. This operation is applied to each pixel and replaces all the negative pixel values in the feature map with zero.
	- Usually, the image is highly non-linear, which means varied pixel values. This is a scenario that is very difficult for an algorithm to make correct predictions. RELU activation function is applied in these cases to decrease the non-linearity and make the job easier.
	- Therefore this layer helps in the detection of features, decreasing the non-linearity of the image, converting negative pixels to zero which also allows detecting the variation of features.
5. Why do we use a Pooling Layer in a CNN?
	- CNN uses pooling layers to reduce the size of the input image so that it speeds up the computation of the network.
	- Pooling or spatial pooling layers: Also called subsampling or downsampling.
		- It is applied after convolution and RELU operations.
		- It reduces the dimensionality of each feature map by retaining the most important information.
		- Since the number of hidden layers required to learn the complex relations present in the image would be large.
	- As a result of pooling, even if the picture were a little tilted, the largest number in a certain region of the feature map would have been recorded and hence the feature would have been preserved. Also as another benefit, reducing the size by a very significant amount will use less computational power. So, it is also useful for extracting dominant features.
6. What is the size of the feature map for a given input size image, Filter Size, Stride, and Padding amount?
	- Stride tells us about the number of pixels we will jump when we are convolving filters.
	- If our input image has a size of n x n and filters size f x f and p is the padding amount and s is the stride, then the dimension of the feature map is given by:
	- $Dimension = floor[((n-f+2p)/s)+1] x floor[((n-f+2p)/s)+1]$
7. An input image has been converted into a matrix of size 12 X 12 along with a filter of size 3 X 3 with a Stride of 1. Determine the size of the convoluted matrix.
	- To calculate the size of the convoluted matrix, we use the generalized equation, given by:
	- $C = ((n-f+2p)/x)+1$
	- Here n = 12, f = 3, p = 0, s = 1
	- Therefore the size of the convoluted matrix is 10 x 10
8. Explain the terms "Valid Padding" and "Same Padding" in CNN.
	- **Valid Padding**
		- This type is used when there is no requirement for Padding. The output matrix after convolution will have the dimension of (n-f+1) X (n-f+1).
	- **Same Padding**
		- Here, we added the Padding elements all around the output matrix. After this type of padding, we will get the dimensions of the input matrix the same as that of the convolved matrix.