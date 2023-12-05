
Sometimes, classification is not.

Problem: Decide whether to wait for a table at a restraunt, based on the following attributes/features

Leaves of the tree of decisions
Nodes are questions. 
- Are there alternative restraunts
- Is the a comfortable bar area to wait in
- Is today Friday or Saturday
- Are we hungry?
- HOw mayn epeople are in the restraunt
- Whats the price
- etc
- 

### Inductive Learning of Decision Tree

Simplest: Construct a decision tree with one leaf for every example
Memory based learning, not good generalizaton

Advanced. split on each variable so that the purity of each split increases, eithe ronly yes or only no

Puyrety measure with entropy
Entropy = iP(Yes)ln[P(yes)]-P(no)ln[P(no)]

### How many distinct decision trees with n boolean attributes?
Number of boolean funciton
NUmber of distinct truth tables with 2^n rules = 2^2^n

# ID3 ALgorithm

Choose which attribute to split a given set of examples
Some possibilities"
- Random
- Least Values
- Most Values
- Max Gain
	- Largest expected information, smalest expected size of subtree

## Information Theory

- INformation is measured in bits
- Infomration is conveyed by message depends on its proibability
- With n equally probable possible messages, the probability of each is 1/p
- Information conveyed by a message is -log(p) = log(n)
	- eg with 16 messages then we n eed 4 bits to identify send each message
- Givebn a probability distribution P for n messages, the information conveyed by the distribution (entropy of P) is
- The information conveyed by the distribution (entropy of P) is I(P) = - \[p * log p1 + p2\*log p2 + ... pn * log pn*]


