---
layout: default
title: Training Iterations
nav_order: 2
parent: RL training
---

# Training Iterations
{: .no_toc }


1. TOC
{:toc}

---

## Introduction
The following sections record every major training iterations we have made to train our hippos. It includes a detailed record of each parameter, our observations and our reasoning for the next iteration
### Environment


Hippo Number: 3

Crocodile Number: 1

Fish Number: 15

### Crocodile Rewards
We are using a pre-trained crocodile agent to train against the hippo agents.
Its rewards are the following:
Bite Hippo: 0.1
Eat Hippo: 1

### Hippo Speed
Hippo speed: 2

---

## Iteration 1: Abusive Hippos

### Reasoning
We want to train the hippo to be able to actively seek for fish but also help save another hippo when it is bitten by the crocodile. This is the first iteration and the numbers are set in a more or less random manner.

### Rewards
Eat Fish:1

Bitten: -1

Save other hippo: 2

Eaten: -1

Enter Crocodile Zone (Bigger collider around crocodile) when crocodile is not eating: -0.1

### Time
Struggle Time (Time between crocodile biting a hippo and the hippo being eaten): 10s

Crocodile Freeze Time
(Time when a hippo saves the bitten hippo, the time that the crocodile can't move): 2s

### Curricula 
No curricula
Crocodile speed: 1.5

### Training Time
20 ~ 30mins

### Observation
At first, the crocodile was able to eat all hippos.
However, towards the end of the training, the hippos learned to game the system. They would gather around the crocodile so they can keep saving each other and getting the big reward.

---
## Iteration 2: Selfish Hippos

### Reasoning
From previous training, though interesting, the hippos would game the system and not really behave in a more dynamic way. We suspect that was due to the really high reward associated with saving other hippos and the relatively small punishment for being bitten. 
In order to prevent them from abusing the system and viewing the helping mechanics as the best strategy. We tried to tweak the data in the following way:
- Decrease the Saving reward
- Increase the biteen punishment
- Decrease the struggle time (to make it less easy to save)
- Decrease the freeze time
- Increase Fish reward to give them more incentive to search for food as their main behavior"


### Rewards
Eat Fish:1.3

Bitten: -1.5

Save other hippo: 1.5

Eaten: -1

Enter Crocodile Zone (Bigger collider around crocodile) when crocodile is not eating: -0.1

### Time
Struggle Time (Time between crocodile biting a hippo and the hippo being eaten): 7s

Crocodile Freeze Time
(Time when a hippo saves the bitten hippo, the time that the crocodile can't move): 2s

### Curricula 
"thresholds": [ -0.1, 0.7, 1.7, 3, 1.7, 2.7, 2.7, 4.5, 5],
"crocodile_speed": [ 0.1, 0.5, 0.5, 0.5, 0.5, 1.0, 1.0, 1.5, 2, 2 ]

### Training Time
2.5h

### Observation
The hippo would run away from crocodile when approaching. It will seek food in safe areas(further from crocodile). At some point, they would hide in the corner of the island to hide from the crocodile. They will still try to go out for fish but seem pretty reluctant.
The helping mechanism is rarely triggered.

---
## Iteration 3: Extreme Rewards and Punishments

### Reasoning
We want to maximize the punishment of being bitten and also the rewards of being saved at the same time to see whether it would be different from the first iteration.

### Rewards
Eat Fish:1.3

Bitten: -2

Save other hippo: 2.5

Eaten: -1

Enter Crocodile Zone (Bigger collider around crocodile) when crocodile is not eating: -0.1

### Time
Struggle Time (Time between crocodile biting a hippo and the hippo being eaten): 7s

Crocodile Freeze Time
(Time when a hippo saves the bitten hippo, the time that the crocodile can't move): 2s

### Curricula 
"thresholds": [ -0.1, 1.7, 3, -0.1, 1.7, 3, -0.1, 1.7, 3],
 "crocodile_speed": [ 0.5, 0.5, 0.5, 0.5, 1.0, 1.0, 1.0, 1.5, 1.5, 1.5 ]

### Training Time
100mins

### Observation
Different from the previous training, we try to increase the rewards by saving the other hippos as well as giving more punishment while being bitten by the crocodile. We want to see whether hippos will tend to help the hippos more or to hide from the crocodiles. The results show that even though sometimes hippos are hiding from the crocodile, hipps tend to get around the crocodile and abuse it more. Because the positions of different animals are randomly generated, when 2 out of 3 hippos were eaten by the crocodile at the beginning, the last hippo will not last long. 

---
## Iteration 4: Same Rewards

### Reasoning
We want to see what decision hippo will make when the rewards of eating a fish is exactly the same as saving a hippo. However, we found out that if this is the case, the hippo will not help with each other any more. They are more focused on self-saving, hiding from crocodile, and running away from crocodile. This training shows the selfishness of the hippos and the result is not desirable.

### Rewards
Eat Fish:1.5

Bitten: -1

Save other hippo: 1.5

Eaten: -1

Enter Crocodile Zone (Bigger collider around crocodile) when crocodile is not eating: -0.1

### Time
Struggle Time (Time between crocodile biting a hippo and the hippo being eaten): 7s

Crocodile Freeze Time
(Time when a hippo saves the bitten hippo, the time that the crocodile can't move): 2s

### Curricula 
"thresholds": [ -0.1, 1.7, 3, -0.1, 1.7, 3, -0.1, 1.7, 3],  
"crocodile_speed": [ 0.5, 0.5, 0.5, 0.5, 1.0, 1.0, 1.0, 1.5, 1.5, 1.5 ]

### Training Time
45mins

### Observation
We want to see what decision the hippo will make when the rewards of eating a fish is exactly the same as saving a hippo. However, we found out that if this is the case, the hippo will not help with each other any more. They are more focused on self-saving, hiding from crocodile, and running away from crocodile. This training shows the selfishness of the hippos and the result is not desirable.

---
## Iteration 5: Well balanced

### Reasoning
Using the iteration 2’s training result, though the hippos would runaway from hippos, they would rarely help eachother out
They also seem very reluctant to go out for food when the crocodile is around and tend to hide in corners. We want to tweak the rewards to still encourage the helping mechanism but also be more brave when seeking out for food. We also trained it in the new map where there are more rock obstacles to see how they perform. 
- We increased the struggle time and crocodile freeze time slightly to give them enough time to rescue other hippos
- We increased the reward of helping back to 2 to encourage more helping
- The punishment of being bitten remains the same


### Rewards
Eat Fish:1.3

Bitten: -1.5

Save other hippo: 2

Eaten: -1

Enter Crocodile Zone (Bigger collider around crocodile) when crocodile is not eating: -0.1

### Time
Struggle Time (Time between crocodile biting a hippo and the hippo being eaten): 7s

Crocodile Freeze Time
(Time when a hippo saves the bitten hippo, the time that the crocodile can't move): 2s

### Curricula 
"thresholds": [ -0.1, 1.7, 3, -0.1, 1.7, 3, -0.1, 1.7, 3], 
"crocodile_speed": [ 0.1, 0.1, 0.1, 0.1, 0.5, 0.5, 0.5, 1.0, 1.0, 1.0 ]

### Training Time
1h40min

### Observation
The hippo has very interesting behaviors under different situations.
They are pretty good at finding and collecting the fish.
They would also runaway from the crocodile when it is chasing them and hide behind rocks
When a hippo is bitten, it is more likely to have a nearby hippo help it out. If the other hippos are too far away, they tend to not choose to approach and attempt to help.
If they are gathered in a corner. They would be more likely to temporarily "abuse" the crocodile(as in, the go in circles to keep gathering rewards) many of the time caused by one of the hippos being stuck in the environment's corner. But if they end up in more open spaces, they would stop the abuse and start to flee

The start position between the hippos and the environment would affect their decisions and behaviors


