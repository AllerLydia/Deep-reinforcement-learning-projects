# Project 2: Continuous Control

In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of the agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1. The entire implementation was done in PyTorch. 
  

## Algorithm

The algorithm is an actor-cirtic method - combines TD estimates and Policy-based. TD estimates uses value-based method, Policy-based methods uses Monto-Carla estimates. Actor-critic methods uses actor as neural network to update the policy, and critic as another neural network, to help train the actor. Actor-critic uses critic to updated rewards for actor instead of update reward in the environment. 
In vanilla policy gradients, the rewards accumulated over each episdoe is the average reward of all the hisotrical episode, Then perform gradient ascent. 


This project uses 20 agents and DDPG for agent training - 
- **Fixed targets**: two - one for actor, one for critic;
- **Soft Updates**: In DDPG, a soft update method is used to update the weight instead of DQN where all the weights from the local networks after a certain number of epochs;
- **Experience Replay**: Introduced to stabilize training. 


### Hyperparameters



| Hyperparameter                      | Value |
| ----------------------------------- | ----- |
| Replay buffer size                  | 1e6   |
| Batch size                          | 1024  |
| $\gamma$ (discount factor)          | 0.99  |
| $\tau$                              | 1e-3  |
| Actor Learning rate                 | 1e-4  |
| Critic Learning rate                | 3e-4  |
| Update interval                     | 20    |
| Update times per interval           | 10    |
| Number of episodes                  | 3000  |
| Max number of timesteps per episode | 1000  |
| Leak for LeakyReLU                  | 0.01  |


## Results

  Agent is able to achieve average of 30.0 scores, the agent solved the environment at 158 eposide. 


## Ideas for improvement

- Saw other projects using stochastic process in the agent, will be fun to explore as well.
- Other algorithms like - TRPO, PPO, A3C, A2C might be interesting to try. 

  
