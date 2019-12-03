---
layout: default
title: Interaction
nav_order: 4
parent: Game design
---


# Interaction
{: .no_toc }

The interaction beteween player and the environment system is the core that makes this game playable and playful.
{: .fs-6 .fw-300 }


1. TOC
{:toc}


## Drag and drop

Player can add drag and drop objects to add into the environment system directly in real-time. Combining the path-finding behaviors of the agents, thhese actions not only affects the amount of obejcts, but also the states, goals, and decision-making results of the agent. Below are possible results happening to the system.


| Actions               | Influences                        | Potential results                                    |
|:----------------------|:----------------------------------|:-----------------------------------------------------|
| Drag and drop fish    | Affecting hippo-fish ratio        | Change the hippo states                              |
|                       | Attracts hippos to come           | Change agents' moving directions, decisions and goals|
| Drag and drop a hippo | Affecting hippo-fish ratio        | Change the hippo states                              |
|                       | Bring hippo close to crocodile    | Change agents' moving directions, decisions and goals|
| Drag and drop a rock  | Change the path layout            | Change agents' pathfinding movements                 |

---