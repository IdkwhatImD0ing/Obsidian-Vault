Overall Definition: Text classification is the act of categorizing instances of data into "classes", where class members share some similarity

## Preprocessing

For preprocessing, we do the simple tokenization, where we remove extra spaces, unhelpful tokens, and characters

We can also do optional ones such as lemmatization, lower casing, contracting

## Feature Extracting

### Simple: Bag of Words

Simply have an array where the the number of each word i is the value j

Limitations:
- No contextual information
- No word dependencies: new york vs new book
- Dominant by common words
- Highly Sparese

### Better: TF-IDF
Core Idea: Reflect how important a word is to an instance in the dataset

**What is term frequency?**
The frequency of a word appears in a document
Word i in document / all words in document

**What is Inverse Document Frequency?**
Measuring how informative a word is
log(documents/documents with word i)
That means the less number of times the word appears in documents, the higher its IDF value will be.

**Result:** TF-IDF is simply the multiplication of the two scores

## Models: GEnerative vs Discriminative

### Generative: Modeling Joint Distribution P(X, Y)
Use Bayes rule to estimate the posterior probability of class Y given input X, P(Y|X).
Returns class to generate that instance

### Descriminative: Modeling Posterior P(Y | X)
Returns the exact function that minimizes clasification errors

**What is the Difference?**
- Discriminative classifiers are more effective, since they directly optimize the classification
	- Sensive to features, which are heuristically designed
	- Overfitting can happen if datasets are small
- Generative model the joint probability
	- Helpful when generating text
	- Harder thanproblem than classification
	- Vulnerable to outlier

## Perceptron

First Neural Network from 1960s
Nervous System

Simple, single layer models
Multiple INputs, one outputs

Perceptron Convergence Theorem: guaranteed to find a solution in finite time if a solution exists

Only problem is that if data points are not linearly seperable, then its not optimal.
