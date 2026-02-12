# Iterative Policy Evaluation

## Input
- A policy $ \pi $ to be evaluated.

## Algorithm Parameter
- A small threshold $ \theta > 0 $ determining the accuracy of estimation.

---

## Initialization

Initialize $ V(s) $ arbitrarily for all $ s \in S^{+} $,  
except that:

$$
V(\text{terminal}) = 0
$$

---

## Algorithm

Loop:

$$
\Delta \leftarrow 0
$$

For each state $ s \in S $:

$$
v \leftarrow V(s)
$$

$$
V(s) \leftarrow 
\sum_{a} \pi(a \mid s)
\sum_{s', r} p(s', r \mid s, a)
\left[ r + \gamma V(s') \right]
$$

$$
\Delta \leftarrow \max(\Delta, | v - V(s) |)
$$

Repeat until:

$$
\Delta < \theta
$$

---

## Description

- $ V(s) $ — State-value function  
- $ \pi(a \mid s) $ — Policy probability of taking action $ a $ in state $ s $  
- $ p(s', r \mid s, a) $ — Transition probability  
- $ \gamma $ — Discount factor  
- $ \theta $ — Convergence threshold  
- $ \Delta $ — Maximum change in value during an iteration  

This algorithm evaluates a given policy by iteratively updating the value function until convergence.
