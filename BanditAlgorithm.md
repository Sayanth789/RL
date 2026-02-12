# ε-Greedy Algorithm (k-Armed Bandit)

## Description

The ε-greedy algorithm balances **exploration** and **exploitation** in the k-armed bandit problem.

- With probability $\( 1 - \epsilon \)$, choose the action with the highest estimated value.
- With probability $\( \epsilon \)$, choose a random action.

---

## Algorithm

### Initialization

For $\( a = 1 \) to \( k \):

\[
Q(a) \leftarrow 0
\]

\[
N(a) \leftarrow 0
\]$

---

### Loop Forever

Select action \( A \):

\[
A =
\begin{cases}
\arg\max_a Q(a) & \text{with probability } 1 - \epsilon \\
\text{a random action} & \text{with probability } \epsilon
\end{cases}
\]

Receive reward:

\[
R \leftarrow \text{bandit}(A)
\]

Update action count:

\[
N(A) \leftarrow N(A) + 1
\]

Update action-value estimate:

\[
Q(A) \leftarrow Q(A) + \frac{1}{N(A)} \left[ R - Q(A) \right]
\]

---

## Explanation

- $\( Q(a) \) — Estimated value of action \( a \)$  
- $\( N(a) \) — Number of times action \( a \) was selected$  
- $\( R \) — Reward received after taking action \( A \)$
- $\( \epsilon \) — Exploration rate$  

The update rule incrementally computes the sample average reward for each action.
