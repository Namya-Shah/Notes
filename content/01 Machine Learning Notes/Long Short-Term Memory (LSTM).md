---
Link: 
tags:
  - ML
---
- A type of RNN
- The differences are the operations within the LSTM's cells
![[Pasted image 20250720235402.png]]
![[Pasted image 20250720235423.png]]
# The main idea
- The cell state and various gates
- The **cell state** act as a transport highway that transfers relative information all the way down the sequence chain.
- The **gates** decide which information is allowed on the cell state.
- Gates contains **sigmoid activations**
- **Forget info**: if sigmoid activation ~ 0
- **Keep info**: if sigmoid activation ~ 1
# Forget gate
- This gate decides what information should be **thrown away or kept**
- Information from **previous hidden state** and the **current input** is passed through the sigmoid function.
- Values come out between 0 and 1. The closer to 0 means to forget, and the closer to 1 means to keep.
- **Hidden state** is **short term memory**
- **Cell state** is **long term memory**
![[Pasted image 20250721000024.png]]
![[Pasted image 20250721000038.png]]
# Input gate
- First, the previous hidden state and current input is passed into a sigmoid function
- Also pass the hidden state and current input into the tanh function to squish values between -1 and 1.
- Multiply the tanh output with the sigmoid output
- Sigmoid output will decide which information is important to keep from the tanh output
![[Pasted image 20250721000423.png]]
# Cell state
- The cell state gets pointwise multiplied by the forget vector.
- Take the output from the input gate and do a pointwise addition which updates the cell state to new values.
# Output gate
- The output gate decides what the next hidden state should be
- First, we pass the previous hidden state and the current input into a sigmoid function
- Then we pass the newly modified cell state to the tanh function.
- Multiply the tanh output with the sigmoid output.
![[Pasted image 20250721000932.png]]
- We get $g$ after we pass $(h_t + x_t)$ to $\tan(h)$ function.
- Operations in LSTM are slightly time consuming.
# References
---
1. 
