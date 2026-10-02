# Sequential Decision-Making

Mathematical study notes on **Markov decision processes (MDPs)** and **dynamic programming**, adapted from Martin L. Puterman's *Markov Decision Processes: Discrete Stochastic Dynamic Programming*.

These 11 reports cover how to evaluate policies, find optimal decisions, and prove convergence, from finite-horizon models to discounted infinite-horizon MDPs.

## Finite-horizon MDPs: evaluation and backward induction

At time $`t`$, action $`A_t`$ in state $`S_t`$ produces reward $`R_{t+1}`$ and a transition to $`S_{t+1}`$. A policy specifies how actions are chosen.

For finite state and action sets, optimal values satisfy:

```math
\Large
\begin{aligned}
u_N^*(s) &= r_N(s), \\
u_t^*(s) &= \max_{a\in A_s}\left\{r_t(s,a)+\sum_{s'\in S}p_t(s'\mid s,a)\,u_{t+1}^*(s')\right\}.
\end{aligned}
```

Here, $`r_t(s,a)=\mathbb{E}[R_{t+1}\mid S_t=s,A_t=a]`$ is the expected immediate reward, $`p_t`$ gives next-state probabilities, and $`r_N`$ is the terminal payoff.

**Backward induction** solves the equation from $`N-1`$ back to $`1`$, choosing the action with the greatest immediate reward plus expected future value.

The reports establish the principle of optimality and show why deterministic Markov policies suffice, even when their actions depend on time.

## Discounted infinite-horizon MDPs: evaluation and convergence

When decisions continue indefinitely, a discount factor $`0\le\gamma\lt1`$ weights future rewards by $`1,\gamma,\gamma^2,\ldots`$. With bounded rewards, the expected discounted return is finite.

For stationary dynamics and a stationary Markov policy $`\pi`$, value equals expected immediate reward plus discounted continuation. In a finite state space:

```math
\Large
\begin{aligned}
v_\pi&=r_\pi+\gamma P_\pi v_\pi, \\
v_\pi&=(I-\gamma P_\pi)^{-1}r_\pi.
\end{aligned}
```

Here, $`r_\pi`$ and $`P_\pi`$ are the policy's reward vector and transition matrix. The **Bellman expectation operator** $`T_\pi v=r_\pi+\gamma P_\pi v`$ keeps the policy fixed. Evaluate the policy by solving the linear system above or by **iterative policy evaluation**, $`v^{(k+1)}=T_\pi v^{(k)}`$.

Convergence follows from the contraction bound:

```math
\Large
\|T_\pi v-T_\pi w\|_\infty\le\gamma\|v-w\|_\infty.
```

Each update shrinks the largest disagreement between estimates. **Banach's fixed-point theorem** guarantees a unique fixed point $`v_\pi=T_\pi v_\pi`$ and convergence to it from any initial estimate.

## Optimality, value iteration, and policy improvement

The **Bellman optimality operator** $`T`$ compares actions rather than following a fixed policy:

```math
\Large
\begin{aligned}
(Tv)(s)&=\max_{a\in A_s}\left\{r(s,a)+\gamma\sum_{s'\in S}p(s'\mid s,a)\,v(s')\right\}, \\
v_*&=Tv_*.
\end{aligned}
```

**Value iteration**, $`v^{(k+1)}=Tv^{(k)}`$, repeatedly applies this update. Since $`T`$ is also a contraction, Banach's theorem guarantees convergence to the unique optimal value $`v_*`$. Choosing maximizing actions at $`v_*`$ yields an optimal stationary deterministic policy in the finite discounted model.

**Policy improvement**:

```math
\Large
T_{\pi'}v_\pi\ge v_\pi
\quad\Longrightarrow\quad
v_{\pi'}\ge v_\pi.
```

If switching to $`\pi'`$ for one decision and then returning to $`\pi`$ performs at least as well in every state, using $`\pi'`$ throughout also does. The reports give both conditional-expectation and operator proofs.

Later reports connect action values and sampled backups to TD, SARSA, Monte Carlo methods, and Q-learning in Sutton & Barto's notation.

## Reports

Read in numerical order for the full development, or select a topic below.

**Finite horizon**

- [01 · Markov decision processes](01_Finite-Horizon-MDPs/01_Markov-Decision-Processes.pdf): Model formulation and policy classes
- [02 · Induced stochastic process](01_Finite-Horizon-MDPs/02_Induced-Stochastic-Process-and-Expectations.pdf): Trajectory probabilities and expectations
- [03 · Policy evaluation](01_Finite-Horizon-MDPs/03_Finite-Horizon-Policy-Evaluation.pdf): Conditional expectations and backward recursion
- [04 · Optimality equations](01_Finite-Horizon-MDPs/04_Optimality-Equations-and-Principle-of-Optimality.pdf): Characterization, verification, and the principle of optimality
- [05 · Matrix representation](01_Finite-Horizon-MDPs/05_Appendix-Matrix-Representation-of-Finite-Markov-Processes.pdf): Transition matrices as expectation operators

**Infinite horizon**

- [06 · Policy evaluation](02_Infinite-Horizon-MDPs/06_Infinite-Horizon-Policy-Evaluation.pdf): Discounted returns and the linear-system solution
- [07 · Banach fixed-point theorem](02_Infinite-Horizon-MDPs/07_Banach-Fixed-Point-and-Iterative-Policy-Evaluation.pdf): Norms, contraction, and iterative evaluation
- [08 · Optimality and value iteration](02_Infinite-Horizon-MDPs/08_Bellman-Optimality-Equations-and-Value-Iteration.pdf): Nonlinear Bellman backups and convergence
- [09 · Sutton notation](02_Infinite-Horizon-MDPs/09_Policy-Evaluation-in-Sutton-Notation.pdf): Random rewards, state values, and action values
- [10 · Bellman operators](02_Infinite-Horizon-MDPs/10_Bellman-Operators.pdf): State/action-value operators and sampled backups
- [11 · Policy improvement](02_Infinite-Horizon-MDPs/11_Policy-Improvement-Theorem.pdf): Two proofs and the greedy-policy corollary

## Related repositories

Companion work covers the mathematical background and the learning algorithms built on these ideas:

- **Mathematical foundations:** [Real Analysis](https://github.com/SaiSampathKedari/Real-Analysis) · [Probability and Distribution Theory](https://github.com/SaiSampathKedari/Probability-and-Distribution-Theory) · [Statistical Inference Theory](https://github.com/SaiSampathKedari/Statistical-Inference-Theory)
- **Algorithms and experiments:** [Reinforcement Learning](https://github.com/SaiSampathKedari/Reinforcement-Learning) · [Deep Reinforcement Learning](https://github.com/SaiSampathKedari/Deep-Reinforcement-Learning)

## Contact

- Email: [sampath@umich.edu](mailto:sampath@umich.edu)
- LinkedIn: [Sai Sampath Kedari](https://www.linkedin.com/in/sai-sampath-kedari/)
