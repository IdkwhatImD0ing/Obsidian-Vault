## Recall: Challenges in Traditional Text Classification
- Heavy reliance on model optimization, assuming features are predefined.
- Insufficient focus on feature representation, relying mostly on frequency (BoW, TF-IDF) without capturing semantics or context.

## Word Embeddings
- Same size used for all words
- One dense vector
- Relatively low dimentional

The Distributional Hypothesis in Computational Linguistics: “Similar words occur in similar contexts” (Firth, ’57)

## Two Main Types

### Prediction Based: Word2Vec
Core Idea: learning embeddings using a prediction task involving neighboring words in a huge real-world corpus
Contexts: surrounding words of a fixed small window in a piece of texts
Similarity: conditional probability to predict a word occurring in the same context
Skip-Gram: given a center word, we predict the context word

 - Vocab
 - Dictionary of words
 - Two sets of embeddig vectors
 - one input vector
 - one output vector
 - use softmax to predict probability

### Problems
Sparsity Problems
- Vectors of frequent words updated more than rare workds
Expensive computation
- Summation in probability

### Factorization Based: GloVe
