 Texture Definition and Applications  
• Texture  
• No formal mathematical definition  
• Defined by examples  
• Regions or surfaces exhibit certain patterns, e.g., water, grass, wood, cloud, etc.  
• Most natural images consist of smooth regions, textured regions and edge  
regions  
• Applications of Texture Analysis  
• Remote sensing image analysis (segmentation, classification, etc.)  
• Medical image analysis

in lo level cv
we take images, extract features, then do predicted lavels

Challenges of Texture Analysis  
• Quasi-periodic, 2D random field, dominated by high frequency  
components

TExture segmentation problem


Pixelwise Response and Its 2 nd Order Statistics  
• Scan the entire texture image pixel by pixel (stride = 1) using a bank of  
filters (e.g. 3x3 Laws’ filters)  
• 9 filters -> 9 responses -> a random vector of 9 dimensions -> response vector  
• Find the second-order statistics of the response vector  
• Mean vector  
• The LL response has a non-zero mean  
• The remaining 8 responses have the same mean (zero mean)  
• Covariance matrix  
• Symmetric matrix  
• Diagonally dominant matrix  
• Weak correlation between different elements of the feature vector  


Digression: Basic Machine Learning

Supervised versus Un-supervised Machine  
Learning  
• Supervised ML  
• Training data with labels provided by humans  
• Heavily supervised ML  
• The # of training samples is much larger than the # of test samples  
• Weakly supervised ML  
• The # of training samples is much smaller than the # of test samples  
• Un-supervised ML  
• No training data with human labels  
• Examples  
• Sobel and Canny edge detectors are un-supervised methods  
• Structured edge detector is a supervised method

Commonly Used Supervised Classifiers in  
Machine Learning  
• Nearest Neighbor (NN) classifier  
• k Nearest Neighbor (kNN) classifier  
• Support vector machine (SVM)  
• Random forest (RF)  
• Multi-layer Perceptron (MLP)  
• Adaptive Boosting (Adaboost)  
• Gradient Boosting and Extremely Gradient Boosting (XGBoost)

Distance-Based Classifiers  
• General principle  
• Compute the distance of the feature vector of a test image from each class’  
centroid and select the class that gives the minimum distance  
• What kind of distance  
• Euclidean distance?  
• This is fine if the variance of each dimension is normalized to unity  
• Otherwise, we should consider Mahalanobis distance  


Unsupervised Classifier – K-means Clustering (1)  
• Objective:  
• Cluster N feature vectors of dimension D, denoted by R D, into K clusters to  
minimize the total distortion between each feature vector and its associated  
cluster centroid  
• Initialization (m=0)  
• Select K feature vectors as the initial set of cluster centroids, called a  
codebook  
• Generalized Lloyd Iteration (m=0,1,...)  
• Given codebook C m = { y i, i = 1, ..., K } obtained from the m th iteration, find a  
new optimal partitioning of space R D using the nearest-neighbor condition to  
form the nearest-neighbor cells R i = { x: d(x,y i) < d(x,y j), j ¹ i

Comments on K-means Clustering  
• Non-convex optimization  
• There are multiple local minima  
• The converged solution is dependent on the initial centroid choice  
• The choice of the optimal K value is a problem  
What is the optimal K value?  

Supervised Distance-based Classifier (1)  
• Nearest Neighbor Classifier  
• Intra-cluster variation is smaller than inter-cluster variation  
• Compute the centroid of each cluster  
• Choose the class that has the smallest test sample-to-centroid distance

Differences  
• Texture classification is usually treated as a supervised learning  
problem  
• Offer exemplar texture images from several texture types (e.g. texture type A,  
texture type B, texture type C, etc.)  
• Given test image X, please find its texture type  
• Texture segmentation is typically treated as an unsupervised learning  
problem  
• One texture mosaic image that contains multiple texture types

Texture Classification  
• Choose the window size to be the same as the image size  
• Namely, take the average of feature vectors at all pixel locations  
• Suppose that there are C texture classes, where each class has Nc  
training images  
• Find the feature vector of each training image  
• Average the feature vectors of training images  
• Centroid of each class
