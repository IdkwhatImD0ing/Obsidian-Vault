## Utilities
 - Function that take in an outcome and return a number that describes the performance in that outcome
 - Where do utilities come from?
 - In a game, may be simple (+1/-1)
 - Utilities summarize the agent’s goals
 - Theorem: any “rational” preferences can be summarized as a utility function

## Rational Preferences

A > B = A is preferred over B
A >=  = A is not preferred over B
A~B = In difference between A and B
\[p, A; (1-p), B] = Lottery

![[Pasted image 20230318212608.png]]

This passage presents the famous Allais Paradox, proposed by Maurice Allais in 1953. The paradox demonstrates that people's choices can sometimes violate the axioms of rationality, particularly the Independence of Irrelevant Alternatives (IIA) axiom.

The example presents two sets of choices, each with two lotteries:

First set of choices:

 - A: 80% chance of winning $4,000 and 20% chance of winning $0.
 - B: 100% chance of winning $3,000 and 0% chance of winning $0.

Second set of choices:

 - C: 20% chance of winning $4,000 and 80% chance of winning $0.
 - D: 25% chance of winning $3,000 and 75% chance of winning $0.

Empirical evidence shows that most people prefer lottery B over A and lottery C over D. This preference pattern appears to violate the IIA axiom.

The passage then demonstrates this violation using utility (U) functions. Assume U($0) = 0. If most people prefer B over A, it implies that U($3,000) > 0.8 * U($4,000). Similarly, if most people prefer C over D, it implies that 0.2 * U($4,000) > 0.25 * U($3,000). Multiplying both sides of the latter inequality by 4 results in 0.8 * U($4,000) > U($3,000), which contradicts the preference of B over A.

**The Allais Paradox highlights that people's preferences sometimes do not conform to the axioms of rationality. It has implications for decision theory and economics, as it challenges the assumptions of rational behavior in these fields.**


## MDPs
 - Markov Decision Processes
 - Common formulation for problems with uncertainty
 - MDPs are a family of non-deterministic search problems
 - An MDP is defined by:
	 - A set of states s ∈ S
	 - A set of actions a ∈ A
	 - A transition function T(s,a,s’)
	 - Prob that a from s leads to s’
		 - i.e., P(s’ | s,a)
	 - Also called the model
	 - A reward function R(s, a, s’)
	 - Sometimes just R(s) or R(s’)
	 - A start state (or distribution)
	 - Maybe a terminal state
 - MDP Solution is a policy rather than a model
   
Imagine you're playing a video game where you control a character that can move around, perform actions, and collect rewards. In this game, you're trying to make the best decisions to earn the most points. MDPs are a way to model this kind of situation.

