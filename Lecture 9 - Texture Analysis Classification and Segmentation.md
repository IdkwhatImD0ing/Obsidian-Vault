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
2/9/25 44