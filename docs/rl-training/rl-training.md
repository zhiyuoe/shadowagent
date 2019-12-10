---
layout: default
title: RL Training
nav_order: 6
---

# RL training
{: .no_toc }
We follow the pipeline of Unity ML-agents plugin. During each iteration, we observe the behaviors of RL agents and change the parameters upon the observations. This section introduces the fundamental pipeline of Unity ML-agents and detailed explanations of each training iteration.
{: .fs-6 .fw-300 }


1. TOC
{:toc}

---
## Pipeline

### Introduction
We used the [Unity ML Agents](https://github.com/Unity-Technologies/ml-agents) plugin to incorporate Reinforcement Learning into our project. This section will present the different components of the plugin, how we specifically used them to train our agents, as well as a basic overview of our training process.

---
### Terms

#### Area
`Area` defines the training environment's initialization, reset specifics, and other environment-related features. 

In our game, the environment is the pound that the hippos reside in. 
At initialization, this class will randomly place fish, hippos, and the crocodile within the environment.
A list of fishes and a list of hippos track the objects present in the environment and handle properly in the event of adding and deleting animals.

When the reset condition is triggered, it properly handles it by deleting all remaining elements in the environment and randomly placing new ones just as the initialization process.

---

#### Agent
`Agent` is attached to a GameObject that is designed to be the RL agent. It defines the agent's rewards, observations, and actions. An agent is always associated with a brain.

##### Actions
The `actions` define what the RL agent is able to do. In our game, the hippos and the crocodile can only perform three actions: advance, turn left and turn right.
This simple action allows them to explore the space and trigger the different rewards within the environment.

##### Observations
The `observations ` defines what information the agent can receive in order to make its decisions. 
In our game, each hippo has a 180-degree ray perception that lets them recognize a predefined set of objects: fish, crocodile, rocks, and borders. The ray perception will return the closest valid object hit, their distance and direction relative to the hippo. The hippos know the relative direction and distance of the crocodile. They also know whether the crocodile is currently eating a hippo or not.

##### Rewards
The `rewards` is a crucial decision factor for the agents. We define the encouraged, and discouraged actions then assign specific values to them. It heavily influences the training results as the agent's sole goal is to maximize its rewards. 
In our game, the crocodile is awarded when biting a hippo, and completely eating one.
The hippo is awarded when eating fish as well as helping another bitten hippo. It is punished if it approaches the crocodile whenever it is not eating another hippo.

---

#### Academy
An academy orchestrates the agents and their decision making processes. It also handles the communication between the editor and the python API.
We would drag the agents' brains(hippo learning brain and crocodile learning brain) into the academy, and whenever we want to train a particular brain, we would tick the checkbox next to it. The academy also handles setting the curricula's parameters. In our case, that would be the speed of the crocodile. 

---

#### Brain
A `brain` controls the actual decisions of the agent according to observations. Roughly, `agent` sets the rules, and the `brain` executes according to the rules and the received information in different situations.

##### Player Brain
A `player brain` helps the developer to simulate the actions of an agent by mapping them to the keyboard. It permits developers to test out the agent script: whether the rewards are triggered in the correct situation.

##### Learning Brain
A `learning brain` is the actual one used to do the training. It can also host a pre-trained model to be integrated into the gameplay.

---

#### Curricula
A `curricula` is like a lesson plan during training. We define a set of rewards, goals, and parameters. Once a reward goal is achieved, we then move on to the next lesson, where usually the parameters and reward goals will be adjusted to greater difficulty.
In our game, we define the curricula's parameter is the speed of the crocodile. During training, it will gradually increase. We observed that establishing a curricula helps the training result as it avoids the hippo from failing too fast and allows it to improve gradually.

---

#### Training parameters
The `training parameters` are specific numbers used for training. They can greatly improve the training results or shorten the training time but at the cost of many trials and errors.

---
### Training Process
After defining all of the above terms. We would duplicate to around eight training areas to speed up the process. We would make sure they check the brain we want to train in the academy. We would type in a few commands in the terminal to associate the curricula and training id we want to use. After making sure that communication is established, we finally click play in the editor to kick off the training.

After the training, it would generate a .nn file, which is the pre-trained model, that we can drag onto the specified brain and test the results.

For more details on the training process and terms, please consult Unity ML-Agents' [documentation](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Readme.md).

---

## Training Iterations

### Introduction
The following sections record every major training iterations we have made to train our hippos. It includes a detailed record of each parameter, our observations and our reasoning for the next iteration

---

#### Environment

Hippo Number: 3

Crocodile Number: 1

Fish Number: 15

---

#### Crocodile Rewards
We are using a pre-trained crocodile agent to train against the hippo agents.
Its rewards are the following:
Bite Hippo: 0.1
Eat Hippo: 1

---

#### Hippo Speed
Hippo speed: 2

---

### Iteration 1: Abusive Hippos

#### Reasoning
We want to train the hippo to be able to actively seek for fish but also help save another hippo when it is bitten by the crocodile. This is the first iteration, and the numbers are set in a more or less random manner.

#### Rewards
Eat Fish:1

Bitten: -1

Save other hippos: 2

Eaten: -1

Enter Crocodile Zone (Bigger collider around crocodile) when the crocodile is not eating: -0.1

#### Time
Struggle Time (Time between crocodile biting a hippo and the hippo being eaten): 10s

Crocodile Freeze Time
(Time when a hippo saves the bitten hippo, the time that the crocodile can't move): 2s

#### Curricula 
No curricula
Crocodile speed: 1.5

#### Training Time
20 ~ 30mins

#### Observation
At first, the crocodile was able to eat all hippos.
However, towards the end of the training, the hippos learned to game the system. They would gather around the crocodile so they can keep saving each other and getting the big reward.<br/>
[![QeRDRVmtvhQhd](https://user-images.githubusercontent.com/58717137/70503002-35230600-1ad7-11ea-9bd7-2286e67ed009.jpg)](https://www.youtube.com/watch?v=QeRDRVmtvhQ&feature=youtu.be)<br/>
(Click on the video)

---

### Iteration 2: Selfish Hippos

#### Reasoning
From previous training, though interesting, the hippos would game the system and not really behave in a more dynamic way. We suspect that was due to the really high reward associated with saving other hippos and the relatively small punishment for being bitten. 
In order to prevent them from abusing the system and viewing the helping mechanics as the best strategy. We tried to tweak the data in the following way:
- Decrease the Saving reward
- Increase the bitten punishment
- Decrease the struggle time (to make it less easy to save)
- Decrease the freeze time
- Increase Fish reward to give them more incentive to search for food as their primary behavior."


#### Rewards
Eat Fish:1.3

Bitten: -1.5

Save other hippos: 1.5

Eaten: -1

Enter Crocodile Zone (Bigger collider around crocodile) when the crocodile is not eating: -0.1

#### Time
Struggle Time (Time between crocodile biting a hippo and the hippo being eaten): 7s

Crocodile Freeze Time
(Time when a hippo saves the bitten hippo, the time that the crocodile can't move): 2s

#### Curricula 
"thresholds": [ -0.1, 0.7, 1.7, 3, 1.7, 2.7, 2.7, 4.5, 5],
"crocodile_speed": [ 0.1, 0.5, 0.5, 0.5, 0.5, 1.0, 1.0, 1.5, 2, 2 ]

#### Training Time
2.5h

#### Observation
The hippo would run away from crocodiles when approaching. It will seek food in safe areas(further from crocodile). At some point, they would hide in the corner of the island to hide from the crocodile. They will still try to go out for fish but seem pretty reluctant.
The helping mechanism is rarely triggered.<br/>
[![uZYv4O7Ahichd](https://user-images.githubusercontent.com/58717137/70503122-9c40ba80-1ad7-11ea-8a3f-2c8719daf8a6.jpg)](https://www.youtube.com/watch?v=uZYv4O7Ahic&feature=youtu.be)<br/>
(Click on the video)

---

### Iteration 3: Extreme Rewards and Punishments

#### Reasoning
We want to maximize the punishment of being bitten and also the rewards of being saved at the same time to see whether it would be different from the first iteration.

#### Rewards
Eat Fish:1.3

Bitten: -2

Save other hippos: 2.5

Eaten: -1

Enter Crocodile Zone (Bigger collider around crocodile) when the crocodile is not eating: -0.1

#### Time
Struggle Time (Time between crocodile biting a hippo and the hippo being eaten): 7s

Crocodile Freeze Time
(Time when a hippo saves the bitten hippo, the time that the crocodile can't move): 2s

#### Curricula 
"thresholds": [ -0.1, 1.7, 3, -0.1, 1.7, 3, -0.1, 1.7, 3],
 "crocodile_speed": [ 0.5, 0.5, 0.5, 0.5, 1.0, 1.0, 1.0, 1.5, 1.5, 1.5 ]

#### Training Time
100mins

#### Observation
Different from the previous training, we try to increase the rewards by saving the other hippos as well as giving more punishment while being bitten by the crocodile. We want to see whether hippos will tend to help the hippos more or to hide from the crocodiles. The results show that even though sometimes hippos are hiding from the crocodile, hipps tend to get around the crocodile and abuse it more. Because the positions of different animals are randomly generated, when 2 out of 3 hippos were eaten by the crocodile at the beginning, the last hippo will not last long. 

---

### Iteration 4: Same Rewards

#### Reasoning
We want to see what decision the hippo will make when the rewards of eating a fish are exactly the same as saving a hippo. However, we found out that if this is the case, the hippo will not help with each other anymore. They are more focused on self-saving, hiding from the crocodile, and running away from the crocodile. This training shows the selfishness of the hippos, and the result is not desirable.

#### Rewards
Eat Fish:1.5

Bitten: -1

Save other hippos: 1.5

Eaten: -1

Enter Crocodile Zone (Bigger collider around crocodile) when the crocodile is not eating: -0.1

#### Time
Struggle Time (Time between crocodile biting a hippo and the hippo being eaten): 7s

Crocodile Freeze Time
(Time when a hippo saves the bitten hippo, the time that the crocodile can't move): 2s

#### Curricula 
"thresholds": [ -0.1, 1.7, 3, -0.1, 1.7, 3, -0.1, 1.7, 3],  
"crocodile_speed": [ 0.5, 0.5, 0.5, 0.5, 1.0, 1.0, 1.0, 1.5, 1.5, 1.5 ]

#### Training Time
45mins

#### Observation
We want to see what decision the hippo will make when the rewards of eating a fish are exactly the same as saving a hippo. However, we found out that if this is the case, the hippo will not help with each other anymore. They are more focused on self-saving, hiding from the crocodile, and running away from the crocodile. This training shows the selfishness of the hippos, and the result is not desirable.<br/>
[![LpRQM7NkOcMhd](https://user-images.githubusercontent.com/58717137/70503282-ed50ae80-1ad7-11ea-9dcc-ccc6c9e75e9e.jpg)](https://www.youtube.com/watch?v=LpRQM7NkOcM&feature=youtu.be)<br/>
(Click on the video)

---

### Iteration 5: Well balanced

#### Reasoning
Using the iteration 2’s training result, though the hippos would runaway from hippos, they would rarely help each other out
They also seem very reluctant to go out for food when the crocodile is around and tend to hide in corners. We want to tweak the rewards to encourage the helping mechanism still but also be braver when seeking out for food. We also trained it on the new map, where there are more rock obstacles to see how they perform. 
- We increased the struggle time and crocodile freeze time slightly to give them enough time to rescue other hippos
- We increased the reward of helping back to 2 to encourage more helping
- The punishment of being bitten remains the same


#### Rewards
Eat Fish:1.3

Bitten: -1.5

Save other hippos: 2

Eaten: -1

Enter Crocodile Zone (Bigger collider around crocodile) when the crocodile is not eating: -0.1

#### Time
Struggle Time (Time between crocodile biting a hippo and the hippo being eaten): 7s

Crocodile Freeze Time
(Time when a hippo saves the bitten hippo, the time that the crocodile can't move): 2s

#### Curricula 
"thresholds": [ -0.1, 1.7, 3, -0.1, 1.7, 3, -0.1, 1.7, 3], 
"crocodile_speed": [ 0.1, 0.1, 0.1, 0.1, 0.5, 0.5, 0.5, 1.0, 1.0, 1.0 ]

#### Training Time
1h40min

#### Observation
The hippo has very interesting behaviors under different situations.
They are pretty good at finding and collecting the fish.
They would also run away from the crocodile when it is chasing them and hide behind rocks
When a hippo is bitten, it is more likely to have a nearby hippo help it out. If the other hippos are too far away, they tend not to choose to approach and attempt to help.
If they are gathered in a corner, they would be more likely to temporarily "abuse" the crocodile(as in, the go in circles to keep gathering rewards) many of the time caused by one of the hippos being stuck in the environment's corner. But if they end up in more open spaces, they would stop the abuse and start to flee.

The start position between the hippos and the environment would affect their decisions and behaviors.<br/>
Trained in old map<br/>
[![Ju3O3gYAKT4hd](https://user-images.githubusercontent.com/58717137/70503443-43255680-1ad8-11ea-9d6c-e125e1e1a804.jpg)](https://www.youtube.com/watch?v=Ju3O3gYAKT4&feature=youtu.be)<br/>
(Click on the video)

However, after we trained the hippos in the new map, the collider issue doesn't exist any more.<br/>
Trained in new map<br/>
[![3fmvjX2ip7ghd](https://user-images.githubusercontent.com/58717137/70503609-9c8d8580-1ad8-11ea-8cb2-65215d846aee.jpg)](https://www.youtube.com/watch?v=3fmvjX2ip7g&feature=youtu.be)<br/>
(Click on the video)
