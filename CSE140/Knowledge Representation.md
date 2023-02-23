### Logical Entailment
KB :  a set of sentences
a : arbitrary sentence
KB *entails* a - written as KB|=a - iff every model of KB is a model of a

### Logical Equivalence
Two sentences a and b are logically equivalent writen as a triple = b -- iff  they have the same models
 - a triple = b iff
 - a |= b
 - b |= a

## Forward Chaining

Idea: Fire any rule whose premises are satisfied in the KB and add its
conclusion to the KB, until query is found

![[Pasted image 20230222175020.png]]

## Backwards Chaining
 - Idea: work backward from the query q to prove q using BC
	 - Check if q is known already, or
	 - Prove by BC all premises of some rule concluding q
 - Avoid loops: check if new subgoal is already on the goal stack
 - Avoid repeated work: check if new subgoal
	 - Has already been proved true
	 - Has already failed

![[Pasted image 20230222175124.png]]

### Differences?
 - FC is data-driven
	 - Automatic, unconscious processing
	 - E.g. object recognition, routine decisions
	 - May do lots of work that is irrelevant to the goal
	 - Blindly expanding hoping to reach goal
	 - Uniform Cost Search
 - BC is goal-driven, appropriate for problem-solving
	 - E.g. Where are my keys? How do I get to my next class
	 - Complexity of BC can be much less than linear in the size of the KB