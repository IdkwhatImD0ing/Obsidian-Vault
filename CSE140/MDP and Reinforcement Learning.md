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