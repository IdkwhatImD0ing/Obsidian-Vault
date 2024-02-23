### 1. Classical Machine Learning

Classical machine learning encompasses algorithms that allow computers to learn from and make predictions or decisions based on data. Here are the key topics within classical ML:

#### Decision Trees and Ensembles

- **Decision Trees**: A decision tree is a flowchart-like structure where each internal node represents a "test" on an attribute (e.g., whether a coin flip comes up heads or tails), each branch represents the outcome of the test, and each leaf node represents a class label (decision taken after computing all attributes). The paths from root to leaf represent classification rules.

- **Ensembles**: An ensemble method combines multiple machine learning models to improve the overall performance. The most common ensemble methods using decision trees are:
  - **Random Forests**: Builds multiple decision trees and merges them together to get a more accurate and stable prediction.
  - **Gradient Boosting Machines (GBM)**: Sequentially adds predictors to an ensemble, each one correcting its predecessor. GBM specifically uses decision trees as the base learners.
  - **AdaBoost (Adaptive Boosting)**: Similar to GBM, but adjusts the weights of incorrectly classified instances so that subsequent classifiers focus more on difficult cases.

#### k-Nearest Neighbors (k-NN)

- **k-NN**: A simple, instance-based learning algorithm where the class of a sample is determined by the majority class among its k nearest neighbors. k-NN can be used for both classification and regression tasks. Key points include:
  - **Distance Metrics**: The algorithm uses distance metrics (such as Euclidean distance) to find the closest neighbors.
  - **Lazy Learning**: k-NN is a type of lazy learning as it does not build a model until a prediction is required.
  - **Choice of k**: The choice of k affects the classification/regression accuracy. A small value of k makes the model sensitive to noise, whereas a large value makes it computationally expensive and possibly less accurate.

#### Clustering

- **Clustering**: A type of unsupervised learning used to group unlabeled data points into clusters based on similarity. The main algorithms include:
  - **K-Means**: Partitions n observations into k clusters in which each observation belongs to the cluster with the nearest mean.
  - **Hierarchical Clustering**: Builds a tree of clusters by iteratively merging or splitting existing clusters.
  - **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)**: Forms clusters based on the density of data points, capable of finding arbitrarily shaped clusters and identifying outliers.

#### Anomaly Detection

- **Anomaly Detection**: The process of identifying unusual patterns that do not conform to expected behavior. It is widely used in fraud detection, system health monitoring, and outlier detection in data analysis. Key approaches include:
  - **Statistical Methods**: Assuming normal distribution and using statistical tests to find outliers.
  - **Isolation Forest**: An ensemble method that isolates anomalies instead of profiling normal data points.
  - **One-Class SVM**: A version of SVM (Support Vector Machine) that is trained only on the normal data and predicts whether a new data point is normal or an anomaly.

--- 

### Neural Network Basics

Neural networks are computational models inspired by the human brain, capable of capturing complex patterns in data. Here are the essential topics within neural network basics:

#### Perceptron Revisited

- **Perceptron**: The perceptron is the simplest type of neural network, consisting of a single neuron. It can be used for binary classification tasks (e.g., determining whether an email is spam or not spam). The key points include:
  - **Structure**: A perceptron takes multiple input features, multiplies each by a weight, sums them up, adds a bias, and then passes the result through an activation function (usually a step function) to produce an output.
  - **Learning**: The perceptron learns by adjusting its weights based on the errors it makes. The learning rule updates the weight of each input based on whether the perceptron correctly classified the input.
  - **Limitations**: Perceptrons can only classify linearly separable sets of data. Complex problems requiring nonlinear solutions cannot be solved by a single perceptron.

#### Gradient Descent

- **Gradient Descent**: A core optimization algorithm used to minimize the cost function in neural networks. It is used to update the parameters (weights and biases) of the network to reduce the difference between the predicted output and the actual output. Key aspects include:
  - **Process**: Gradient descent iteratively adjusts parameters in the opposite direction of the gradient of the cost function with respect to the parameters.
  - **Learning Rate**: A hyperparameter that controls how much we adjust the parameters with respect to the gradient. Too small a learning rate makes the learning slow, while too large a rate can lead to overshooting the minimum.
  - **Variants**: Stochastic Gradient Descent (SGD), Mini-batch Gradient Descent, and Batch Gradient Descent are variants that differ in the amount of data used to compute the gradient of the cost function.

#### Forward Propagation

- **Forward Propagation**: The process of calculating the output of a neural network by applying weights and biases through its layers and passing the result through activation functions. The main steps are:
  - **Input Layer**: Receives the input features.
  - **Hidden Layers**: Each neuron in these layers computes a weighted sum of its inputs, adds a bias, and applies an activation function. The number of hidden layers and the number of neurons in each layer define the architecture of the network.
  - **Output Layer**: Produces the final prediction of the neural network. For classification tasks, the output layer often uses a softmax function to generate probabilities for each class.
