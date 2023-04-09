---
title: scarlib-core
parent: Design
has_children: false
nav_order: 2
---

## Module: scarlib-core
The scarlib-core module implements the main functionalities and abstractions of the framework, including defining the main data structures and implementing the key algorithms. The abstractions are built around a set of concepts, with the System being the most important one. The System is a collection of agents that interact in a shared environment and are trained to optimize a global or local reward signal expressed by a reward function. The module includes two types of systems, which are CTDESystem and DTDESystem, both of which are commonly found in literature. Additionally, the module provides an implementation of the DQN algorithm for training agents.

To define a custom learning process, users only need to implement four elements, including the environment, agent state space, action space, and reward function. With this module, users can easily run a learning process in a simulated environment based on the platform.

![](https://i.imgur.com/25Zxlln.png)

To better understand the system's dynamics, it's helpful to explain some of the internals. Both systems use a training process that consists of multiple epochs, with each epoch consisting of a set of episodes. During each episode, agents receive the current state and execute an action that causes the environment to move to the next state. At the end of an epoch, the environment is reset, and agents are trained using the collected experience. In a CTDESystem, agents are trained in a centralized way, with a single central dataset and learner responsible for the training process and policy improvement. The DTDESystem works similarly, with each agent having its own dataset and learner.

| <img src="https://i.imgur.com/IezpICT.png" style="zoom:33%;" /> | <img src="https://i.imgur.com/bdnejKu.png" style="zoom:33%;" /> |

To support neural-network-based RL algorithms such as DQN, the module uses PyTorch as the de facto standard framework for building neural networks. The module relies on ScalaPy to interact directly with the Python API of PyTorch and other connected libraries. This integration involves setting up a Python environment and creating a Scala API that isolates what is necessary to access the Python ecosystem. In this case, DQN is the entry point for accessing Torch.

![](https://i.imgur.com/vE6THrj.png)