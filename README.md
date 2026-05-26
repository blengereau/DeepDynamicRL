# Deep Reinforcement Learning for Dynamic Economic Systems

This project solves a continuous-time optimal growth problem with human capital accumulation. It explores how AI methods can learn optimal decision rules in economic environments governed by Bellman equations and intertemporal optimization.

## Project Overview

This repository investigates how Deep Learning and Reinforcement Learning can approximate optimal policies in a classical economic control problem.

The agent dynamically allocates labor between:
- producing consumption goods,
- and investing in human capital accumulation.

To solve the problem, the project implements:

- Dynamic Programming via **Value Function Iteration**,
- **Policy Evaluation** and **Greedy Policy Improvement**,
- Reinforcement Learning-inspired optimization procedures,
- and a **Deep Neural Network** trained to approximate the optimal transition dynamics.

The final model learns trajectories that converge toward the theoretical steady state of the economy.


## Model

Consider an agent who allocates her time between producing the consumption good C, and accumulating human capital H. The agent seeks to maximize her discounted utility, as captured by the following objective:

![Model](images/problem.png)

The production function reads in (i).
Normalizing the labor supply of the agent to one, the accumulation law for human capital is given by (ii), where 𝛿 is the depreciation rate of human capital, while 𝐿t is the share of the labor supply dedicated to the production of the consumption good.

We assume a CRRA Utility function: U(C) = C^(1-𝜎)/(1-𝜎).

## 2. Value function and optimal policy
The Bellman Equation of the agent is:

![Bellman Equation and Feasability set](images/bellman_equation.png)

We iteratively approximate the value function, reached by the following optimal policy function:

![Value Function](images/value_function.png)

![Policy function](images/policy_function.png)

## 3. Reinforcement Learning Perspective

The environment evolves according to the human capital transition dynamics, while the agent learns policies that maximize cumulative discounted rewards.

Implemented concepts include:

- policy evaluation,
- policy iteration,
- greedy improvement,
- and approximate optimal control.

This bridges classical computational economics with modern AI optimization techniques.


## 4. Neural Network calibration to estimate the optimal path
A deep neural network is trained to approximate optimal state trajectories.

Instead of directly solving the Bellman equation at every step, the network learns dynamics that satisfy the theoretical equilibrium conditions.

The loss function minimizes residuals associated with:
- Euler equation

![Euler Equation](images/euler_equation.png)

- Accumulation law of human capital

![Accumulation law](images/accumulation_law.png)

- Initial stock of human capital

![Initial condition](images/initial_condition.png)

We estimate the optimal path using a deep neural network calibration with back propagation of the loss of the residuals associated with the three equations. We observe a convergence to the steady state of the model.

![Optimal path](images/optimal_path.png)
