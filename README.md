# Reinforcement Learning for Blackjack Strategy

### Overview

This repository contains an exploration of reinforcement learning (RL) techniques applied to discovering an optimal strategy for the card game Blackjack. The project implements and evaluates two primary RL methods: a tabular Q-learning approach and a Deep Q-Network (DQN). The performance of these models is benchmarked against a random agent and a known optimal strategy.

The core of this work lies in the comparison of these different agents, focusing on their computational efficiency, the quality of the learned policies, and their overall win rates. This README provides a high-level summary of the project, the methodologies used, and the key findings.

### Table of Contents

1.  **Introduction to Blackjack and the Environment**
    *   [Blackjack Rules](#blackjack-rules)
    *   [Gymnasium Environment](#gymnasium-environment)
2.  **Implemented Solutions**
    *   [Random Agent](#random-agent)
    *   [Optimal Agent](#optimal-agent)
    *   [Tabular Q-learning](#tabular-q-learning)
    *   [Deep Q-Network (DQN)](#deep-q-network-dqn)
3.  **Key Findings and Results**
    *   [Policy Comparison](#policy-comparison)
    *   [Win Rate Estimation](#win-rate-estimation)
4.  **How to Use This Repository**
5.  **Conclusion**

### Introduction to Blackjack and the Environment

#### Blackjack Rules

The objective in Blackjack is to achieve a hand value closer to 21 than the dealer, without exceeding it. This project utilizes a simplified version where the player can only "hit" (take another card) or "stand" (keep their current hand).

#### Gymnasium Environment

The experiments are conducted using the "Blackjack-v1" environment from the Gymnasium library. This standardized environment provides the necessary components for training RL agents, including:

*   **Observation Space**: A tuple representing the player's current hand sum, the dealer's visible card, and whether the player holds a usable Ace.
*   **Action Space**: Discrete actions of hitting or standing.
*   **Reward Structure**: A simple reward system of +1 for a win, -1 for a loss, and 0 for a draw.

### Implemented Solutions

This project develops and analyzes four distinct agents to tackle the Blackjack environment.

#### Random Agent

A baseline agent that selects actions randomly. This agent serves as a lower-bound for performance, demonstrating the effectiveness of learned policies.

#### Optimal Agent

An agent that follows a predefined, mathematically derived optimal strategy for when to hit or stand. This agent acts as an upper-bound benchmark for the performance of the learning agents.

#### Tabular Q-learning

A classic reinforcement learning approach that uses a Q-table to learn the expected rewards for taking a certain action in a given state. This method is well-suited for environments with discrete state and action spaces. The agent was trained for 10 million episodes, with its convergence and reward evolution tracked to assess its learning progress.

#### Deep Q-Network (DQN)

A more advanced approach that employs a neural network to approximate the Q-value function, making it suitable for more complex, high-dimensional state spaces. The DQN agent's architecture consists of a fully connected neural network and utilizes an experience replay mechanism to stabilize training.

### Key Findings and Results

#### Policy Comparison

The policies learned by the Q-learning and DQN agents were compared against the optimal strategy.

*   The **Tabular Q-learning** agent learned a policy that very closely mimics the optimal strategy, with only minor deviations in specific scenarios.
*   The **DQN** agent, due to the nature of function approximation, developed a more rigid set of rules that, while effective, did not match the optimal policy as closely as the tabular method.

#### Win Rate Estimation

To provide a robust comparison, the win rates of all four agents were estimated over a large number of episodes (960,400) to ensure statistical significance.

| Agent | Win Rate (%) |
| :--- | :--- |
| Optimal | 43.29 |
| Tabular Q-Learning | 43.20 |
| DQN | 42.79 |
| Random | 28.23 |

### Conclusion

The results demonstrate that reinforcement learning can successfully be applied to learn effective strategies for Blackjack. The Tabular Q-learning approach proved to be particularly well-suited for this discrete environment, achieving a win rate nearly identical to the optimal policy with high computational efficiency. While the DQN was also able to learn a strong policy, its training was significantly more time-consuming. This project highlights the strengths and weaknesses of different RL approaches in a classic game environment.