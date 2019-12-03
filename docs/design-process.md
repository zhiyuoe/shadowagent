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

During ideation stage, we researched the potential applications of enhancing the relationship and interaction and came up with six ideas.

![6 ideas](img/6ideas.png)

---

## Tech exploration

After learning the concept of RL, we trained the board to balance the ball, first we could see the amount of time we spent to train the model will really make a difference of the performance. Also, If we trained at the smaller board and put it at the bigger board environment, the ball tempts to not fall off since it is restricted when it trains. From this, we learned that environment is also an important factor in RL.
https://youtu.be/
<a href="http://www.youtube.com/watch?feature=player_embedded&v=11CwRzjL_c0
" target="_blank"><img src="http://img.youtube.com/vi/11CwRzjL_c0/0.jpg" 
alt="tech demo" width="240" height="180" border="10" /></a>

---

## Findings

- RL as an environment is good for observing obvious changes effectively.
- The competing relationship between RL agents and players gets easily fall into the Good-old-fashioned-AI's application. 

---

## Design direction

- A coop game where RL agent and the player influence each other with a purpose.
- Starting from something small, and gradually build up complexity upon it.
- Establish a triangular relationship to create a dynamic system.