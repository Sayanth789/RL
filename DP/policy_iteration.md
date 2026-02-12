## Policy Iteration (using Iterative Policy Evaluation) for estimating $\pi \approx \pi_*$

---

### 1. Initialization

Initialize:

- $V(s)\in\mathbb{R}$ arbitrarily  
- $\pi(s)$ arbitrarily  

for all $s\in S$.

---

### 2. Policy Evaluation

Loop:

$$
\Delta\leftarrow 0
$$

For each $s\in S$:

$$
v\leftarrow V(s)
$$

$$
V(s)\leftarrow
\sum_{s',r}p(s',r\mid s,\pi(s))
\left[r+\gamma V(s')\right]
$$

$$
\Delta\leftarrow \max(\Delta,|v-V(s)|)
$$

Repeat until:

$$
\Delta<\theta
$$

where $\theta>0$ is a small positive number determining the accuracy of estimation.

---

### 3. Policy Improvement

$$
\text{policy-stable}\leftarrow\text{true}
$$

For each $s\in S$:

$$
\text{old-action}\leftarrow \pi(s)
$$

$$
\pi(s)\leftarrow
\arg\max_a
\sum_{s',r}p(s',r\mid s,a)
\left[r+\gamma V(s')\right]
$$

If $\text{old-action}\neq\pi(s)$:

$$
\text{policy-stable}\leftarrow\text{false}
$$

If policy-stable, then stop and return:

- $V\approx v_*$
- $\pi\approx\pi_*$

Else go to Step 2.
