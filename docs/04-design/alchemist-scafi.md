---
title: alchemist-scafi
parent: Design
has_children: false
nav_order: 2
---

## Module: alchemist-scafi

We have developed an additional module, called alchemist-scafi (Figure 6), which integrates two important tools, Alchemist and ScaFi. This integration allows for the execution of the learning process in an aggregate computing context, which is a significant contribution. With this integration, we provide a usable system that brings the many-agent RL community closer to the use of this simulator and paradigm, which can describe various environments, from robotic swarms to data centers. The specification of a learning system remains the same, with the addition of two new elements: the specification of the Alchemist simulation and the implementation of the ScaFi-based logic. The Alchemist simulation is defined by passing a ScaFi class as a program, which contains aggregate programming code. A molecule containing the current action to be taken (a subtype of the Action class) is injected by a learner that contains the RL policy to advance the training process. Additionally, the aggregate program evaluates the environment state (which must be a subtype of State) using computeState and inserts it into the state molecule, which is used by the learner to update the policy.

![](https://i.imgur.com/P6k4KAO.png)