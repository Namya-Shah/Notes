# Vocabulary
- States are simply the observations that our model will see while it interacts with the environment.
- Actions is how it can interact with the environment. How it can make decisions to receive new observations.
- Agent is the main actor in the environment. It is taking the decisions and actions.
- Environment is the place in which the agent exists and makes its decisions.
- Based on the actions the agent takes, the environment will send observations back to the agent
**Total Reward:** $R_t = \sum_{i=t}^\infty r_i=r_t+r_{t+1}+...+r_{t+h}+...$
**Discounted Total Reward (Return):** $R_t=\sum_{i=t}^\infty \gamma^i r_i$
> [!NOTE]
> *Future rewards are much less valuable than current rewards*

- **Example:** 5$ today is more valuable than 5$ after 10 years
# Q-Function
$$
R_t = r_t + \gamma r_{t+1} + \gamma^2r_{t+2} + ...
$$
$R_t$ is the discounted sum of all rewards obtained from time $t$
$$
Q(s_t, a_t) = \mathbb{E}[R_t|s_t,a_t]
$$
The Q-function captures the **expected total future reward** an agent in state $s$, can receive by executing a certain action $a$.
* Ultimately, the agent needs a **policy $\pi(s)$**, to infer the best action to take at its state, s
**Strategy:** the policy should choose an action that maximizes future reward.
$$
\pi^*(s) = argmax_a \ Q(s,a)
$$
> Optimal action for any given state is just going to be computed by plugging in all of our actions to this Q function

# Value Learning
Find Q(s,a)
$a = argmax_a \ Q(s,a)$
![[Pasted image 20251220234846.png]]
- The only difference is changing the parameterization of how you're calling this model.
- **Minimize the number of calls to the model as it becomes more expensive**
- The **state** captures the entire environment
- What happens if we take all the best actions?
	- *Maximize target return -> train the agent*

target = $(r + \gamma \max_{a'}Q(s',a')$
## Q-Loss
$$
\mathcal{L} = \mathbb E[||(r+\gamma \max_{a'}Q(s',a')) - Q(s,a)||^2]
$$
## Example of Atari Game
![[Pasted image 20251221115235.png]]
## Downsides of Q-Learning
**Complexity:**
- Can model scenarios where the action space is discrete and small
- Cannot handle continuous action spaces
**Flexibility:**
- Policy is deterministically computed from the Q function by maximizing the reward -> cannot learn stochastic policies
	- It is a deterministic algorithm and no stochasticity involved
# Policy Learning
Find $\pi(s)$
Sample a ~ \pi(s)
![[Pasted image 20251220235112.png]]
![[Pasted image 20251221124433.png]]
- We will output not the Q-value but we will output a probability that the action would have been the best action.
## Case Study - Self Driving Cars
![[Pasted image 20251221142245.png]]
### Training Algorithm
1. Initialize the agent
2. Run a policy until termination
3. Record all states, actions, rewards
4. Decrease probability of actions that resulted in low reward
5. Increase probability of actions that resulted in high reward
$$
loss = - \log P(a_t|s_t)R_t, \quad \text{log-likelihood of action * discounted reward}
$$
*Gradient Descent:*
$$
w' = w - \nabla \ \text{loss}
$$
$$
w' = w + \nabla \text{log}P(a_t|s_t)R_t
$$
![[Pasted image 20251221144454.png]]


---
# Frameworks
[[Actor-Critic Method]]
[[Proximal Policy Optimization]]
[[Policy]]

---
# References
[Colab Notebook](https://colab.research.google.com/drive/1HtW6ActUnacCcs1In0kJIUzIJaW6vH8v?authuser=0#scrollTo=x36pnc4kU4Ag)
