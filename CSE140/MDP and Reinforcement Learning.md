## Utilities
 - Function that take in an outcome and return a number that describes the performance in that outcome
 - Where do utilities come from?
 - In a game, may be simple (+1/-1)
 - Utilities summarize the agent’s goals
 - Theorem: any “rational” preferences can be
summarized as a utility function

## MDPs
 - Markov Decision PRoperties
 -  MDPs are a family of non-deterministic search problems
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

## Reinforcement Learning

### Passive Learning
 - Don't know the transitions T(s,a,s')
 - Don't know rewards R(s,a,s')
 - Given Policy 
 - Goal: Learn state values
 
### Model Based Learning
 - Learn the model empirically through experience
 - Solve for values as if mode is correct
 - Simple model learning:
	 - Count outcomes for each s,a
	 - Normalize to give estimate of T(s,a,s')
	 - Discover R(s,a,s') when we experience (s,a,s')

### Temporal Difference Learning
 - Learn from every experience
	 - Update V(s) each time we experience (s,a,s',r)
	 - Likely s' will contribute to updates more often
 - Policy is still fixed
 - Move values towards value of whatever successor occurs: running average
 - ![[Pasted image 20230213182111.png]]

### Exponential Moving Average
 - Average, but most recent samples more important
 - ![[Pasted image 20230213182226.png]]
 - Forgets about the past since those values are wrong anyways
 - Easy to compute from running average
 - ![[Pasted image 20230213182307.png]]
 - Decreasing learning rate makes averages converge

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