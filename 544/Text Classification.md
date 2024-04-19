Let's reintroduce the specific equations and mathematical descriptions back into your notes, especially for the TF-IDF section, which is crucial for understanding how it's calculated:

---

**Overall Definition:** 
Text classification involves categorizing data instances into "classes" based on their similarities.

## Preprocessing
- **Tokenization**: Remove extra spaces and non-essential tokens or characters.
- **Optional Techniques**: Include lemmatization, lower casing, and contracting to refine tokens.

## Feature Extraction
### Simple Method: Bag of Words (BoW)
- Description: Represents text as an array counting each word’s occurrence.
- Limitations:
  - Lacks contextual information.
  - Fails to capture word dependencies (e.g., "New York" vs. "new book").
  - Dominated by common words.
  - Results in highly sparse matrices.

### Advanced Method: TF-IDF
- **Term Frequency (TF)**: The frequency of a word in a document, calculated as:
 $$ 
  \text{TF}(word) = \frac{\text{Number of times the word appears in the document}}{\text{Total number of words in the document}}
  $$
- **Inverse Document Frequency (IDF)**: Measures a word's informativeness, calculated as:
$$  
  \text{IDF}(word) = \log\left(\frac{\text{Total number of documents}}{\text{Number of documents containing the word}}\right)
  $$
- **TF-IDF Score**: The product of TF and IDF, emphasizing words that are distinctive to a document:
$$  
  \text{TF-IDF} = \text{TF}(word) \times \text{IDF}(word)
  $$

## Models: Generative vs Discriminative
### Generative Models
- Model the joint probability distribution P(X, Y).
- Use Bayes' rule to estimate P(Y|X), the posterior probability of a class given the input.
- Useful for text generation but can be complex and sensitive to outliers.

### Discriminative Models
- Directly model the conditional probability P(Y | X).
- Focus on minimizing classification errors and are generally more effective.
- Can overfit smaller datasets due to their sensitivity to feature design.

## Perceptron
- Historical Context: The first neural network model from the 1960s, inspired by the nervous system.
- Structure: Simple, single-layer model with multiple inputs and one output.
- Perceptron Convergence Theorem: Guarantees a solution if one exists, provided the data is linearly separable.
- Limitation: Not effective for non-linearly separable data.

## Challenges in Traditional Text Classification
- Heavy reliance on model optimization, assuming features are predefined.
- Insufficient focus on feature representation, relying mostly on frequency (BoW, TF-IDF) without capturing semantics or context.

These additions provide a clearer mathematical foundation for your notes, particularly for understanding how TF-IDF works in practical terms.