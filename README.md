# Sequential Decision-Making

Mathematical study notes on **Markov decision processes (MDPs)** and **dynamic programming**, adapted from Martin L. Puterman's *Markov Decision Processes: Discrete Stochastic Dynamic Programming*. Later reports connect these foundations to Sutton & Barto's reinforcement learning notation.

Decisions have both immediate and long-term consequences. What we choose today affects the choices we face tomorrow. These 11 reports develop the mathematics of this connection under uncertainty, showing how policies generate stochastic processes, how their expected returns are evaluated, and how optimal decisions are characterized and computed.

## Finite-horizon MDPs: evaluation and backward induction

At time $t$, action $A_t$ in state $S_t$ produces reward $R_{t+1}$ and a transition to $S_{t+1}$. A policy specifies how actions are chosen. The reports construct the resulting trajectory probabilities and derive expected returns from conditional expectations.

For finite state and action sets, optimal values satisfy:

$$
\begin{aligned}
u_N^*(s) &= r_N(s), \\
u_t^*(s) &= \max_{a\in A_s}\left\{r_t(s,a)+\sum_{s'\in S}p_t(s'\mid s,a)\,u_{t+1}^*(s')\right\}.
\end{aligned}
$$

Here, $r_t(s,a)=\mathbb{E}[R_{t+1}\mid S_t=s,A_t=a]$ is the expected immediate reward, $p_t$ describes next-state probabilities, and $r_N$ is the terminal payoff. For each feasible action $a\in A_s$, compare immediate reward plus expected future value. **Backward induction** starts at $N$ and solves these comparisons at $t=N-1,\ldots,1$.

The notes establish the principle of optimality and show why deterministic Markov policies suffice. Their actions may still depend on how much time remains.

## Discounted infinite-horizon MDPs: evaluation and convergence

When decisions continue indefinitely, a discount factor $0\le\gamma<1$ weights future rewards by $1,\gamma,\gamma^2,\ldots$. With bounded rewards, the expected discounted return is finite.

For stationary dynamics and a stationary Markov policy $\pi$, the value $v_\pi$ equals **one expected reward plus the discounted value of continuing**. In a finite state space, this gives a linear system and its exact solution:

$$
\begin{aligned}
v_\pi&=r_\pi+\gamma P_\pi v_\pi, \\
v_\pi&=(I-\gamma P_\pi)^{-1}r_\pi.
\end{aligned}
$$

The reward vector $r_\pi$ and transition matrix $P_\pi$ average over the policy's action choices. The **Bellman expectation operator** $T_\pi v=r_\pi+\gamma P_\pi v$ updates a value estimate while keeping the policy fixed. To evaluate that policy, we can solve $(I-\gamma P_\pi)v_\pi=r_\pi$ directly, or apply **iterative policy evaluation**, $v^{(k+1)}=T_\pi v^{(k)}$.

These repeated updates converge because:

$$
\|T_\pi v-T_\pi w\|_\infty\le\gamma\|v-w\|_\infty.
$$

Each update shrinks the largest disagreement between two estimates. **Banach's fixed-point theorem** guarantees a unique solution $v_\pi=T_\pi v_\pi$, where the update leaves the value unchanged. It also guarantees convergence to this solution from any initial estimate.

## Optimality, value iteration, and policy improvement

Evaluation follows a given policy. Optimization compares feasible actions and chooses the largest sum of immediate reward and future value, while still averaging over uncertain next states:

$$
\begin{aligned}
(Tv)(s)&=\max_{a\in A_s}\left\{r(s,a)+\gamma\sum_{s'\in S}p(s'\mid s,a)\,v(s')\right\}, \\
v_*&=Tv_*.
\end{aligned}
$$

The **Bellman optimality operator** $T$ includes a maximization in each update. Its fixed-point equation is solved using **value iteration**, $v^{(k+1)}=Tv^{(k)}$. This operator is also a contraction, so Banach's theorem guarantees convergence to the unique optimal value $v_*$. Choosing maximizing actions at $v_*$ yields an optimal stationary deterministic policy in the finite discounted model.

Policy improvement connects evaluation to better decisions:

$$
T_{\pi'}v_\pi\ge v_\pi
\quad\Longrightarrow\quad
v_{\pi'}\ge v_\pi.
$$

If using $\pi'$ for one decision and then returning to $\pi$ performs at least as well as $\pi$ in every state, using $\pi'$ throughout also does. The reports prove this through both conditional expectations and Bellman operators.

The later notes extend this view to action values and sampled backups, connecting the theory to TD, SARSA, Monte Carlo methods, and Q-learning.

## Reports

Read in numerical order for the full development, or select a topic below. All reports are PDFs typeset in LaTeX.

| Finite horizon | Focus |
| :--- | :--- |
| [01 · Markov decision processes](01_Finite-Horizon-MDPs/01_Markov-Decision-Processes.pdf) | Model formulation and policy classes |
| [02 · Induced stochastic process](01_Finite-Horizon-MDPs/02_Induced-Stochastic-Process-and-Expectations.pdf) | Trajectory probabilities and expectations |
| [03 · Policy evaluation](01_Finite-Horizon-MDPs/03_Finite-Horizon-Policy-Evaluation.pdf) | Conditional expectations and backward recursion |
| [04 · Optimality equations](01_Finite-Horizon-MDPs/04_Optimality-Equations-and-Principle-of-Optimality.pdf) | Characterization, verification, and the principle of optimality |
| [05 · Matrix representation](01_Finite-Horizon-MDPs/05_Appendix-Matrix-Representation-of-Finite-Markov-Processes.pdf) | Transition matrices as expectation operators |

| Infinite horizon | Focus |
| :--- | :--- |
| [06 · Policy evaluation](02_Infinite-Horizon-MDPs/06_Infinite-Horizon-Policy-Evaluation.pdf) | Discounted returns and the linear-system solution |
| [07 · Banach fixed-point theorem](02_Infinite-Horizon-MDPs/07_Banach-Fixed-Point-and-Iterative-Policy-Evaluation.pdf) | Norms, contraction, and iterative evaluation |
| [08 · Optimality and value iteration](02_Infinite-Horizon-MDPs/08_Bellman-Optimality-Equations-and-Value-Iteration.pdf) | Nonlinear Bellman backups and convergence |
| [09 · Sutton notation](02_Infinite-Horizon-MDPs/09_Policy-Evaluation-in-Sutton-Notation.pdf) | Random rewards, state values, and action values |
| [10 · Bellman operators](02_Infinite-Horizon-MDPs/10_Bellman-Operators.pdf) | State/action-value operators and sampled backups |
| [11 · Policy improvement](02_Infinite-Horizon-MDPs/11_Policy-Improvement-Theorem.pdf) | Two proofs and the greedy-policy corollary |

## Related repositories

Companion work covers the mathematical background and the learning algorithms built on these ideas:

- **Mathematical foundations:** [Real Analysis](https://github.com/SaiSampathKedari/Real-Analysis) · [Probability and Distribution Theory](https://github.com/SaiSampathKedari/Probability-and-Distribution-Theory) · [Statistical Inference Theory](https://github.com/SaiSampathKedari/Statistical-Inference-Theory)
- **Algorithms and experiments:** [Reinforcement Learning](https://github.com/SaiSampathKedari/Reinforcement-Learning) · [Deep Reinforcement Learning](https://github.com/SaiSampathKedari/Deep-Reinforcement-Learning)

## Contact

- Email: [sampath@umich.edu](mailto:sampath@umich.edu)
- LinkedIn: [Sai Sampath Kedari](https://www.linkedin.com/in/sai-sampath-kedari/)
