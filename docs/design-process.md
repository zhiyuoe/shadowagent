---
layout: default
title: Design process
nav_order: 4
---

# Design process
{: .no_toc }

Our design sprints went through iterative stages from pre-production to production.
{: .fs-6 .fw-300 }


1. TOC
{:toc}

---

## Ideation

During ideation stage, we researched the potential applications of enhancing the relationship and interaction and came up with six ideas.<br/>
![capture 12345](https://user-images.githubusercontent.com/58717137/70496209-ab1d7200-1ac3-11ea-8f94-3df9d29021fc.PNG)


---

## Tech exploration

After learning the concept of RL, we trained the board to balance the ball, first we could see the amount of time we spent to train the model will really make a difference of the performance. Also, If we trained at the smaller board and put it at the bigger board environment, the ball tempts to not fall off since it is restricted when it trains. From this, we learned that environment is also an important factor in RL.<br/>
![techexploration](https://user-images.githubusercontent.com/58717137/70496564-e2405300-1ac4-11ea-998a-931391e6dd5e.jpg)](https://www.youtube.com/watch?v=11CwRzjL_c0&feature=youtu.be)



---

## Research findings

- RL as an environment is good for observing obvious changes effectively.
- The competing relationship between RL agents and players gets easily fall into the Good-old-fashioned-AI's application. 

---

## Design direction

- A coop game where RL agent and the player influence each other with a purpose.
- RL and player collaborate to solve puzzles together.

---

## Stage 1

### Hippo demo

#### Keywords

`RL as an environment`

#### Design

The player uses fish to attract bad hippos to get through the river. There are two different kinds of hippos in our current stage. Good hippos are the peaceful ones that just stay stationary inside the scene; bad hippos are the panic ones that want to eat the fish.

#### Lesson learned 
- Keep designing more elements into the current scene until it reaches its limit. when the environment is too chaotic for the player to control.

---

### Chicken demo

#### Keywords

`Asymmetrical information and communication`

#### Design
We set up a scenario of Imagining a jungle world where you and your friend are roleplaying two birds. You two have to go through a series of stairs to win. However, both of you can only see your partner’s stairs ahead, not yourselves’. You must take turns to jump and rely on your partner to give instructions. You two are allowed to communicate through limited yet creative methods like sending emojis and making sounds. 


#### Lesson learned 
- It’s unrealistic to have a human player keeps playing the game for a long period of time to train the RL agent. The PlayerAI system is a simulated version of the human player designed to train against the RL system on a reinforcing basis.

- To mimic the complexity of player behavior, the PlayerAI is constructed with variables in Movement and Communication based on the game mechanic. Then, by adjusting the parameters for example vision, reaction time, expertise, we generate 3 types of Preference as the input source of RL system.

[View Full Documentation](https://docs.google.com/document/d/1B3o1PSnI4Q-JMemKxr71XEj3zGQ49tZjKVkPRFIInfo/edit?usp=sharing)

### Penguin demo

#### Keywords

`Pathfinding`

#### Design
Thie demo is about the parent penguin is trying to find the fish and to feed its baby. What if we are the mother nature and we are trying to stop the adult penguin from finding the fish and feeding the child, without killing them. 

#### Lesson learned 
- Since the goals of each individuals are single and direct, it is not obvious how RL can play an important role in the gameplay.

- Adding complexity to the scen will help distinguish RL from the hard-coding NPC.


---

## Stage 2

### Hippo with food preference

#### Keywords

`Layers of complexity on individual behaviors`

#### Design
- Add multiple goals to the hippo, and have the hippo physical structure changes. 

- Switch agent's goals during the gameplay or there are other agents with totally different goals.

#### Lesson learned

- During implementing phase, we encountered some questions like, when the system becomes complicated, it starts to become hard to tune the parameters in order to get the results we want for the RL agent. Also, once there are a new component add into the environment, the system need to be retrained.

- When individual behaviors' layers becomes more and more, it was not obvious how the behaviors were influenced by the parameters in the scene. It was also too chaotic to observe.

- A new direction - establish a triangular relationship to create a dynamic system.

---

## Stage 3

### Cat power system

#### Keywords

`Build complexity on relationships and individual goals` `Power dynamics`

#### Design

This idea is inspired by the real-life cat’s social hierarchy. Cats choose food according to their power rank in their community. The player is a newcomer cat and is trying to survive, understand the rules, and disrupt the power dynamics. In this idea, all the cats, except the player, are all RL agents. We try to avoid the frustrations and limitations that are caused by the pathfinding behavior in the previous hippo demo. 

#### Challenges
We found out that even though sometimes the hippo has made a decision of where to go, the hippo has trouble to reach to its destination because of pathfinding. We tried to find a way to show the decisions that RL agents have made more clearly. This Cat Hierarchy game could solve this struggle.

#### Lesson learned
- We only have two weeks left before the soft opening and it take s along time to tune the parameters and train the RL agents, we decided to compromise our ideas into our current hippo demo.

---

## Stage 4

### Fish-Hippo-Crocodile ecosystem

#### Keywords
`Integration` `Triangular relationship` `Pathfinding` `Multiple rewards`

#### Challenges

Due to the limited time left, and in order to get the obvious results effectively, we reverted back to the previous layer that hippos only eat one food. With only one kind of food, players can observe the hippo’s behavior more clearly. Then, we add one more RL agent, the Crocodile, to eat the hippo.

#### Design

The hippo will get rewards by eating the fish as well as trying to avoid the crocodile to prevent punishment. Hippos need to decide what they need to do next according to their rewards and punishments.

Besides adding another RL agent, we also want hippos to have multiple rewards that will trigger interesting and unexpected behaviors between hippos. We set that hippo allies will have time to save the bitten hippo before the crocodile catches it and eats it.

The decision point is that when the individual reward is smaller than the group reward, the hippo allies will choose to save the hippo in danger. At the same time, if the bitten hippo does not get helped, the hippo will receive a bigger punishment after a certain period of a struggle time.

---
