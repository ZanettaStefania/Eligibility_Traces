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
![Version 1](https://github.com/user-attachments/assets/16ac2443-378a-41f8-b475-3d2886071a4b)
2. **Version 2**: Added intermediate rewards (+2) on specific states, which disappear once collected.
![Version 2](https://github.com/user-attachments/assets/f4b46603-8399-47de-9933-47b4e8346d6c)
3. **Version 3**: Introduced new final states with negative rewards, representing ghosts (non-moving).
![Version 3](https://github.com/user-attachments/assets/6d5344f2-3ac3-4477-99f4-5ab48d8f11e0)
4. **Version 4**: Randomized state positions and rewards, with a fixed final positive reward and agent starting position.
![Version 4](https://github.com/user-attachments/assets/6427055f-6433-4bda-8034-8acf0dedd03a)


### Results:

For each game version and *λ* value, the following results were shown:
- Average reward over 100 episodes
- Average TD error over 100 episodes
- Final policy
- Heatmap of eligibility traces


![AMLheatmap](https://github.com/user-attachments/assets/b7860355-18f8-4b08-b0d2-2007b19d31f4)

The notebook presents the results of the experiments, comparing average rewards, TD errors, and the number of steps taken for each algorithm with different *λ* values.

---

## Final Comment

Generally, we can say that the **Q-Learning** method converges faster than the **SARSA** method. This is more evident when using higher *λ* values, as **Q-Learning** tends to converge faster with larger *λ* values.

However, the same cannot be said about the **TD error**. From the plot, we can observe that **Q-Learning** exhibits more spikes and isn't as stable as **SARSA**. This is due to the fact that **Q-Learning** is an off-policy method and does not need to follow the optimal policy learned, leading to instability in the TD error.

From the **heatmap plots**, we can see that the eligibility trace becomes longer as *λ* increases, showing a greater influence of past states or actions on the current value updates.

Finally, from the **table of results**, we can clearly see that **Q-Learning** outperforms **SARSA** overall, with higher rewards, fewer steps, and lower TD error. Although **SARSA** sometimes achieves better results with *λ=0*, **Q-Learning** tends to yield slightly better performance most of the time.
![AMLTable](https://github.com/user-attachments/assets/2ea345aa-1dee-405f-a4f5-3ad464163eac)

