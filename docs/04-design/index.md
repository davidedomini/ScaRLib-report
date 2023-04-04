---
title: Design
has_children: true
nav_order: 5
---

# Design

The main objective of this project is to provide an easy-to-use and robust tool for system specification. To achieve this goal, the framework incorporates numerous abstractions to model high-level aspects of the MARL domain, abstracting away low-level implementation details. The framework is composed of three primary modules: scarlib-core, alchemist-scafi, and dsl-core.

![](https://i.imgur.com/T1P6qVT.png)

## Module: scarlib-core

The scarlib-core module implements the main functionalities and abstractions of the framework, including defining the main data structures and implementing the key algorithms. The abstractions are built around a set of concepts, with the System being the most important one. The System is a collection of agents that interact in a shared environment and are trained to optimize a global or local reward signal expressed by a reward function. The module includes two types of systems, which are CTDESystem and DTDESystem, both of which are commonly found in literature. Additionally, the module provides an implementation of the DQN algorithm for training agents.

To define a custom learning process, users only need to implement four elements, including the environment, agent state space, action space, and reward function. With this module, users can easily run a learning process in a simulated environment based on the platform.

![](https://i.imgur.com/25Zxlln.png)

To better understand the system's dynamics, it's helpful to explain some of the internals. Both systems use a training process that consists of multiple epochs, with each epoch consisting of a set of episodes. During each episode, agents receive the current state and execute an action that causes the environment to move to the next state. At the end of an epoch, the environment is reset, and agents are trained using the collected experience. In a CTDESystem, agents are trained in a centralized way, with a single central dataset and learner responsible for the training process and policy improvement. The DTDESystem works similarly, with each agent having its own dataset and learner.



| <img src="https://i.imgur.com/IezpICT.png" style="zoom:33%;" /> | <img src="https://i.imgur.com/bdnejKu.png" style="zoom:33%;" /> |
| :----------------------------------------------------------: | :----------------------------------------------------------: |



To support neural-network-based RL algorithms such as DQN, the module uses PyTorch as the de facto standard framework for building neural networks. The module relies on ScalaPy to interact directly with the Python API of PyTorch and other connected libraries. This integration involves setting up a Python environment and creating a Scala API that isolates what is necessary to access the Python ecosystem. In this case, DQN is the entry point for accessing Torch.

## Module: alchemist-scafi

We have developed an additional module, called alchemist-scafi (Figure 6), which integrates two important tools, Alchemist and ScaFi. This integration allows for the execution of the learning process in an aggregate computing context, which is a significant contribution. With this integration, we provide a usable system that brings the many-agent RL community closer to the use of this simulator and paradigm, which can describe various environments, from robotic swarms to data centers. The specification of a learning system remains the same, with the addition of two new elements: the specification of the Alchemist simulation and the implementation of the ScaFi-based logic. The Alchemist simulation is defined by passing a ScaFi class as a program, which contains aggregate programming code. A molecule containing the current action to be taken (a subtype of the Action class) is injected by a learner that contains the RL policy to advance the training process. Additionally, the aggregate program evaluates the environment state (which must be a subtype of State) using computeState and inserts it into the state molecule, which is used by the learner to update the policy.

![](https://i.imgur.com/P6k4KAO.png)

## Module: dsl-core

We have developed a new module, which is an internal Domain Specific Language (DSL) for creating CMARL training systems in a more agile and flexible manner. Our goal is to bridge the gap between the MARL system designer's idea and the actual training system by providing a more efficient tool. To achieve this, we have used a typed DSL in Scala, which captures errors during compilation, rather than waiting for the actual system runs to intercept simple configuration errors.

```scala
class MyRewardFunction extends CollectiveRewardFunction:
override def computeReward(state: State, action: Action, nextState: State): Double = ...
```

The DSL provided is a simple facade to the abstractions shown in the scarlib-core module. To start a simulation (e.g., in Alchemist), the developer must first define a reward function that evaluates the current state of a specific agent compared to the current environmental condition. Additionally, they must decide which actions are supported by the agents living in the chosen system. As we are dealing with CMARL systems, we assume that all agents have the same action space. Thus, we can define a set of actions as a product type.

```scala
sealed trait MyAction extends Action
object MyAction:
case object A extends MyAction
case object B extends MyAction
case object C extends MyAction
def all: Seq[MyAction] = Seq(A, B, C)
```

The final refinements required are to choose the class of the Alchemist environment to instantiate, define the number of agents living in the environment, and determine the size of the buffer in which the memory will be stored. These refinements are expressed as follows:

```scala
val system = learningSystem {
	rewardFunction { new MyRewardFunction() }
	actions { MyAction.all}
	dataset { ReplayBuffer[State, Action](10000) }
	agents { 50 } // select the number of agent
	environment {
		// select a specific environment
		"it.unibo.scarlib.experiments.myEnvironment"
	}
}
```