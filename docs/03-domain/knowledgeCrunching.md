---
title: Knowledge Crunching
parent: Domain Knowledge
has_children: false
nav_order: 2
---

# Knowledge Crunching

## Interview

After analyzing the client's request and the making the impact map, we had an interview with one of the clients, it is reported below.

**Question 1**

<span style="color: #0077b6">**Analyst**</span>: 
    In the request you asked us to develop a tool for Cooperative Many Agent Reinforcement Learning, with the term "many" what order of magnitude do you mean ?

<span style="color: #79a355">**Domain expert**</span>: 
    I mean that the tool has to be able to handle from hundreds of agents to about one or two thousand.


**Question 2**

<span style="color: #0077b6">**Analyst**</span>: 
    In the description of the ad-hoc systems you are using you mentioned that you have used the tools Alchemist and Scafi, is the integration highly needed also in the new framework?

<span style="color: #79a355">**Domain expert**</span>:
    Yes, ideally we want a generic tool that can be integrated with other tools for simulation environment (e.g., Alchemist) and aggregate programming (e.g., Scafi). The default integration has to be with Alchemist and Scafi but since it is a generic tool we must be able to replace one (or all) of these two tools with another one (e.g., Alchemist with some other simulator).


**Question 3**

<span style="color: #0077b6">**Analyst**</span>: 
    Let's suppose that the tool is ready, how do you expect to be able to use it to define your experiments?

<span style="color: #79a355">**Domain expert**</span>:
    I expect that I have to implement/define the concepts related to the specific experiment, for example the action space, then start the training and monitor it.


**Question 4**

<span style="color: #0077b6">**Analyst**</span>:
    What do you mean with "monitor the training" ?

<span style="color: #79a355">**Domain expert**</span>:
    I mean that I would like to have both: 
        i) a live check of what the agents are learning and 
        ii) a posteriori evaluation of the learned policy.


**Question 5**

<span style="color: #0077b6">**Analyst**</span>: 
    What do you mean with "live check"?

<span style="color: #79a355">**Domain expert**</span>:
    I mean that I would like to see the agents act and, moreover, to have some charts that resume some specified metrics (e.g., the sum of the rewards over the time).


**Question 6**

<span style="color: #0077b6">**Analyst**</span>: 
    Are the graphs always the same or should they be customizable?

<span style="color: #79a355">**Domain expert**</span>:
    The charts must be customizable, in this way, depending on the specific experiment, the most relevant metrics can be plotted.


**Question 6**

<span style="color: #0077b6">**Analyst**</span>: 
    Talking about the "a posteriori evaluation", you said that you would like to check the learned policy, is that policy the last one of the training process or is there the need for a snapshot mechanism, for example at any given step ?

<span style="color: #79a355">**Domain expert**</span>:
    A snapshot mechanism is needed! Usually the learning process is very unpredictable and, for example, a policy learned at the episode 500 may be better than one learned at the episode 650. 


**Question 7**

<span style="color: #0077b6">**Analyst**</span>: 
    Regarding the specification of the experiments, in your opinion, what are the aspects that should be customizable in order to define a new task for the agents?

<span style="color: #79a355">**Domain expert**</span>:
    Surely: 
        i) the action space, 
        ii) the state, 
        iii) the reward function,
        iiii) and the environment in which the agents act.


**Question 8**

<span style="color: #0077b6">**Analyst**</span>: 
    Regarding the learning algorithm, is the implementation of the DQN algorithm enough? Is there a need to implement other algorithms?

<span style="color: #79a355">**Domain expert**</span>:
    DQN is a very generic learning algorithm and it performs well on a wide range of tasks, so it is optimal as a default algorithm for the framework. However, the framework should offer the possibility to add new algorithms in an agile way.


**Question 9**

<span style="color: #0077b6">**Analyst**</span>: 
    These algorithms make extensive use of neural networks, are the classical feed-forward neural networks sufficient or is there a need for more complex networks (e.g., Reccurent NN or Convolutional NN) ?

<span style="color: #79a355">**Domain expert**</span>:
    Feed-forward neural networks work well on a wide range of tasks, however, the framework should allow the user to define his own preferred neural network.
    I think that first the tool has to support feed-forward neural networks, then in the future, as soon as possible, there should also be the integration of more complex neural networks.

This is only one of the several interviews that we had with the clients, these interviews have been very important in being able to fully understand their needs.

## Activity diagram

Many activity diagrams were also developed during the various interviews. These diagrams gave the development team a better understanding of how the end user should interact with the framework. Below is an example of the activity diagram developed for the definition of a learning process.

<div align="center">
<img src="./imgs/activity-diagram.png" alt="Activity diagram for a learning process" width="100%">
</div>