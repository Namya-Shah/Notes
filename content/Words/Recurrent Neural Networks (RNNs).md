---
tags:
  - word
---
- Mostly used where **sequence of data is important**
- First words get transformed into machine-readable vectors
- Then the **RNN processes the sequence of vectors one by one**.
# Difference between Feedforward Neural Network vs Recurrent Neural Network
- In feedforward neural network, we went from one way to another (left to right). There is only one way.
- In recurrent neural network, they don't have single direction.
# Hidden State
Information that goes from one RNN to next RNN is called **hidden state**.
## Passing hidden state to next time step
- While processing, it passes the previous hidden state to the next step of the sequence
- The *hidden state* acts as the **memory**.
- It holds information on previous data the network has seen before.
![[Pasted image 20250720233612.png]]
![[Pasted image 20250720233638.png]]
> [!NOTE]
> For the first RNN, we will define any random hidden state.
> Activation function (tanh) is generally fixed for RNN
# Equations
![[Pasted image 20250720233705.png]]
$x_t$: Encoded word vectors
$s_t$: hidden states
$E_t$: Loss function at each step
$$
s_t = tanh(Ux_t + Ws_{t-1})
$$
$$
z_t=Vs_t
$$
$$
\hat y_t = softmax(z_t)
$$
$$
E_t(y_t, \hat y_t) = -y_t \log(\hat y_t)
$$
$$
E(y, \hat y) = \sum_t E_t(y_t, \hat y_t)
$$
$y_t$: One hot encoded vector
$\hat y_t$: Probability distributions
# How to learn weights (U, V, W)
Overall gradient = Sum of gradients at each step
$$
\frac{\partial E}{\partial W} = \sum_t \frac{\partial E_t}{\partial W}
$$
$$
\frac{\partial E}{\partial V} = \sum_t \frac{\partial E_t}{\partial V}
$$
$$
\frac{\partial E}{\partial U} = \sum_t \frac{\partial E_t}{\partial U}
$$
![[Pasted image 20250720234503.png]]
- As we increase number of RNNs, the value for the gradient will come close to 0, which can cause **vanishing gradient**.
# Vanishing/Exploding Gradients
- **Vanishing Gradient**
	- Product of so many derivatives of tanh functions (<1) will lead to exponentially small values (~0).
- **Exploding Gradient**
	- Product of so many other activation functions and network parameters will lead to exponentially large values.
- **Exploding Gradient** problem can be simply solved by clipping the gradients.
- However, **vanishing gradients** is a complex issue and disallow capturing long-range dependencies.
- **Proper initialization of the W matrix can reduce the effect of vanishing gradients**
- **Use ReLU (derivative either 0 or 1) instead of sigmoid or tanh activation functions**
- **Use Long Short-Term Memory (LSTM) or Gated Recurrent Unit (GRU) architectures**