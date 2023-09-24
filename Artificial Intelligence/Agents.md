### Agents in AI

Agents perceive the state of the world through sensors and perform actions on it through actuators. The primary types of agents are:

### Reflex Agents:

Reflex agents make decisions based on specific conditions in their environment, without considering the future consequences. They are designed to respond immediately to stimuli.

**Example**: A vacuum-cleaning robot that detects dirt on the floor and immediately starts cleaning is a reflex agent. The agent's action (start cleaning) is directly triggered by the perception (dirt on the floor).

### Goal-Based Agents:

Goal-based agents aim to achieve a predefined goal. They not only consider the current state but also simulate future actions to decide the best path to reach their goal.

**Example**: A chess-playing agent considers its goal to checkmate the opponent. It predicts the outcomes of various possible moves to choose the one that maximizes its chances of achieving this goal.

### Utility-Based Agents:

Utility-based agents use a utility function to evaluate the desirability of different states. The agent aims to maximize its utility, choosing actions that it believes will lead to the highest utility state.

**Example**: A stock-trading agent uses a utility function that takes into account not just profit but also risk factors. It aims to maximize this utility function by buying and selling stocks.

### Learning Agents:

Learning agents improve their performance based on experience. They consist of a learning element that updates the agent's knowledge and a performance element that makes decisions based on this knowledge. Feedback from the environment, often via a critic, helps the agent learn.

**Example**: A recommendation system that learns from user behavior. Initially, the system might not make very accurate recommendations, but over time it learns from the feedback (e.g., clicks, likes, or skips) to improve its future recommendations.