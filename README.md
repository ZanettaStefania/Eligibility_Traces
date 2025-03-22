# Eligibility Traces

---

## Overview

This project explores the concept of **Eligibility Traces** in Reinforcement Learning (RL), with a focus on **TD(λ)**, and how it connects with **SARSA(λ)** and **Q-Learning(λ)**. 

### Concepts to Explain

#### 1. **Monte Carlo and Temporal Difference (TD)**:
- **Monte Carlo (MC)**: MC methods are based on waiting for the end of an episode to update the value function. They are only applicable to episodic (terminating) environments.
- **Temporal Difference (TD)**: TD methods update the value function after each step, based on estimates of the next state’s value. TD can handle continuing (non-terminating) environments, like stock trading.
  
MC provides unbiased estimates of value functions, but with higher variance. TD, in contrast, is biased but has lower variance due to continuous updates.

#### 2. **N-Step Methods**:
N-step methods extend TD learning by considering multiple future time steps before updating. The parameter *N* controls the trade-off between bias and variance. Both Monte Carlo and TD can be seen as special cases of N-step, with Monte Carlo being *N = ∞* and TD being *N = 1*.

#### 3. **Eligibility Traces**:
Eligibility traces, denoted by *λ*, are a technique used to track the influence of past state-action pairs on the current value estimates. They serve as a memory mechanism, allowing agents to assign credit to states or actions based on their previous visits.

#### 4. **TD(λ)**:
TD(λ) extends basic TD methods by combining eligibility traces to credit rewards to past states or actions. The parameter *λ* controls how much influence past states or actions have on the current value updates, from *λ=0* (immediate reward) to *λ=1* (full sequence of future rewards).

---

## Notebook

The Python notebook demonstrates the differences between SARSA(λ) and Q-Learning(λ) with various values of *λ*. The experiments were conducted using a simplified version of PacMan, where four different versions of the game were implemented to illustrate the impact of different *λ* values.

### Game Versions:

1. **Version 1**: Simple environment with a single final state that gives a positive reward.
2. **Version 2**: Added intermediate rewards (+2) on specific states, which disappear once collected.
3. **Version 3**: Introduced new final states with negative rewards, representing ghosts (non-moving).
4. **Version 4**: Randomized state positions and rewards, with a fixed final positive reward and agent starting position.

### Results:

For each game version and *λ* value, the following results were shown:
- Average reward over 100 episodes
- Average TD error over 100 episodes
- Final policy
- Heatmap of eligibility traces

The notebook presents the results of the experiments, comparing average rewards, TD errors, and the number of steps taken for each algorithm with different *λ* values.

---

## Final Comment

Generally, we can say that the **Q-Learning** method converges faster than the **SARSA** method. This is more evident when using higher *λ* values, as **Q-Learning** tends to converge faster with larger *λ* values.

However, the same cannot be said about the **TD error**. From the plot, we can observe that **Q-Learning** exhibits more spikes and isn't as stable as **SARSA**. This is due to the fact that **Q-Learning** is an off-policy method and does not need to follow the optimal policy learned, leading to instability in the TD error.

From the **heatmap plots**, we can see that the eligibility trace becomes longer as *λ* increases, showing a greater influence of past states or actions on the current value updates.

Finally, from the **table of results**, we can clearly see that **Q-Learning** outperforms **SARSA** overall, with higher rewards, fewer steps, and lower TD error. Although **SARSA** sometimes achieves better results with *λ=0*, **Q-Learning** tends to yield slightly better performance most of the time.

---

## Acknowledgments

- **SARSA(λ)**: Algorithm for on-policy reinforcement learning with eligibility traces.
- **Q-Learning(λ)**: Off-policy reinforcement learning algorithm with eligibility traces.
- **PacMan**: Simplified environment used to illustrate RL algorithms.


