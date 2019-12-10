---
layout: default
title: Lessons Learned
nav_order: 8
---


# Lessons Learned
{: .no_toc }

Designing and developing games with reinforcement learning can be exciting and unpredictable. From our semester-long design process, we have learned a few lessons from our emerging design patterns. 

{: .fs-6 .fw-300 }


1. TOC
{:toc}

---

## Learnings<br/>

### Break up complexity<br/> 
When you go into a more complex system of the agent, try to design interrelated relations between multi-agents and try to avoid complicated systems built on top of one agent, which might just lead to chaos. Also, in one environment, if you have agents with similar rewards and punishments, this might lead to chaos as well since it's hard to tell why they make a certain decision over another one.
### Don’t frustrate the player<br/> 
Know how to balance the unpredictability and uncertainty in order not to frustrate the player. Also, the game genre that requires a stable state might not be suitable for RL to use. And it requires prototyping out the result to see.    
### Programmer is a trainer<br/> 
Unlike a normal programmer, you implemented the design directly. The programmer is also a trainer and designer. The programmer has to set different parameters that will influence the result and iterate the numbers for the training session.
### Let the fun emerge<br/> 
How to make good use of the RL agent is important. The designer needs to make sure that the player feels they emerge in the game.
### State machines are okay<br/> 
The game that you are building does not necessarily have to be only using reinforcement learning, try to combine with different methods, and including the traditional state machine is also good.
### Engage the player<br/>
The player would probably get confused about the agent's behavior since it's hard to see their decision-making process directly. It's important to design visual aids or efficient UI to give a hint to the agent's behavior in order to improve player engagement.

---
## Design process with reinforcement learning<br/>

### Standard game design process<br/> 
A standard game design process looks like the image underneath that you have the uncertainty in the beginning, and you define the goals and problems clearer and clearer until the end of the production stage.<br/>
<img src = "https://user-images.githubusercontent.com/58717137/70498197-79f47000-1aca-11ea-8cdc-ce1e058f7f39.PNG" width= "700">


### Our design process<br/>
Due to the characteristics of the unpredictability of reinforcement learning. Our projects seem something more like this that we have the uncertainty of designing the game all the time, and along the way, we pivot to a lot of different directions and try out a bunch of stuff that could work with RL.<br/>
<img src = "https://user-images.githubusercontent.com/58717137/70499189-744c5980-1acd-11ea-8838-71d3256bfbc0.png" width= "520">




---
## Game designer's toolkit 

### 1. Start with something simple and small
Start with a doable RL demo or one simple mechanics.

### 2. Don't fix the rules and game mechanics too early
It's more important to figure out how much how RL does and How RL will influence the result, and therefore to have a well-planned plan or set rules are not necessary. 

### 3. Prototype the simple mechanics and document the result
Prototype the simple mechanics and see how RL could work. 

### 4. Iterate and adjust the result and prototype again
Based on the result of RL, brainstorm the idea, iterate the design, and prototype them again. 

With this process, you might be pivoting to a lot of different directions, and there is always uncertainty while designing since you don't know how much RL could work and what RL could result into, but get comfortable of staying at the uncomfortable and make good use of the unpredictable results that generate from reinforcement learning. 

---

