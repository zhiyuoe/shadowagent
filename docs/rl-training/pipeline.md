---
layout: default
title: Pipeline
nav_order: 1
parent: RL training
---

# Pipeline
{: .no_toc }


1. TOC
{:toc}

Introduction
---
We used the Unity ML Agents plugin to incorporate Reinforcement Learning into our project. This section will present the different components of the plugin and how we specifically used them in order to train our agents.

Area
---
`Area` defines the training environment's initialization, reset specifics, and other environment-related features. 

In our case, the environment is the pound that the hippos reside in. 
At initialization, this class will randomly place fish and hippos within the environment.
A list of fishes and a list of hippos track the objects present in the environment and handles properly in the event of adding and deleting animals.

When the reset condition is triggered, it will handle it properly by deleting all remaining elements in the environment and randomly placing new ones just as the initialization process.
