Review:
n 1936 Alan Turing described:  
• A simple formal model of computation now known as Turing machines.  
• A proof that TM can NOT solve the halting problem.  
• A proof that NO Turing machine can determine whether a given  
proposition is provable from the axioms of first-order logic.  
• Compelling arguments that a problem not computable by a Turing  
machine is not “computable” in the absolute (human) sense.  
• A non-deterministic Turing machine: for each state it makes an  
arbitrary choice between a finite of possible transitions.
Non-Deterministic Turing Machine  
• NDTM is a choice machine: for each state it makes an arbitrary  
choice between a finite (possibly zero) number of states.  
• The computation of a NDTM is a tree of possible configuration paths.  
• One way to visualize NDTM is that it makes an exact copy of itself  
for each available transition, and each machine continues the  
computation.  
• Rabin & Scott in 1959 shown that adding non-determinism does not  
result in more powerful machine.  
• For any NDTM, there is a DTM that accepts and rejects exactly the  
same strings as NDTM.  
• P vs. NP is about whether we can simulate NDTM in polynomial time.
Complexity Classes  
P = set of problems that can be solved in polynomial time by a DTM.  
NP = set of problems for which solution can be verified in  
polynomial time by a deterministic TM.  
X is NP-Hard, if ∀Y ∈ NP and Y ≤p X.  
X is NP-Complete,  
if X is NP-Hard and X  NP.  
NP = set of problems that can be solved in polynomial time by a NDTM.

It’s not known if NPC problems can be solved by a deterministic TM in  
polynomial time.  
NPC problems are  
the most  
difficult NP  
problems.  
optimization &  
decision  
problems  
NPC problems can be solved by a non-deterministic TM in polynomial  
time.