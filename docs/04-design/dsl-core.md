---
title: scarlib-core
parent: Design
has_children: false
nav_order: 2
---

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