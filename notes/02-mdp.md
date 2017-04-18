# Chap 03: Finite Markov Decision Processes

Notations

- $S_t\in\mathcal{S}$: the environment state at step $t$, where $\mathcal{S}$ is the set of possible states
- $A_t\in\mathcal{A}(S_t)$: action given $S_t$, where $\mathcal{A}(S_t)$ is the set of actions available in state $S_t$
- $R_{t+1}\in\mathcal{R}\subset\mathbb{R}$: reward
- $\pi_t$: agent's policy, where $\pi_t(a|s)$ is the probability that $A_t=a$ if $S_t=s$

## Returns

Expected discounted return

$$G_t=\sum_{k=0}^{\infty}\gamma^{k}R_{t+k+1}$$
where $\gamma$ is a parameter, $0\leq \gamma\leq 1$, called the discount rate.

## MDP

A reinforcement learning task that statisfies the Markov property is called a **Markov Discision Process** (MDP).

A finite MDP is specified by its state and action sets ($\mathcal{S}$ and $\mathcal{A}$) and its one-step dynamics of the environment as:
$$p(s',r|s,a)=\text{Pr}(S_{t+1}=s',R_{t+1}=r|S_t=s,A_t=a)$$

All other things can be computed from this dynamics, including

- the expected rewards for state-action pairs $r(s,a)=\mathbb{E}(R_{t+1}|S_t=s,A_t=a)$
- the state transition prob $p(s'|s,a)=\text{Pr}(S_{t+1}=s'|S_t=s,A_t=a)$
- the expected rewards for state-action-next-state triples $r(s,a,s')=\mathbb{E}(R_{t+1}|S_t=s,A_t=a,S_{t+1}=s')$

**An alternative definition**[1] A MDP is defined by:

- a ste of states $\mathcal{S}$
- a start state or initial state $s_0\in\mathcal{S}$
- a set of actions $\mathcal{A}$
- a transition prob $P(S_{t+1} = s'|S_t = s,A_t = a)$
- a reward prob $P(R_{t+1}=r|S_t=s,A_t=a)$

## Value functions

For MDP, the **state-value function** for a policy $\pi$ is defined as
$$v_{\pi}(s)=\mathbb{E}_{\pi}(G_t|S_t=s)=\mathbb{E}_{\pi}(\sum_{k=0}^{\infty}\gamma^kR_{t+k+1})$$

Similar way can be used to define the **action-value function** for policy $\pi$, $q_{\pi}(s,a)$,
$$q_{\pi}(s,a)=\mathbb{E}_{\pi}(G_t|S_t=s,A_t=a)$$

- Q learning

### Bellman equation

The Bellman equation for $\pi$ is defined as following: for $s\in\mathcal{S}$,

$$v_{\pi}(s)=\sum_{a}\pi(a|s)\sum_{s',r}p(s',r|s,a)[r+\gamma v_{\pi}(s')]$$
which specifies the relation between $S_t$ and $S_{t+1}$ for a given $\pi$.

Reinforcement learning can solve Markov decision processes without explicit specification of the transition probabilities.

## Optimal Value Functions

In finite MDPs, value functions define a partial ordering over policies

- A policy $\pi$ is defined to be better than or equal to a policy $\pi'$ if its expected return is greater than or equal to that of $\pi'$ for all states.

Optimal state-value function, denoted $v_{\ast}$, $\forall s\in\mathcal{S}$
$$v_{\ast}(s)=\max_{\pi}v_{\pi}(s)$$

For MDP
$$v_{\ast}(s)=\max_{a\in\mathcal{A}(s)}\sum_{s',r}p(s',r|s,a)[r+\gamma v_{\ast}(s')]$$

This equation means that any policy that is greedy with respect to the optimal evaluation function $v_{\ast}$ is an optimal policy. Optimal policies also share the same *optimal action-value function*, denoted $q_{\ast}$, 
$$q_{\ast}(s,a) = \sum_{s',r}p(s',r|s,a)[r+\gamma\max_{a'}q_{\ast}(s',a')]$$


- This equation is also a special formulation that dynamic programming could find the optimal solution [2].
- Q learning

An [example](https://aclweb.org/anthology/D/D16/D16-1261.pdf) of using MDP for information extraction.

## Reference

1. Mohri, Rostmizadeh, Talwalkar. Foundations of Machine Learning. 2012
2. Kleinberg and Tardos. Algorithm Design. 2005
