## Probability Review

 - **Probability distributions**
	 - are tables that show the likelihood of different outcomes for unobserved random variables. 
	 - For example, a distribution for weather temperature (T) might have "warm" with a probability (P) of 0.5 and "cold" with a probability of 0.5. 
	 - Another distribution for weather type (W) might have "sun" with a probability of 0.6, "rain" with a probability of 0.1, and "fog" with a probability of 0.3.
 - **Joint distributions
	 - combine these individual distributions and assign a real number to each possible outcome of the combined variables. 
	 - The size of a joint distribution depends on the number of variables (n) and their domain sizes (d). 
	 - However, for large distributions, it's difficult to write out every possible outcome.
 - **Probabilistic Model: 
	 - A joint distribution over a set of random variables. It tells us the likelihood of different outcomes (assignments) happening together. 
	 - Example: Weather temperature (T) and weather type (W) combined.
 - **Constraint Satisfaction Problem: 
	 - A problem with variables, domains, and constraints specifying if assignments are possible.
	 - Example: T=W only if it's hot and sunny, or cold and rainy.
 - **Events: A set of outcomes.
	 - Example: Hot AND Sunny, Hot OR Sunny.
 - **Marginal Distributions:** 
	 - Sub-tables that eliminate variables by summing probabilities. 
	 - Example: Marginal distribution of temperature (T) - Hot: 0.5, Cold: 0.5.
 - **Conditional Probabilities:** 
	 - The likelihood of an event happening given another event has occurred. 
	 - Example: Probability of rain given it's cold - 0.6.
 - **Conditional Distributions:** 
	 - Distributions over some variables given fixed values of others.
	 - Example: Weather type (W) given it's hot - Sun: 0.8, Rain: 0.2.
 - **Normalization Trick:** 
	 - A method to get a conditional distribution at once by selecting joint probabilities matching evidence and normalizing the selection. 
	 - Example: ![[Pasted image 20230319170422.png]]
 - **Probabilistic Inference:** 
	 - Compute a desired probability from other known probabilities. 
 - **Inference by Enumeration:** 
	 - A method to calculate probabilities by selecting evidence-consistent entries and summing or normalizing. 
 - **Product Rule:** 
	 - A rule used to find the joint distribution using conditional distributions. 
	 - P(x|y) = P(x,y)/P(y) <==> P(x,y) = P(x|y) * P(y)
 - **Chain Rule:** 
	 - A method to write any joint distribution as an incremental product of conditional distributions. 
	 - Example: P(A, B, C) = P(A) * P(B|A) * P(C|A, B).
 - **Bayes' Rule:** 
	 - A rule to derive one conditional probability from its reverse. 
	 - Example: P(meningitis | stiff neck) derived from P(stiff neck | meningitis).
	 - P(x|y) = P(y|x) * P(x) / P(y)

## Probablistic Models

Models are simplified representations of how something in the world works. They don't include every detail or interaction between factors, but they can still be useful in understanding and predicting certain situations.

With probabilistic models, we use them to reason about things we don't know, based on the information we have. Here are three examples:

1.  Explanation (Diagnostic reasoning): Imagine you have a headache. A model might tell you that headaches are commonly caused by dehydration or lack of sleep. Based on this, you might conclude that you're probably dehydrated or didn't get enough sleep.
    
2.  Prediction (Causal reasoning): Suppose you know it's going to rain tomorrow. A model might tell you that rain usually causes traffic jams. Based on this, you can predict that there might be a traffic jam tomorrow because of the rain.
    
3.  Value of Information: Imagine you're deciding whether to bring an umbrella. A model tells you there's a 70% chance of rain. Knowing this, you can decide if it's worth carrying an umbrella, considering the likelihood of rain and the inconvenience of carrying the umbrella.

This is only three examples out of many

## Bayesian Networks
Purpose of Bayesian Networks
 - Facilitate the description of a collection of beliefs by making explicit causality relations and conditional independence among beliefs
 - Provide a more efficient way (than by using joint distribution tables) to update belief strengths when new evidence is observed