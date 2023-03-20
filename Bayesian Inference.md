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

## Independence

### Independent Random Variables: 
Two variables, X and Y, are independent if knowing the value of Y doesn't change the prediction of X. In this case, the joint probability P(X,Y) equals the product of their individual probabilities: P(X)P(Y). For multiple independent variables, the joint probability is the product of their individual probabilities.

### Conditional Independence: 
Two variables, X and Y, are conditionally independent given Z if knowing the value of Y doesn't change the prediction of X once we know Z. In this case, the conditional joint probability P(X, Y|Z) equals the product of their conditional probabilities: P(X|Z)P(Y|Z). This concept helps us model relationships between variables when they're not fully independent but become independent when considering another variable (Z).

## Bayesian Networks

A Bayes net (short for Bayesian network) is a tool that helps us visualize and understand these relationships using simple connections between the factors.

Think of it like a flowchart, where each factor (like weather or traffic) is a circle, and there are arrows showing how one factor affects another. These arrows represent local interactions, which are easy to understand on their own.

The cool thing about Bayes nets is that when you combine these local interactions, you can figure out more complex relationships that aren't obvious at first. For example, you might see that bad weather can cause traffic jams, and traffic jams can make you late for school. By following the arrows, you can see how weather indirectly affects whether you're late for school, even though the two factors aren't directly connected.

### Encoding in Bayesian Networks:

Encoding refers to the representation of the relationships between variables within a Bayesian Network (BN). A BN encodes dependencies between variables using nodes (representing the variables) and directed edges (representing dependencies). The edges point from parent nodes to child nodes, indicating the direction of influence.

The primary advantage of encoding in a BN is the efficient representation of joint probability distributions. This efficiency is achieved by exploiting the conditional independence properties between variables. A variable in a BN is conditionally independent of its non-descendants given its parents. This allows the representation of a joint probability distribution with a smaller number of parameters, making it easier to learn, understand, and update the BN as new information becomes available.

### Structure of Bayesian Networks:

The structure of a BN is a directed acyclic graph (DAG) that visually represents the relationships among variables. The nodes in the DAG represent random variables, while the directed edges represent direct causal relationships between variables.

The structure of a BN captures the conditional independence relationships among variables. In a BN, the parents of a variable X are all variables that directly influence X. The graph structure of a BN allows you to read off conditional independence relationships directly. The structure ensures that each variable is independent of its non-descendants given its parents, which in turn simplifies the representation of the joint probability distribution.

The structure of a BN is crucial for efficient inference, as it allows for the application of various algorithms that exploit the graph's properties. For example, message-passing algorithms like belief propagation can leverage the BN's structure to compute probabilities of interest in a distributed and efficient manner.

### Construction of Bayesian Networks:

Constructing a BN involves the following steps:

1. Variable selection: Choose the relevant random variables that describe the domain. These variables should capture the essential aspects of the problem you're trying to model.
2. Ordering: Select an ordering X1, ..., Xn of the variables such that all the variables that directly influence Xi come before Xi in the ordering. This step is essential to ensure that the BN respects the conditional independence properties among variables.
3. Adding nodes and edges: For each variable in the ordering, add a node to the network labeled by the variable. Connect the node to its parents (i.e., the variables that directly influence it) using directed edges.
4. Defining Conditional Probability Tables (CPTs): For each node in the network, define a CPT that specifies the probability distribution of the node's variable given its parents. The CPTs capture the local relationships between variables and enable the BN to represent the joint probability distribution over all variables.

Once the BN is constructed, it can be used for various tasks such as probabilistic inference, learning, and decision-making. The construction process often involves domain expertise to select the relevant variables and determine the appropriate structure that accurately represents the problem at hand.