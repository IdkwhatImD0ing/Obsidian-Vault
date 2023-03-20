## Probability Review

 - **Probability distributions**:
	 - are tables that show the likelihood of different outcomes for unobserved random variables. 
	 - For example, a distribution for weather temperature (T) might have "warm" with a probability (P) of 0.5 and "cold" with a probability of 0.5. 
	 - Another distribution for weather type (W) might have "sun" with a probability of 0.6, "rain" with a probability of 0.1, and "fog" with a probability of 0.3.
 - **Joint distributions:**
	 - combine these individual distributions and assign a real number to each possible outcome of the combined variables. 
	 - The size of a joint distribution depends on the number of variables (n) and their domain sizes (d). 
	 - However, for large distributions, it's difficult to write out every possible outcome.
 - **Probabilistic Model**:**
	 - A joint distribution over a set of random variables. It tells us the likelihood of different outcomes (assignments) happening together. 
	 - Example: Weather temperature (T) and weather type (W) combined.
 - **Constraint Satisfaction Problem:** 
	 - A problem with variables, domains, and constraints specifying if assignments are possible.
	 - Example: T=W only if it's hot and sunny, or cold and rainy.
 - **Events: A set of outcomes.**
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

## Independence

### Independent Random Variables: 
Two variables, X and Y, are independent if knowing the value of Y doesn't change the prediction of X. In this case, the joint probability P(X,Y) equals the product of their individual probabilities: P(X)P(Y). For multiple independent variables, the joint probability is the product of their individual probabilities.

### Conditional Independence: 
Two variables, X and Y, are conditionally independent given Z if knowing the value of Y doesn't change the prediction of X once we know Z. In this case, the conditional joint probability P(X, Y|Z) equals the product of their conditional probabilities: P(X|Z)P(Y|Z). This concept helps us model relationships between variables when they're not fully independent but become independent when considering another variable (Z).

## Bayesian Networks

A Bayes net (short for Bayesian network) is a tool that helps us visualize and understand these relationships using simple connections between the factors.

Think of it like a flowchart, where each factor (like weather or traffic) is a circle, and there are arrows showing how one factor affects another. These arrows represent local interactions, which are easy to understand on their own.

The cool thing about Bayes nets is that when you combine these local interactions, you can figure out more complex relationships that aren't obvious at first. For example, you might see that bad weather can cause traffic jams, and traffic jams can make you late for school. By following the arrows, you can see how weather indirectly affects whether you're late for school, even though the two factors aren't directly connected.

**Example:**
```
Imagine a situation where you want to know if there's a burglary at your friend's house. There's an alarm system, and two neighbors, John and Mary, who can call you if they hear the alarm.
```

### Encoding in BNs:
 - Represents relationships between variables using nodes and directed edges
 - Efficiently represents joint probability distributions by exploiting conditional independence
 - Variables are conditionally independent of non-descendants given parents
 - Example: 
	 - The variables here are:
		 - Burglary
		 - Earthquake
		 - Alarm
		 - JohnCalls
		 - MaryCalls.
	 - The BN would look like this:
		 - Burglary → Alarm 
		 - Earthquake → Alarm
		 - Alarm → JohnCalls 
		 - Alarm → MaryCalls

### Structure of BNs:
 - Directed acyclic graph (DAG) representing relationships among variables
 - Captures conditional independence relationships
 - Parents of a variable are variables that directly influence it
 - Enables efficient inference algorithms like belief propagation
 - Example:
	 - This BN tells you that JohnCalls and MaryCalls depend on the Alarm. They're independent of each other and the Burglary and Earthquake given the Alarm. The Alarm is affected by both Burglary and Earthquake.

### Construction of BNs:
 - Variable selection: Choose relevant random variables
 - Ordering: Arrange variables so direct influencers come before influenced variables
 - Add nodes and edges: Create nodes for variables, connect them to parents
 - Define CPTs: Specify probability distribution for each node's variable given its parents
 - Use constructed BN for inference, learning, and decision-making; requires domain expertise
 - Creating the example:
	1.  Choose variables: Burglary, Earthquake, Alarm, JohnCalls, MaryCalls
	2.  Order them: Burglary, Earthquake, Alarm, JohnCalls, MaryCalls
	3.  Add nodes and connections as shown above
	4.  Define the CPT for each node, showing the probability of each outcome given different scenarios


## Independence of Bayesian Networks

Given a set E of evidence nodes, two beliefs
connected by an undirected path are
independent if one of the following three
conditions holds:
1. A node on the path is linear and in E
	1. Picture a straight line of nodes. The first node affects the second, the second affects the third, and so on. 
	2. If you have evidence for a node in the middle of this line, then the beliefs before and after it don't affect each other.
		1. In a linear chain like A → B → C, if we have evidence for B (we know its value), then A and C become conditionally independent. It means that knowing A doesn't give us any extra information about C when we already know B, and vice versa.
		2. However, if we don't know B, then A does have an effect on C. In this case, A and C are not conditionally independent, and the relationship between A and C is indirect (through B).
2. A node on the path is diverging and in E
	1. Imagine a upside-down "V" shape, where one node affects two other nodes. If you have evidence for the top node of the "V", the two bottom nodes don't affect each other. 
	2. For example, if you know it rained (top node), the wet sidewalk (left bottom node) and wet car (right bottom node) are independent, because you already know the cause.
3. A node on the path is converging and neither this node, nor any descendant is in E
	1. Think of an "V" where two nodes affect a third one. If you have no evidence for the bottom node of the "V" or any of its descendants (nodes it affects), the two top nodes don't affect each other. 
	2. For example, a fire alarm (bottom node) can be triggered by a fire (left top node) or burnt toast (right top node). If you don't know anything about the alarm or related events, the fire and burnt toast are independent.

# Inference


## Inference in Chains

Inference in chains refers to computing the probability of a variable in a simple chain-like Bayesian Network. 

A chain is a linear sequence of variables, where each variable is connected to the next one by a single directed edge, like this: X1 → X2 → X3 → ... → Xn.

To compute the probability of the last variable in the chain, Xn, we can use a step-by-step approach. Instead of trying to compute P(Xn) directly, which could be computationally expensive, we compute the probability of each variable in the chain using the probability of the previous variable.

Here's how we do it:

1.  Compute P(X1), the probability of the first variable.
2.  Compute P(X2) using P(X1) and the conditional probability P(X2 | X1).
3.  Compute P(X3) using P(X2) and the conditional probability P(X3 | X2).
4.  Continue this process until we reach Xn.

## General Inference with Variable Elimination

General Inference with Variable Elimination is a technique used to compute probabilities in more complex Bayesian Networks, not just chains. The main idea is to rewrite the query as a summation of products and then iteratively eliminate variables by marginalizing them in a specific order.

Here's the process in an easy-to-understand way:

1.  Write the query in the form of a Summation of Products. This will suggest an "elimination order" of variables to be marginalized.
2.  Iteratively perform the following steps: 
	1. Move all terms that do not depend on the variable being eliminated outside of the innermost sum. 
	2. Perform the innermost sum, which means computing the sum over the variable being eliminated, and get a new term.
	3. Insert the new term into the product.
3.  Continue this process until all variables in the elimination order have been marginalized.