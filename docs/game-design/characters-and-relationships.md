---
layout: default
title: Characters and relationships
nav_order: 3
parent: Game design
---

# Characters and relationships
{: .no_toc }

The muturally influenced characters co-creates a dynamic environment.
{: .fs-6 .fw-300 }


1. TOC
{:toc}

---

## Fish

Fish is the food for hippo. It serves as the most basic parameters for players to control and influence the environment. 

---

## Hippo (agent)

Hippos are pretrained pathfinding agents. Their goal is to find and eat fish and hide away from crocodile. Sometimes, they will help other hippos in danger against the crocodile.

---

## Dynamic hippo states (agents with different brains)

Hippos have 3 states: Normal, Selfish, and Helpful. 

### Normal

`<Normal state>` were trained to have a balanced decision-making possibilities to choose between saving another hippo in danger and chasing after fish for food. It sets as the initial state of the game.

### Selfish

`<Selfish state>` were trained to be more likely to ignore a hippo friend in danger and chase for food. It reflects a mind-set that when food resources is in short supply, individuals tend to be selfish and greedy.


### Helpful

`<Helpful state>` were trained to be more likely to help a hippo friend in danger and ignore the food. It represents the altristic characteristics in a group society.

---

## Hippo-fish ratio

Inspired by the demand-supply relationships often seen in resource management scenario, the dynamic hippo states were designed to be controlled together by the amount of hippo and the amount of fish. For example, when fish resources were sufficient for the amount of hippos in the spring, hippos change to `<Helpful state>`.

We set up thresholds of ratio as the boundaries in between Normal, Selfish and Helpful states. As player drag more objects into the spring, or as the fish gets eaten by the hippos, or as the hippos get eaten by the crocodile, they can observe the change happening to the hippos. 

---

## Crocodile (agent)

Crocodile is a pretrained pathfinding agent and the predator of hippo. It chases and eats hippo in the scene. Adding the crocodile into the game makes hippos' goal diversed. It can scare away the hippo chasing food, as well as distracting hippos to choose between go helping others or ignoring them.

---

## Zookeeper
Zookeeper is the help-asker in the game. It serves as a initial promt to invite the player into the game with a clear motivation and strong empathy. 