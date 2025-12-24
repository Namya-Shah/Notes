PPO is a policy gradient method and can be used for environments with either discrete or continuous action spaces.
* It trains a stochastic policy in an on-policy way.
* It also utilises the **actor critic method**.
* The actor maps the observation to an action and the critic gives an expectation of the rewards of the agent for the observation given.
	* The observation represents the input data that the agent receives from the environment at a specific moment in time.
	* It is the information the agent uses to "see" or perceive the current situation before making a decision.
	* **Input for the Actor**: "*The actor maps the observation to an action.*" This means the observation serves as the raw input (variables, pixels, or sensor readings) that the Actor neural network processes to determine the best move to take.
		* Actor -> Observation -> Action
	* **Input for the Critic**: "*the critic gives an expectation of the rewards... for the observation given.*" Here, the observation is the context the Critic uses to judge how "good" or "bad" the current situation is (i.e., how much reward to expect).
		* Critic -> Observation -> Rewards
	* The **policy** is updated via a stochastic gradient ascent optimizer, while the **value function** is fitted via some gradient descent algorithm.
	* 