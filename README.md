# DICE_RL
Application of Reinforcement Learning on DICE model

This project borrows ideas from the Dynamic Integrated Climate-Economy (DICE) model by William Nordhaus, and used the initialization from the [Python Version of DICE model optimization](https://github.com/hazem2410/PyDICE). The Python Version is basically the same as [R Version of DICE model optimization](https://github.com/olugovoy/climatedice/tree/master/R), where more details can be discovered.

In this application, the Tabular Q-learning, Deep Q Network and Actor-Critic Algorithms are adopted. 

[Original DICE Model (Python)](https://github.com/linguo4/DICE_RL/blob/master/DICE.ipynb)

[Tabular Q-learning](https://github.com/linguo4/DICE_RL/blob/master/DICE_Tabular%20Q.ipynb) 
: Create a Q-table, and roughly choose actions simultaneously for the total 200 values of Miu and S over 100 years. The bounds for the Miu and S are not bounded perfectly and the action space is discrete, making the observation space discrete, as well.

[Deep Q Network_1](https://github.com/linguo4/DICE_RL/blob/master/DICE_DQN_1.ipynb) (Used Tensorflow 1.3)
: Choose the MIU and S at each step according to epsilon-greedy action policy from the replay buffer and calculate the reward at each step (even if the step doesn't reach 99). The state also incorporated step as an input. The action space is still discrete, but the result converge beyond 4400 after the epsilon reaches high.

[Deep Q Network_2](https://github.com/linguo4/DICE_RL/blob/master/DICE_DQN_2.ipynb) (Used Tensorflow 1.3)
: Use the initialization of MIU and S for 100 years for reward calculation, update the MIU and S at each step (looping over 100 years) according to epsilon-greedy action policy from the replay buffer and calculate the reward at each step. The action space is still discrete, and the result seems not converging.

[Actor-Critic Sample](https://github.com/linguo4/DICE_RL/blob/master/A2C%20Sample.ipynb) 
: A2C sample from [tensorflow official website](https://keras.io/examples/rl/actor_critic_cartpole/).


[Actor-Critic on Dice Model_1](https://github.com/linguo4/DICE_RL/blob/master/DICE_A2C_1.ipynb) (Used Tensorflow 2.0)
: A2C on DICE model. Choose MIU and S and output reward at each year. Choose action with Bivariate Normal Dist. Result changes between 4200 to 4400 and cannot reach 4500.

[Actor-Critic on Dice Model_2](https://github.com/linguo4/DICE_RL/blob/master/DICE_A2C_2.ipynb) (Used Tensorflow 2.0)
: A2C on DICE model. Use the initialization of MIU and S for 100 years for reward calculation, update MIU and S year by year and output reward over the updated 100 years' values. Choose action with Bivariate Normal Dist. Result converges to negative -1.34. 

[DDPG on Dice Model](https://github.com/linguo4/DICE_RL/blob/master/DICE_DDPG.ipynb) (Used Tensorflow 2.0)
: DDPG on DICE model. Choose MIU and S and output reward at each year. Choose action from the replaybuffer, then sample from two independent normal distribution (with choosen action as means) with decaying variances for miu and s. This algorithm behaves the best with the best convergence performance and solves the problem.