An MDP consists of the following elements:

 - States (s ∈ S): These are like different places or situations in the game where your character can be. For example, different rooms or levels.

 - Actions (a ∈ A): These are the moves or things your character can do in the game, like jumping, running, or shooting.

 - Transition function (T(s, a, s')): This tells you the probability that doing an action (a) in a state (s) will lead you to a new state (s'). It's like a rulebook that explains how the game world changes based on your actions. The transition function is sometimes called the "model."

 - Reward function (R(s, a, s')): This tells you how many points or rewards you get for performing an action (a) in a state (s) and reaching a new state (s'). Sometimes, the reward function might depend only on the current state (s) or the next state (s').

 - Start state: This is the initial situation or place in the game where your character begins.

 - Terminal state (optional): This is a special state that, once reached, ends the game or level.

The goal of an MDP is to find the best strategy or sequence of actions that will earn the most rewards (points) in the game. You'll want to consider not only the immediate rewards but also the potential future rewards as you progress through the game.

In summary, Markov Decision Processes are a way to model decision-making situations, like playing a video game, where you have to choose the best actions to maximize your rewards. They involve states, actions, transition functions, reward functions, and start (and possibly terminal) states to describe the problem and help you find the best strategy.


### Bellman Equations
![[Pasted image 20230213180052.png]]

### Value Iteration
 - Idea:
	 - Start with V0 (s) = 0, which we know is right (why?)
	 - Given Vi, calculate the values for all states for depth i+1:
	 - ![[Pasted image 20230213180149.png]]
	 - Throw out old Vi values
	 - This is called a value update or Bellman update
	 - Repeat until convergence
 - Theorem: will converge to unique optimal values
	 - Basic idea: approximations get refined towards optimal values
	 - Policy may converge long before values do

### Explanation:

Value Iteration is an algorithm used to solve Markov Decision Processes (MDPs) by iteratively updating the estimated values of each state. The goal is to find an optimal policy that maximizes the expected cumulative reward over time.

Basically, imagine you're trying to find the best way to play a game to earn the most points. Value Iteration is like a strategy to figure out the best moves in the game.

 - Initialization: Start with V0(s) = 0 for all states s. We initialize V0(s) to 0 because we haven't considered any actions or rewards yet, so our initial estimate for the value of each state is zero.
	 - Imagine you're trying to find the best way to play a game to earn the most points. Value Iteration is like a strategy to figure out the best moves in the game.
	 
 - Iterative Updates: Given the current value function Vi, calculate the values for all states for the next depth (i+1) using the Bellman update equation:
	 - Vi+1(s) = max_a [sum_s' (T(s, a, s') * (R(s, a, s') + γ * Vi(s')))]
	 - This equation calculates the value of a state (s) by considering all possible actions (a) and their consequences. It computes the expected reward (R) for taking each action, plus the discounted (γ) value of the next state (Vi(s')). The value for the next iteration (Vi+1(s)) is the maximum expected value over all actions.
	 - Update the guess: For each place in the game, we consider all the possible moves and their outcomes. We calculate the points we'd get for each move and the points we could get in the future (discounted a bit). We choose the move that gives us the most points and update our guess for that place in the game.
	 
 - Discarding Old Values: After each iteration, discard the old Vi values and keep the updated Vi+1 values.
	 - Keep the new guesses: After updating all the guesses, we throw away the old ones and keep the new ones.
	 
 - Convergence: Repeat the iterative updates until the value function converges (the values don't change significantly between iterations).
	 - Keep the new guesses: After updating all the guesses, we throw away the old ones and keep the new ones.

Value Iteration is guaranteed to converge to the unique optimal values, as the approximations get refined towards the optimal values over time. The optimal policy (the best sequence of actions) may converge long before the value function does.

## Policy Iteration

Value iteration is a dynamic programming algorithm used to solve Markov Decision Processes (MDPs). It iteratively computes the optimal value function for each state and improves the estimated value function until convergence. The main problem with value iteration is that it can be slow, as it considers all actions at each iteration, which takes |A| times longer than policy evaluation.

Policy iteration is an alternative to value iteration, which can be more efficient in some cases. It works by iteratively updating the policy based on a fixed policy and improving it with one-step lookahead. Policy iteration consists of two main steps: policy evaluation and policy improvement.

1. Policy Evaluation:
	1. In this step, the algorithm calculates the utilities for a fixed policy. It's important to note that these utilities are not optimal but are an approximation based on the current policy. The policy evaluation step converges quickly since the policy remains unchanged during this process.
2. Policy Improvement:
	1. Once the policy evaluation step converges, the algorithm moves to the policy improvement step. In this step, the policy is updated using a one-step lookahead with the converged utilities (which are not optimal). This step can be slow, but it happens infrequently, making it more efficient than the value iteration algorithm in some cases.

The policy iteration algorithm repeats these two steps until the policy converges. Despite being an alternative to value iteration, policy iteration is still an optimal algorithm for solving MDPs.

## Difference Between Value and Policy Iteration?

Alright, imagine you're playing a video game, and you want to find the best way to reach the highest score. The game has multiple levels, and in each level, you have different actions you can take. You want to find the best action to take at each level to maximize your score.

Policy iteration and value iteration are two methods to figure out the best actions to take in the game.

 - Value Iteration:
	 - In value iteration, you start by guessing how good each level is (like assigning points to each level). Then, you go through each level, look at all the possible actions you can take, and calculate how good each action is based on the points you assigned to the levels. You keep updating your guesses about the points for each level and repeat this process until your guesses don't change much.
	 
 - Policy Iteration:
	 - In policy iteration, you start by coming up with a strategy (like choosing to always go left). Then, you calculate how good this strategy is by figuring out how many points you'd get if you followed it. After that, you try to improve your strategy by looking at each level and checking if taking a different action would give you more points, based on your current strategy's points. You keep repeating these steps (evaluating your strategy and improving it) until your strategy doesn't change much.

# Reinforcement Learning

## Passive Learning
 - Don't know the transitions T(s,a,s')
 - Don't know rewards R(s,a,s')
 - Given Policy 
 - Goal: Learn state values
 
## Model Based Learning
 - Learn the model empirically through experience
 - Solve for values as if mode is correct
 - Simple model learning:
	 - Count outcomes for each s,a
	 - Normalize to give estimate of T(s,a,s')
	 - Discover R(s,a,s') when we experience (s,a,s')
 - In Model Based Learning, you try to understand how the game works, like what happens when you take certain actions and what rewards you get. You create a "model" of the game in your head, which helps you plan your actions and make better decisions. It's like learning the rules and mechanics of the game so you can strategize better.

## Temporal Difference Learning
 - Learn from every experience
	 - Update V(s) each time we experience (s,a,s',r)
	 - Likely s' will contribute to updates more often
 - Policy is still fixed
 - Move values towards value of whatever successor occurs: running average
 - Discount Factor is to lower the effect of previous states on the current
 - ![[Pasted image 20230213182111.png]]
 - In Temporal Difference Learning, you learn by looking at the difference between what you thought would happen and what actually happened. For example, if you thought you'd get a high score by going left but actually got a low score, you'd learn from that difference and adjust your expectations. This method helps you learn from your mistakes and improve your gameplay over time.

## Exponential Moving Average
 - Average, but most recent samples more important
 - ![[Pasted image 20230213182226.png]]
 - Forgets about the past since those values are wrong anyways
 - Easy to compute from running average
 - ![[Pasted image 20230213182307.png]]
 - Decreasing learning rate makes averages converge
 - Exponential Moving Average is a way to keep track of your performance and make predictions about how well you'll do in the future. It's like taking a weighted average of your past scores, where recent scores have more weight (or importance) than older scores. This helps you see trends and figure out if you're improving or if you need to change your strategy.

## Q-Learning

 - Q-Learning: sample-based Q-value iteration
 - Learn Q*(s,a) values
	 - Receive a sample (s,a,s’,r)
	 - Consider your old estimate: Q(s,a)
	 - Consider your new sample estimate:
	 - ![[Pasted image 20230213183207.png]]
	 - Incorporate the new estimate into a running average:
	 - ![[Pasted image 20230213183225.png]]
- Amazing result: Q-learning converges to optimal policy
	- If you explore enough
	- If you make the learning rate small enough
	- ... but not decrease it too quickly!
	- Basically doesn’t matter how you select actions (!)
- Cannot learn about every state in realistic situation
	- Too many states to visit them all in training
	- Too many states to hold q values in memory
- Must generalize states
	- Transfer learning???
- Q learning is a technique where you learn the value of taking certain actions in different situations. Instead of trying to understand the game's rules like in Model Based Learning, you focus on finding the best actions to take that will lead to the highest score. You learn by trying out different actions and updating your knowledge about how good each action is in different situations.
### Linear Features
 - Using features to generalize states
 - Write a q funciton for any state using a few weights
 - Advantage
	 - Experienced summed up in few but powerful numbers
 - Disadvantage
	 - States share features but value very different

# Summary

MDPs (Markov Decision Processes) are a widely-used formulation for planning under uncertainty, which is common in real-world problems. An MDP solution is a policy rather than a plan, as it provides a general strategy for making decisions in different situations instead of a specific sequence of actions.

Key concepts in MDPs include the value function, Q-value, optimal value, and optimal policy. These concepts form the basis of dynamic programming algorithms that can be used to solve MDPs. The value function estimates the expected long-term reward for each state, while the Q-value estimates the value of taking a specific action in a state. The optimal value is the highest possible value that can be obtained from a state, and the optimal policy is the strategy that leads to achieving the optimal value.

There are several algorithms for solving MDPs, such as Value Iteration and Policy Iteration. Value Iteration works by iteratively updating the estimated value function until it converges to the optimal value function. Policy Iteration, on the other hand, alternates between evaluating a fixed policy and improving it using one-step lookahead. Both algorithms ultimately converge to the optimal policy.

Reinforcement Learning (RL) is a class of algorithms for learning MDPs. There are two main types of RL algorithms: Passive Learning and Active Learning. Passive Learning involves learning from a fixed policy, while Active Learning involves learning while making decisions and interacting with the environment.

In Passive Learning, there are several algorithms, such as Direct Evaluation, Model-based Learning, Temporal Difference (TD) Learning, and Q-learning. Direct Evaluation involves estimating the value function directly from experience. Model-based Learning creates a model of the environment to make predictions and learn the value function. TD Learning learns by comparing predictions with actual outcomes and adjusting the value function accordingly. Q-learning is a popular off-policy algorithm that learns the optimal Q-values for each state-action pair.

Active Learning involves learning while making decisions and interacting with the environment. This requires exploration strategies to balance the need for gathering information and maximizing rewards. Feature-based representation is another important aspect of Active Learning, as it allows for generalization and learning in high-dimensional or continuous state spaces.

In conclusion, MDPs provide a powerful framework for planning under uncertainty. Algorithms like Value Iteration and Policy Iteration can be used to find the optimal policy for a given MDP, while Reinforcement Learning algorithms, such as Passive and Active Learning, offer ways to learn MDPs in various scenarios. The combination of these concepts and algorithms enables intelligent agents to make effective decisions in uncertain environments.