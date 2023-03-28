---
title: Ubiquitous Language
parent: Domain Knowledge
has_children: false
nav_order: 2
---

# Ubiquitous Language

This subsection provides a description of the Ubiquitous Language extracted from the knowledge crunching sessions conducted with domain experts.

## Environment
A representation of the task or problem that an agent is trying to learn. It includes the set of possible [State](#state)s the [Agent](#agent) can be in, the [Action](#action)s it can take, the rules that govern how the environment changes in response to those actions, and the [Reward](#reward) signal that the [Agent](#agent) receives as feedback for its [Action](#action)s.

## Agent
An entity that interacts with an [Environment](#environment) in order to learn the optimal [Action](#action)s sequence to maximize a [Reward](#reward).

## State
A representation of the current situation or condition of the [Environment](#environment), including any relevant information that the [Agent](#agent) can perceive or use to make decisions about its [Action](#action)s.

### Initial State
The starting point of an [Agent](#agent)-[Environment](#environment) interaction, where the [Agent](#agent) is initialized in a particular [State](#state) of the [Environment](#environment).

## State Space
The set of all possible [State](#state)s in which an [Agent](#agent) can be while interacting with the [Environment](#environment). 

## Reward 
A scalar value that represents the feedback signal provided to an [Agent](#agent) by the [Environment](#environment) in response to the agent's [Action](#action)s. The reward signal is used by the [Agent](#agent) to learn which [Action](#action)s are beneficial and which are detrimental in achieving a particular goal. The goal of the [Agent](#agent) is typically to maximize the cumulative reward received over time. The reward can be positive, negative, or neutral.

## Action
A decision or choice made by an [Agent](#agent) in response to the current state of the [Environment](#environment).

## Action Space
The set of all possible [Action](#action)s that an [Agent](#agent) can take in response to the current state of the [Environment](#environment). It may be either [Discrete](#discrete-action-space) or [Continuous](#continuos-action-space).

### Discrete Action Space
An action space in which an [Agent](#agent) can choose from a finite set of [Action](#action)s.

### Continuos Action Space
An action space in which an [Agent](#agent) can choose from a continuous range of values.

## Experience
A set consisting of the current [State](#state) of the [Environment](#environment), the [Action](#action) taken by the agent in response to that [State](#state), the resulting [Reward](#reward) received by the agent, and the next [State](#State) of the [Environment](#environment) that the [Agent](#agent) transitions into as a result of its action.

## Policy
A function that maps the current [State](#state) of the [Environment](#environment) to a probability distribution over the set of possible [Action](#action)s that the [Agent](#agent) can take in that [State](#state). The policy specifies the [Agent](#agent)'s behavior or strategy in response to different [State](#state)s of the [Environment](#environment), and it is learned through a process of trial and error using the [Reward](#reward) signal as feedback.

## Step
A single interaction between the [Agent](#agent) and the [Environment](#environment), where the [Agent](#agent) observes the current [State](#state) of the [Environment](#environment), selects an [Action](#action) based on its current [Policy](#policy), receives a [Reward](#reward) from the [Environment](#environment), and transitions to a new [State](#state). Each step represents a discrete unit of time in the process. Steps need not to be fixed-length, just successive stages.

## Episode
A sequence of [Experience](#experience)s that an [Agent](#agent) goes through from an [Initial State](#initial-state), while interacting with the [Environment](#environment). Each episode has a fixed-length that is a hyper-parameter of the learning process.

## System
A collection of [Agent](#agent)s that interact within a shared [Environment](#environment). It defines the execution flow of the [Agent](#agent)s.

### CTDE System
A [System](#system) in which there is only one, centralized, [Learner](#learner) and only one [Replay Buffer](#replay-buffer). The [Policy](#policy) is 
improved by the centralized learner and then notified to each [Agent](#agent).

### DTDE System
A [System](#system) in which each [Agent](#agent) has its own [Learner](#learner) and [Replay Buffer](#replay-buffer). Each [Agent](#agent) is responsible
for updating its own [Policy](#policy).

## Learner
An abstraction over the learning algorithm, it knows how to improve the policy given the accumulated [Experience](#experience).

## Exploration Rate
The probability or frequency with which an [Agent](#agent) selects a random [Action](#action) rather than the optimal one according to its current [Policy](#policy). The exploration rate is used to balance the trade-off between exploration and exploitation, as it determines the degree to which the [Agent](#agent) explores the [Environment](#environment) to discover new and potentially better [Action](#action)s versus exploiting its current knowledge to maximize [Reward](#reward).

## Decay
A process in which a parameter or value is gradually reduced over time, usually at a fixed rate or according to a predefined function. Decay is commonly used to decrease the [Exploration Rate](#exploration-rate) over time. 

## Q-Learning
A Reinforement Learning algorithm that aims to learn the optimal [Q-value](#q-value) function for a given [Environment](#environment) and task.

## Q-Value
The expected cumulative [Reward](#reward) that the [Agent](#agent) will receive if it takes a particular [Action](#action) in a particular [State](#state), and then follows an optimal [Policy](#policy) thereafter.

## DQN
A type of Reinforcement Learning algorithm that combines the [Q-learning](#q-learning) algorithm with deep neural networks to handle high-dimensional [State Spaces](#state-space). In DQN, the [Q-Value](#q-value) function is approximated by a deep neural network, which takes the [State](#state) as input and outputs the [Q-value](#q-value) for each possible [Action](#action).

## Replay Buffer
A data structure that stores a history of the [Agent](#agent)'s [Experience](#experience)s. 

## Encoding
A representation of a specific [State](#state) used as input for the neural network that approximates the [Q-Value](#q-value) function.
 
