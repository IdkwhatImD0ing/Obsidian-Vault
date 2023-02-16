## Logics
 - Logics are formal languages for representing information such that new conclusions can be drawn
 - Syntax: defines the sentences in the language
 - Semantics: define the “meaning” of sentences: i.e., define truth of a sentence in a world
 
### Entailment
 - One thing follows another
 - KB |= a
 - **A knowledge base KB entails sentence α if and only if α is true in all worlds where KB is true
 
## Models
 - Formal definition of possible states in a world
 - M is a model of a sentence a if a is _True_ in m
 - M(a) is the set of all models of a
 - KB|=a iif M(KB) is a subset of M(a)
 
### Inference
 - KB ⊢i α: sentence α can be derived from KB by procedure i
 - Soundness: i is sound if whenever KB ⊢i α, it is also true that  KB ⊨ α
 - Completeness: i is complete if whenever  KB ⊨ α, it is also true that KB ⊢i α

