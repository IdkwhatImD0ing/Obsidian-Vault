## Basic Definitions

- P(X}: Probability X
- P(X^Y): Probability X and Y
- P(X | Y): Probability X if Y

## Two Key Concepts

- Probability Distribution Model
	- Real World
		- Possible worlds
		- Atomic Events
		- Samples
	- Mind
		- Variables
		- Value assignments (entailment)
	- Deviation
		- How spread is the distribution
	- Variance
		- How widely is the distribution spread
		- Deviation squared
	- Distributions
		- Fully Joint Probability Table
			- Multiple Probability Tables joined together
			- Possible worlds are mutually explosive
				- Cannot have multiple worlds at once
			- Possible worlds are exhaustive
				- All of the probabilities add to 1
- Inferences that can be made from the model
	- Sum rule
		- P(A|B) + P(~A|B) = 1, where ~A represents the negation of A. This rule states that the probability of event A occurring plus the probability of event A not occurring equals 1.
	- Product Rule
		- P (A and B) = P(A|B) * P(B) = P(B|A) * P(A), where P(A and B) represents the probability of both events A and B occurring.
		- P (A and B | C) = P(A|C) * P(B|AC) = P(B|C) P(A|BC)
	- Conditional Probability
		- Bayes Theorem
		- P (A | B) = P(A and B) / P(B)
	- Marginalization
		- Introducing a variable as an extra condition
		- To plug in the numbers we know
		- P(X|Y) = Summation of P(X|Y, Z = z) * P(Z = z|Y)

	- Normalization
		- Make the distribution sum to 1
		- Ensure that all the probabilities for a specific variable add up to 1 by adjusting the probabilities of each possible outcome. 
		- This is important for accurately representing the likelihood of each outcome within the distribution model.
### Formal Definition of  Probability Distribution MOdel

Set Omega - Sample Space
	Eg 6 possible rolls of dice

Probability space is defined as a triple (Ω, F, P), where Ω is the sample space, F is the set of events, and P is the probability measure defined on F.

An event A is any subset of the sample space Ω, and the probability of event A, denoted P(A), is the measure of the set A according to the probability measure P.


