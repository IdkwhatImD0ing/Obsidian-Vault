### Logical Entailment
KB :  a set of sentences
a : arbitrary sentence
KB *entails* a - written as KB|=a - iff every model of KB is a model of a

### Logical Equivalence
Two sentences a and b are logically equivalent writen as a triple = b -- iff  they have the same models
 - α ≡ β iff α |= β and β |= α
 - Examples:
	 - (α ∧ β) ≡ (β ∧ α)
	 - α ⇒ β ≡ ¬α ∨ β

### What is a Model?

Models are formal definitions of possible states in a world.
```
Just like a model airplane represents a real airplane, these models represent real-world situations, but in a more simplified and abstract way.
```
 - We say m is a model of a sentence α if α is true in m
	 - This means that if a model (m) accurately represents a situation described by a sentence (α), we can say that the model (m) is a model of that sentence (α). The sentence (α) has to be true in the model (m) for this to happen.
 - M(α) is the set of all models of α.
	 - This is just a fancy way of saying that M(α) is a collection of all the different models that make the sentence (α) true. It's like a group or list of all the models that can represent the situation described by the sentence (α).
 - Then KB *entails* α if and only if M(KB) ⊆ M(α)
	 - This point talks about a "knowledge base" (KB), which is a collection of information or facts that an AI system has. 
	 - The idea here is that we can say the knowledge base (KB) "knows" the sentence (α) if the set of models that make the knowledge base true (M(KB)) is a subset of the set of models that make the sentence (α) true (M(α)).
	 - In other words, if all the models that make the knowledge base (KB) true are also models that make the sentence (α) true, then we can say the knowledge base (KB) "knows" the sentence (α).

### Inference

Inference is a process in which you draw conclusions based on the information or knowledge you have. It's like solving a puzzle or a mystery based on the clues you've been given.

 - "KB ⊢i α: sentence α can be derived from KB by procedure i."
	 - This means that if you have a knowledge base (KB) which contains all the information you know, and a procedure or method (i) for making conclusions, you can use that method to derive or figure out a new piece of information or a conclusion, represented by the sentence (α).
 - "Soundness: i is sound if whenever KB ⊢i α, it is also true that KB ⊨ α."
	 - Soundness is a property that we want our inference procedure (i) to have. If a procedure is "sound," it means that whenever we use it to derive a conclusion (α) from our knowledge base (KB), that conclusion is always true. Basically, a sound procedure won't lead us to any false conclusions.
	 - So, if our procedure (i) is sound, and we can derive a sentence (α) from our knowledge base (KB) using that procedure (KB ⊢i α), then it must also be true that the sentence (α) is true based on our knowledge base (KB ⊨ α).
 - "Completeness: i is complete if whenever KB ⊨ α, it is also true that KB ⊢i α."
	 - Completeness is another property we want our inference procedure (i) to have. If a procedure is "complete," it means that it can always find a conclusion (α) that's true based on our knowledge base (KB), as long as that conclusion actually exists.
	 - In other words, if a sentence (α) is true based on our knowledge base (KB ⊨ α), and our procedure (i) is complete, then we should be able to derive that sentence (α) from our knowledge base (KB) using our procedure (i) (KB ⊢i α).



## Forward Chaining

Idea: Fire any rule whose premises are satisfied in the KB and add its
conclusion to the KB, until query is found

Forward Chaining is a reasoning technique used in artificial intelligence and knowledge representation, particularly in expert systems and rule-based systems. It starts with the available facts or data (the knowledge base) and uses inference rules to draw conclusions or make predictions.

Forward Chaining can be summarized in the following steps:

1. Start with a knowledge base containing facts and rules.
2. Find all the rules whose premises are satisfied by the facts in the knowledge base.
3. Apply these rules and add their conclusions to the knowledge base.
4. Repeat steps 2 and 3 until the query is found in the knowledge base or no more rules can be applied.

![[Pasted image 20230222175020.png]]

## Backwards Chaining
 - Idea: work backward from the query q to prove q using BC
	 - Check if q is known already, or
	 - Prove by BC all premises of some rule concluding q
 - Avoid loops: check if new subgoal is already on the goal stack
 - Avoid repeated work: check if new subgoal
	 - Has already been proved true
	 - Has already failed

Backward Chaining is a reasoning technique used in artificial intelligence, knowledge representation, and rule-based systems. It's the opposite of Forward Chaining. Instead of starting with the available facts and using rules to draw conclusions, Backward Chaining starts with a query or goal and works backward, trying to find a chain of rules and facts that can prove the query.

The basic idea of Backward Chaining can be summarized in the following steps:

1. Start with a query or goal you want to prove.
2. Check if the query is already known (in the knowledge base).
3. If not, find a rule that has the query as its conclusion
4. Try to prove the premises (conditions) of the rule using Backward Chaining (recursive step)
5. If all the premises of the rule can be proven, the query is proven as well
6. Avoid loops and repeated work by keeping track of the goals that have already been attempted.

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