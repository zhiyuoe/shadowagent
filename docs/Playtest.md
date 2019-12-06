---
layout: default
title: Playtest
nav_order: 7
---


# Playtest
{: .no_toc }

This section records the observations of playtesting and how we iterate based on the them.
{: .fs-6 .fw-300 }


1. TOC
{:toc}

---

## Rewards change
We conducted playtest session for each of the brain individually.
### Helpful hippos
When we playtest for the helpful hippos, we found out that each player could clearly identify the behaviors of the hippos. Once the game start, they saw the hippos began to gather around the crocodile and abuse it. No matter how many fishes are put inside the pool, most of the hippos will continuously swim around the crocodile. Hippos are afraid of being caught by the crocodile, so what they do is to help each other all the time to prevent any freezing moment of hippos being bitten by the crocodile. Even though players find this observation interesting, there is a limited amount of space for them to control and manipulate the situation.


### Selfish hippos
When we only have selfish hippos inside the scene, players find hippos indifferent from each other. No matter how many fishes they put in or whether they put new hippos next to the bitten hippo, hippos swim away from each other and keep looking for food. Even though sometimes hippos are very close to the bitten hippo, they do not help each other. Players could observe this behavior, but the same as the helpful hippos, they find it hard to intervene.


### Balanced hippos
We then trained a balanced brain for the hippos. With this brain, sometimes hippos help each other from the crocodile and swim around the crocodile together. Sometimes they care about the fishes and not help each other. Players find it less interesting to observe because they could not merely control the behaviors of the hippos at all. Even though they put fishes next to the hippos, sometimes hippos each the fishes and sometimes they don't. 


---
## Brain change
Based on the feedback we got above, we find it is not fun enough to just put one brain inside the game. It is necessary to combine three brains together to make the gameplay experience more enjoyable and dynamic. We believe the relationship between the number of fishes and the number of hippos obey the natural selection theory in reality. We implemented the brain switch logic based on the ratio of fishes and hippos. When there are too many fishes, hippos have sufficient food resources, so they prefer to help each other other than just eating fishes. When there are very few fishes, hippos are afraid of being starving, so they prefer to eat fishes first, rather than helping each other. When there are about the right amount of fishes, they are in a balanced status that they help each other as well as eating fishes. Once we implemented this feature and began playtesting, we found players have more fun during the gameplay. They can now control the ecosystem by putting fishes and hippos. They could observe the changes in the behaviors based on the ration between fishes and hippos. The changes keep the interesting curve all the time.


---
## Environment change
### Map Shape
We also have tried different shapes of the maps. We first put the hippos in a round pool. We then realize that because there is a 360 degree of freedom for the hippos to move around, sometimes it might be too tricky for the hippos' pathfinding behaviors. 
We then put hippos inside a square pool and re-trained them. Playtesters find it too easy and less dynamic of hippo's behaviors. So finally, we decide to put them back to a smaller round pool with a longer training time to help hippos identify the different elements in the environment.

### Rock
In the adventure mode, we preset some rocks inside the scene and also give freedom of players to put more rocks inside the scene. We designed in this way to increase the difficulty of pathfinding for both hippos and the crocodile. Inside the training session, hippos learned to hide from the crocodile behind the rocks. The crocodile cannot see the hippos behind the rocks. Playtesters used rocks to stop the crocodile from chasing the hippos as well as to help hippos hide from the crocodile.


---
## Player intervention
The game is designed and iterated to provide enough intervention for the players. Inside the final build, players could intervene the environment and RL agents with rocks, fishes, and more hippos. They can change and observe the behaviors of RL agents not only by putting more rocks inside the scene to change the environment, as well as by putting more fishes and hippos to manipulate the ecocystsem.
