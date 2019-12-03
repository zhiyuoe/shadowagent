---
layout: default
title: Problem statement
nav_order: 2
---


# Problem statement
{: .no_toc }


The goal of the project is to present a delightful user experience by creating believable characters in a game using existing machine learning tools to train different behaviors of Non-Player Characters (NPCs). The primary question we would like to explore is "How can trained RL agents create a delightful game experience for players".
{: .fs-6 .fw-300 }


1. TOC
{:toc}

---

## Background

Reinforcement learning (RL) is a relatively new machine learning method which learns the best actions based on reward or punishment in an environment. In games, it has been applied as NPCs to compete with human players (AlphaGo), simulate an realistic environment (Fortnite), and imitate player behaviors (FIFA). These applications brings exciting possibilities of new formats of player-computer interactions and new game genres powered by a highly-human-like trained agent.

---

## Challenges

However, game designers starts to question whether it is actually fun, delightful, or emotional to play with a “machine” for players. In competitive games, although the algorithms prove to train an powerful and skillful enough agent such that it can beat human competitors (AlphaGo), players tend to get bored of competing with a superpowerful computer that is unbeatable. Watching two machines competing would be tedious after a while either, since almost no empathy were aroused.

Likewise, game developers were both excited and skeptical about implementing RL into the design process, since giving control to this self-reinforcing tool would mean losing controls over the game results. Specifically, storytelling-based interactive narratives were systematically structured of branches of plots, whose game mechanics are highly relied on state machines. This genre usually requires the game designers to write each branches in a consistent and meaningful way, which might not be what a RL-training approach is good at.

Lastly, Reinforcement learning trained results tend to be unpredictable and unexpected. Since human cannot easily interpret how RL algorithm “computes” while training, machine learning engineers use it typically to explore emerging unknown assumptions based on observations from the aggressively generated results. By micro-adjusting parameters, mixing combinations and variations, a validate model is decided when there are obvious multivariate relations. It seems more a inductive methodology than a deductive one. This is somehow to the opposite of the traditional game design process.

In short, the conflict between reinforcement learning and designing a delightful game seems natural and inevitable. How might we tackle this challenge in this project?

---

## Opportunites

### RL 