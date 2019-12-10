---
layout: default
title: Game Design
nav_order: 5
---

# Game Design
{: .no_toc }

Hippo Spring is a sandbox game that simulates a set of natural behaviors and chain relationships commonly found among animals and predators. By using player intervention to interrupt and change the environment states, this interactive environment brings unexpected results which surprise the player in a good way.
{: .fs-6 .fw-300 }


1. TOC
{:toc}

---

## Story
In this game, a crocodile at large is invading the peaceful baby hippo spring. The hippos are in danger of being eaten by the crocodile. Meanwhile, the hippos are always chasing after food to keep alive.

The zookeeper looking for the crocodile is on his way to the spring to rescue the hippos. He has 3 mins left to come. So he asks the player to help protect the hippos for a while.

---
 
## Mechanics
Players experiment with different strategies to help the hippo to eat fish while avoiding the crocodiles.

### Sandbox Simulation
Hippo Spring simulates the food chain relationships using Fish - Hippo - Crocodile in the water. It also stimulates the resource management dilemma in the conflict between individual goals and group rewards.

---

### Player intervention
In this simplified ecosystem, a player changes the environment states by adding a variety of objects. Based on their observation of the rules, they decide what purpose, how much, when, and where to put in. Their goal is to maximize the hippos alive, protect them away from being eaten by predators.

---

### 2 Modes
In order to showcase all the design and research results, the game features Adventure mode and Sandbox mode.

#### Adventure mode
Adventure mode is a goal-oriented game where players have a clear task to maximize the hippos and keep them alive before the time runs out. The game is wrapped within a simple story of rescuing hippos. To win or lose depends on if there is a hippo left in the spring within 1.5 mins.

This mode has a map with clear paths formed by rocks with limited adjustment space, which encourages the player to focus on observing and reacting to the characters' behaviors. The number of objects controlled by the players was limited to keep a balanced level of difficulty. 

#### Sandbox mode
Sandbox mode is an experimental space where players can unleash their creativity to build their own map into any layouts. There are no limits to the amount of objects, no win, or lose conditions. This mode allows free observations in an open-world setting. 

---

## Characters and Relationships

The mutually influenced characters co-creates a dynamic environment.

---

### Fish

Fish is the food for the hippo. It serves as the most basic parameters for players to control and influence the environment. 

---

### Hippo (agent)

Hippos are trained pathfinding agents. Their goal is to find and eat fish and hide away from the crocodile. Sometimes, they will help other hippos in danger against the crocodile.

---

### Dynamic hippo states (agents with different brains)

Hippos have three states: Normal, Selfish, and Helpful. 

#### Normal

`<Normal state>` were trained to have a balanced decision-making possibility to choose between saving another hippo in danger and chasing after fish for food. It sets as the initial state of the game.

#### Selfish

`<Selfish state>` were trained to be more likely to ignore a hippo friend in danger and chase for food. It reflects a mindset that when food resources are in short supply, individuals tend to be selfish and greedy.


#### Helpful

`<Helpful state>` were trained to be more likely to help a hippo friend in danger and ignore the food. It represents the altruistic characteristics of group society.

---

### Hippo-fish ratio

Inspired by the demand-supply relationships often seen in the resource management scenario, the dynamic hippo states were designed to be controlled together by the amount of hippo and the amount of fish. For example, when fish resources were sufficient for the number of hippos in the spring, hippos change to `<Helpful state>.`

We set up thresholds of ratio as the boundaries between Normal, Selfish, and Helpful states. As the player drags more objects into the spring, or as the fish gets eaten by the hippos, or as the hippos get eaten by the crocodile, they can observe the change happening to the hippos. 

---

### Crocodile (agent)

Crocodile is a trained pathfinding agent and the predator of the hippo. It chases and eats hippo in the scene. Adding the crocodile into the game makes hippos' goal diverse. It can scare away the hippo chasing food, as well as distracting hippos from choosing between helping others or ignoring them.

---

### Zookeeper
Zookeeper is the help-asker in the game. It serves as an initial prompt to invite the player into the game with a clear motivation and strong empathy. 

---

## Interaction
The interaction between players and the environment system is the core that makes this game playable and playful.

---

### Drag and drop
The player can add drag and drop objects to add to the environment system directly in real-time. Combining the pathfinding behaviors of the agents, these actions affects not only the number of obejcts, but also the states, goals, and decision-making results of the agent. Below are possible results happening to the system
 
 
| Actions               | Influences                        | Potential results                                    |
|:----------------------|:----------------------------------|:-----------------------------------------------------|
| Drag and drop fish    | Affecting hippo-fish ratio        | Change the hippo states                              |
|                       | Attracts hippos to come           | Change agents' moving directions, decisions and goals|
| Drag and drop a hippo | Affecting hippo-fish ratio        | Change the hippo states                              |
|                       | Bring hippo close to crocodile    | Change agents' moving directions, decisions and goals|
| Drag and drop a rock  | Change the path layout            | Change agents' pathfinding movements                 |

---
 
## Strategies

We expect players to experiment with different strategies to help the hippo to eat fish while avoiding the crocodiles and try to figure out how this dynamic relationship system works.

### Group of hippos abusing the crocodile
<img src = "https://user-images.githubusercontent.com/58717137/70496834-f6388480-1ac5-11ea-9850-0b99c5e98187.png" width= "520">

---

### Trap the crocodile with rocks
<img src = "https://user-images.githubusercontent.com/58717137/70496869-18320700-1ac6-11ea-85b6-b01641d13764.png" width= "520">

---

### Send over hippos to rescue their friend
<img src = "https://user-images.githubusercontent.com/58717137/70496885-25e78c80-1ac6-11ea-9ca1-53607ee10d8b.png" width= "520">

---

### Use fish to guide way for hippos
<img src = "https://user-images.githubusercontent.com/58717137/70496899-339d1200-1ac6-11ea-86e4-0ce198fff983.png" width= "520">

---


 
 
 
 

