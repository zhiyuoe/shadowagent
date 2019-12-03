---
layout: default
title: Pipeline
nav_order: 1
parent: RL training
---

# Pipeline
{: .no_toc }


1. TOC
{:toc}

## Introduction
We used the [Unity ML Agents](https://github.com/Unity-Technologies/ml-agents) plugin to incorporate Reinforcement Learning into our project. This section will present the different components of the plugin, how we specifically used them in order to train our agents, as well as a basic overview of our training process.

---
## Terms

### Area
`Area` defines the training environment's initialization, reset specifics, and other environment-related features. 

In our game, the environment is the pound that the hippos reside in. 
At initialization, this class will randomly place fish, hippos, and the crocodile within the environment.
A list of fishes and a list of hippos track the objects present in the environment and handle properly in the event of adding and deleting animals.

When the reset condition is triggered, it properly handles it by deleting all remaining elements in the environment and randomly placing new ones just as the initialization process.

### Agent
`Agent` is attached to a GameObject that is designed to be the RL agent. It defines the agent’s rewards, observations and actions. An agent is always associated with a brain.

#### Actions
The `actions` define what the RL agent is able to do. In our game, the hippos and the crocodile can only perform three actions: advance, turn left, and turn right.
These simple action allows them to explore the space and trigger the different rewards within the environment.

#### Observations
The `observations ` defines what information the agent can receive in order to make its decisions. 
In our game, each hippo have a 180 degree ray perception that lets them recognize a predefined sets of objects: fish, the crocodile, rocks, and borders. The ray perception will return the closest valid object hit, their distance and direction relative to the hippo. The hippos know the relative direction and distance of the crocodile. They also know whether the crocodile is currently eating a hippo or not.

#### Rewards
The `rewards` is a crucial decision factor for the agents. We define the encouraged and discouraged actions then assign specific values to them. It heavily influences the training results as the agent’s sole goal is to maximize its rewards. 
In our game, the crocodile is awarded when biting a hippo, and completely eating one.
The hippo is awarded when eating fish as well as helping another bitten hippo. It is punished if it approaches the crocodile whenever it is not eating another hippo.

### Academy
An academy orchestrates the agents and their decision making processes. It also handles the communication between the editor and the python API.
We would drag the agents’ brains(hippo learning brain and crocodile learning brain) into the academy and whenever we want to train a particular brain, we would tick the checkbox next to it. The academy also handles setting the curricula’s parameters. In our case, that would be the speed of the crocodile. 

### Brain
A `brain` controls the actual decisions of the agent according to observations. Roughly, `Agent` sets the rules and the `brain` executes according to the rules and the received information in different situations.

#### Player Brain
A `player brain` helps developer to simulate the actions of an agent by mapping them to keyboard. It permits developers to test out the agent script: whether the rewards are triggered in the correct situation.

#### Learning Brain
A `learning brain` is the actual one used to do the training. It can also host a pre-trained model to be integrated in the gameplay.

### Curricula
A `curricula` is like a lesson plan during training. We define a set of rewards goals and parameters. Once a reward goal is achieved, we then move on to the next lesson where usually the parameters and reward goals will be adjusted to a higher difficulty.
In our game, we define the curricula’s parameter is the speed of the crocodile. During training, it will gradually increase. We observed that establishing a curricula helps the training result as it avoids the hippo from failing too fast and allows it gradually improve.

### Training parameters
The `training parameters` are specific numbers used for training. They can greatly improve the training results or shorten the training time but at the cost of many trials and errors.

## Training Process
After defining all of the above terms. We would duplicate to around 8 training areas to speed up the process. We would make sure the check the brain we want to train in the academy. We would type in a few commands in the terminal to associate the curricula and training id we want to use. After making sure that communication is established, we finally click play in the editor to kick off the training.

After the training, it would generate a .nn file, that is the pre-trained model, that we can drag onto to specified brain and test the results.

For more details on the training process and terms, please consult Unity ML-Agents’ [documentation](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Readme.md).


