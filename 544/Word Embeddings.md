# Challenges in Traditional Text Classification

## Key Challenges
- **Model Optimization**: Traditional approaches heavily rely on model optimization with a presumption that features are predefined.
- **Feature Representation**:
  - Focus mainly on frequency measures like Bag of Words (BoW) and TF-IDF.
  - Lack incorporation of semantics or contextual meanings.

## Word Embeddings

- **Characteristics**:
  - Uniform size for all words.
  - Represented by one dense vector.
  - Typically low dimensional.

### The Distributional Hypothesis
- **Origin**: Proposed by Firth in 1957.
- **Principle**: "Similar words occur in similar contexts", suggesting that words appearing in similar contexts tend to have similar meanings.

## Two Main Types of Word Embeddings

### 1. Prediction Based: Word2Vec

#### Overview
- **Full Name**: Distributed Representations of Words, Phrases, and their Compositionality.
- **Core Idea**: Learning embeddings via a prediction task that involves neighboring words in a large real-world corpus.

#### Characteristics
- **Contexts**: Surrounding words within a fixed small window in text.
- **Similarity Measure**: Conditional probability to predict a word occurring in the same context.
- **Model Variants**: Skip-Gram model, where a center word is used to predict context words.

#### Technical Details
- **Vocabulary and Dictionary of Words**.
- **Two Sets of Embedding Vectors**:
  - One input vector.
  - One output vector.
- **Probability Prediction**: Utilizes softmax function.

#### Challenges
- **Sparsity**: Vectors of frequent words are updated more than those of rare words.
- **Computational Expense**: High due to summation involved in probability calculation.
- **Interpretability**: Difficult to interpret Word2Vec vectors.

### 2. Factorization Based: GloVe

#### Overview
- **Full Name**: Global Vectors for Word Representation.
- **Developed by**: Stanford.
- **Core Principle**: Utilize word vectors to approximate pairwise mutual information of two words.

#### Characteristics
- **Similar to Word2Vec**:
  - Contains two sets of word vectors for each word: input (`uw`) and output (`vw`).

## Comparison: Word2Vec vs GloVe
- No single word embedding approach is considered state-of-the-art (SOTA) for all applications.

## Highlights

- "Similar words occur in similar contexts" — Firth, '57.
- Word2Vec and GloVe, while serving similar purposes, have unique characteristics and applications.
