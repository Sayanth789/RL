## Value Iteration

### Algorithm Parameter

A small threshold $\theta>0$ determining the accuracy of estimation.

---

### Initialization

Initialize $V(s)$ arbitrarily for all $s\in S^+$,  
except that:

$$
V(\text{terminal})=0
$$

---

### Algorithm

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
\max_a
\sum_{s',r}p(s',r\mid s,a)
\left[r+\gamma V(s')\right]
$$

$$
\Delta\leftarrow \max(\Delta,|v-V(s)|)
$$

Repeat until:

$$
\Delta<\theta
$$

---

### Output

A deterministic policy $\pi\approx\pi_*$ such that

$$
\pi(s)=
\arg\max_a
\sum_{s',r}p(s',r\mid s,a)
\left[r+\gamma V(s')\right]
$$
