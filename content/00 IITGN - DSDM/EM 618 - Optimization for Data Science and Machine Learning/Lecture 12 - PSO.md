---
Lecture Date: 2025-03-05
Presentation:
Links:
Subject:
  - "[[EM 618 - Optimization for Data Science and Machine Learning]]"
References:
  - "[[Particle Swarm Optimization]]"
tags:
  - EM618
---
# Particle Swarm Optimization
## What is Particle Swarm Optimization (PSO)?
- 
## PSO: Broad Steps
1. **Initialization:** random positions, random velocities
2. **Evaluate Fitness:** see how good each particle's position is
3. **Update `pbest` & `gbest`:** track best solutions so far
4. **Velocity Update:** move each particle influenced by `pbest` and `gbest`
5. **Position Update:** new position = old position + velocity
6. **Repeat** until stopping criteria is met
## Velocity Update (Key Equation)

$$
v_i \leftarrow w v_i + c_1 r_1 (\text{pbest}_i - x_i) + c_2 r_2 (\text{gbest})
$$
