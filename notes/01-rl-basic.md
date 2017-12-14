# Chap 01: The Reinforcement Learning (RL) Problem

## Introduction 

- Three characteristics of the RL problems
	- being closed-loop in an essential way
	- not having direct instructions as to what actions to take
	- where the consequences of actions, including reward signals, play out over extended time periods
- The difference between RL and supervised learning
- The difference between RL and unsupervised learning
	- RL: maximize rewards
	- Unsupervised learning: find hidden structures of data
- The special challenge of RL: the tradeoff between **exploration** and **exploitation**. An agent is supposed to both
	- exploit what it already knows in order to obtain reward
	- explore in order to make better action selections in the future

## Elements of RL

- A policy
	- define the learning agent's way of behaving at a given time
	- the **core** of an agent in the sense that it alone is sufficient to determine behavior
- A reward signal
	- define the goal in an RL problem by determining what are the good and bad events for the agent
	- the agent's sole objective is to maximize the **total** reward it receives over the long run
	- the process that generates the reward signal must be unalterable by the agent
- A value function
	- specify what is good in the long run
	- the *value* of a state is the total amount of reward an agent can **expect** to accumulate over the future, starting from that state
	- a value of the prediction of rewards in a long run given the current state
- A model of the environmnet (optional)

## Tic-Tac-Toe

- The difference between evolutionary methods and the methods of learning value functions
	- learning a value function takes advantage of information available during the course of play
