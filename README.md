# Sequential Decision-Making — MDP and Dynamic Programming Theory

This repository contains my **mathematical foundations** for **Markov Decision Processes (MDPs)** and **Dynamic Programming**, synthesizing material from *Puterman: Markov Decision Processes*, *Bertsekas: Dynamic Programming and Optimal Control*, and *Sutton & Barto: Reinforcement Learning: An Introduction*. The focus is on **rigorous theory** — the probabilistic and operator-theoretic foundations underlying every reinforcement learning algorithm — independent of any specific implementation.

## Key Topics Covered

1. **Finite-Horizon MDPs**: Formal MDP definition, history-dependent vs Markovian policies, induced probability measure on trajectory space, finite-horizon policy evaluation by backward induction, complexity of history-dependent vs Markovian rules.
2. **Optimality Theory**: Optimality equations, principle of optimality, greedy policy construction (Theorem 4.3.2, 4.3.3).
3. **Infinite-Horizon MDPs**: Discounted, total, and average-reward criteria; Bellman consistency for stationary policies; Neumann-series solution; matrix representation of finite Markov chains.
4. **Operator-Theoretic Foundations**: Supremum norm on the value space, Banach Fixed-Point Theorem, the Bellman expectation and optimality operators on both V and Q, γ-contraction proofs, value iteration as fixed-point iteration.
5. **Policy Improvement**: Policy Improvement Theorem (both component-wise and operator-monotonicity proofs), greedy improvement, foundations of policy iteration.
## Repository Structure
- **`01_Finite-Horizon-MDPs/`** — Foundational definitions, induced stochastic process, backward induction, optimality equations, matrix representation appendix.
- **`02_Infinite-Horizon-MDPs/`** — Discounted policy evaluation, Banach fixed-point theory, value iteration, Bellman operators, Policy Improvement Theorem.

## Purpose

This repository is the **theoretical foundation** for my work in **Reinforcement Learning** and **Deep Reinforcement Learning**. It plays the same role for those topics that [`Probability-and-Distribution-Theory`](https://github.com/SaiSampathKedari/Probability-and-Distribution-Theory) and [`Statistical-Inference-Theory`](https://github.com/SaiSampathKedari/Statistical-Inference-Theory) play for [`MonteCarlo-Statistical-Methods`](https://github.com/SaiSampathKedari/MonteCarlo-Statistical-Methods) and [`Bayesian-Filtering-and-Smoothing`](https://github.com/SaiSampathKedari/Bayesian-Filtering-and-Smoothing): **pure theory upstream of any implementation**.

Algorithmic implementations of tabular RL, function approximation, and policy gradient methods will live in a separate **Reinforcement-Learning** repository; deep RL algorithms will live in **Deep-Reinforcement-Learning**. Both will reference this repository as a submodule for the underlying theory.

All reports are typeset in **LaTeX** for clarity.

## References
- M. L. Puterman, *Markov Decision Processes: Discrete Stochastic Dynamic Programming*
- D. P. Bertsekas, *Dynamic Programming and Optimal Control, Vol. I*
- R. S. Sutton and A. G. Barto, *Reinforcement Learning: An Introduction* (2nd ed.)
- S. Zhao, *Mathematical Foundations of Reinforcement Learning*

---

### **About Me**
I am focused on building strong **mathematical and statistical foundations** to support my work in **Robotics, AI, and State Estimation**.

---

### **Contact**
Feel free to connect with me:
- **Email**: sampath@umich.edu
- **LinkedIn**: www.linkedin.com/in/sai-sampath-kedari
