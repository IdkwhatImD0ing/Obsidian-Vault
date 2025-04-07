# Texture Definition and Applications

**Texture**  
- Texture does not have a formal mathematical definition; it is defined by examples.  
- It refers to the spatial arrangement of intensities or colors that form patterns on surfaces or regions.  
- Examples include natural patterns such as water ripples, grassy fields, wood grains, and cloud formations.  

**Characteristics in Natural Images**  
- Most natural images contain a mixture of smooth regions, textured regions, and edge regions.

**Applications of Texture Analysis**  
- **Remote Sensing:** Segmentation and classification of satellite images (e.g., identifying water bodies, forests, urban areas).  
- **Medical Imaging:** Analysis of tissue textures to detect abnormalities.  
- **Low-Level Computer Vision:** Extracting texture features from images to predict labels or perform segmentation.

**Challenges in Texture Analysis**  
- Textures are often **quasi-periodic** and can be modeled as a 2D random field.
- They are frequently dominated by **high-frequency components** making analysis and segmentation challenging.

---

# Texture Segmentation and Feature Extraction

**Texture Segmentation Problem**  
- The goal is to partition an image into regions based on differing texture types.  
- For example, in a mosaic image with patches of grass, water, and sand, segmentation would label each region according to its texture.

**Pixelwise Response and Its 2nd Order Statistics**  
- **Filtering Process:**  
  - The texture image is scanned pixel by pixel (using a stride of 1) with a bank of filters (e.g., a set of 3×3 Laws’ filters).  
  - Using 9 filters results in 9 response images; thus, each pixel is represented by a 9-dimensional response vector.

- **Second-Order Statistics:**  
  - **Mean Vector:**  
    - The low-low (LL) filter response typically has a non-zero mean, whereas the other 8 responses are designed to have zero mean.  
  - **Covariance Matrix:**  
    - This symmetric, diagonally dominant matrix captures the variance and pairwise correlations between different filter responses.  
    - In practice, there is often weak correlation between different elements of the feature vector.

*Example:* Consider analyzing a wood texture. The filtering process might capture repetitive grain patterns, and the covariance matrix will help quantify the variability in these patterns.

---

# Digression: Basic Machine Learning

## Supervised vs. Unsupervised Machine Learning

**Supervised Machine Learning**  
- **Definition:** Models are trained using labeled data provided by humans.  
- **Variants:**  
  - **Heavily Supervised:** The number of training samples is much larger than the number of test samples.  
  - **Weakly Supervised:** The training sample count is smaller relative to test samples.  
- **Example:** A structured edge detector trained on images with human-annotated edges.

**Unsupervised Machine Learning**  
- **Definition:** Models work with data that are not labeled.  
- **Example:** Edge detectors like Sobel and Canny, which do not rely on pre-labeled training data.

---

## Commonly Used Supervised Classifiers

- **Nearest Neighbor (NN) and k-Nearest Neighbor (kNN):** Classify based on the closest training examples.  
- **Support Vector Machine (SVM):** Finds the hyperplane that best separates classes.  
- **Random Forest (RF):** Uses multiple decision trees to vote on the class label.  
- **Multi-layer Perceptron (MLP):** A type of neural network that can learn non-linear mappings.  
- **Adaptive Boosting (Adaboost):** Combines weak classifiers to form a strong classifier.  
- **Gradient Boosting / XGBoost:** Ensemble methods that optimize performance via iterative improvements.

*Example:* In texture classification, an SVM might be used to differentiate between wood, fabric, and stone textures based on their extracted features.

---

# Distance-Based Classification

**General Principle:**  
- For a test image's feature vector, compute the distance to each class centroid.  
- The class with the **minimum distance** is chosen as the predicted label.

**Distance Metrics:**  
- **Euclidean Distance:**  
  $$ d(x, y) = \sqrt{\sum_{i=1}^{D} (x_i - y_i)^2} $$
  - Works well when the variance in each feature dimension is normalized.
- **Mahalanobis Distance:**  
  $$ d_M(x, y) = \sqrt{(x-y)^T S^{-1} (x-y)} $$
  - Takes into account the covariance (i.e., variance and correlation) among features, which is useful when features have different scales.

*Example:* When classifying textures of fabric versus leather, the Euclidean distance might suffice if both feature sets are normalized; otherwise, Mahalanobis distance provides a more robust measure.

---

# Unsupervised Classification – K-means Clustering

**Objective:**  
- Given $N$ feature vectors in $\mathbb{R}^D$, partition them into $K$ clusters by minimizing the total distortion (i.e., the sum of squared distances between feature vectors and their corresponding cluster centroids).

**Algorithm Steps:**

1. **Initialization ($m = 0$):**  
   - Randomly select $K$ feature vectors to serve as initial cluster centroids (forming a codebook).

2. **Generalized Lloyd Iteration (for $m=0,1,\dots$):**  
   - **Assignment Step:**  
     For each feature vector $x$, assign it to the cluster whose centroid $y_i$ minimizes the distance:
     $$ R_i = \{ x : d(x,y_i) < d(x,y_j), \; \forall j \neq i \} $$
   - **Update Step:**  
     Recompute each centroid as the mean of all feature vectors assigned to that cluster.

**Comments on K-means:**  
- The optimization is **non-convex** and can converge to local minima.  
- Results are sensitive to the initial centroid choice.  
- Selecting the optimal number of clusters $K$ is itself a challenging problem.

*Example:* In a texture mosaic image containing grass, water, and sky, k-means might group pixels into three clusters corresponding to these textures, even if the boundaries are not clearly defined.

---

# Supervised Distance-Based Classification

**Nearest Neighbor Classifier:**  
- Assumes that the variation **within** a cluster (intra-cluster) is smaller than the variation **between** clusters (inter-cluster).  
- **Steps:**  
  1. Compute the centroid for each texture class using the training data.  
  2. For a new test image, calculate the distance between its feature vector and each class centroid.  
  3. Assign the test image to the class with the smallest distance.

*Example:* In a system trained on different types of fabric textures, a new fabric sample's features are compared to the centroids of known fabric types, and the closest match is chosen as its label.

---

# Texture Classification vs. Texture Segmentation

**Texture Classification (Supervised):**  
- **Task:** Given exemplar texture images from various classes (e.g., texture type A, B, C), predict the texture class of a new image.  
- **Approach:**  
  - Use the entire image as the analysis window.
  - Compute the average feature vector over all pixels.
  - With $C$ classes, and for each class having $N_c$ training images, the centroid for each class is computed as:
    $$ \text{Centroid}_c = \frac{1}{N_c} \sum_{i=1}^{N_c} f_i $$
    where $f_i$ is the feature vector for the $i$-th training image.

**Texture Segmentation (Unsupervised):**  
- **Task:** Partition a single mosaic image containing multiple textures into regions based on texture similarity.  
- **Approach:**  
  - Extract texture features pixelwise.
  - Use clustering (e.g., k-means) to group similar texture regions without prior labels.

*Example:* In satellite imagery, texture classification might be used to identify different land-cover types given training examples, whereas texture segmentation would automatically delineate regions like forests, urban areas, and water bodies within one large image.

---

# Summary

- **Texture** is defined by its pattern examples rather than a strict mathematical definition.
- **Applications** span remote sensing, medical imaging, and low-level computer vision tasks.
- **Feature Extraction** involves filtering (e.g., Laws’ filters) and computing second-order statistics like mean vectors and covariance matrices.
- **Machine Learning Approaches:**  
  - **Supervised methods** (e.g., SVM, kNN) are used for texture classification where labeled examples are available.
  - **Unsupervised methods** (e.g., k-means clustering) are applied to texture segmentation where labels are not provided.
- **Distance Metrics** such as Euclidean and Mahalanobis distances are key in comparing feature vectors for classification.

These concepts and techniques form the foundation for analyzing and classifying textures in various computer vision applications.


Why is image segementation so difficult?
Good number of segments
3d information to segment, computers only have 2d
Semantics can be used for humans, but computers weak at semantic understanding

Several Ideas  
• Contour detection (contour serves as a separator)  
• Active contour  
• Region growing  
• Watershed  
• Graph-based  
• Pixels are nodes, their similarity is defined by an edge value  
• Very similar -> small edge value  
• Very different -> large edge value  
• How to define similarities? mostly related to color (could be others)  
• Superpixel methods  
2/24/25 8
Superpixel Methods  
• Superpixel algorithms group pixels into perceptually meaningful  
regions while respecting potential object contours, and thereby can  
replace the rigid pixel grid structure  
• Due to the reduced complexity, superpixels were popular for various  
unsupervised computer vision applications  
• Examples: multiclass object segmentation, depth estimation, human pose  
estimation, and object localization.


Superpixel Methods  
• Superpixel algorithms group pixels into perceptually meaningful  
regions while respecting potential object contours, and thereby can  
replace the rigid pixel grid structure  
• Due to the reduced complexity, superpixels were popular for various  
unsupervised computer vision applications  
• Examples: multiclass object segmentation, depth estimation, human pose  
estimation, and object localization.

Simple Linear Iterative Clustering (SLIC)  
• Cluster pixels in the five-dimensional color and pixel coordinate space  
(e.g., r,g,b,x,y)  
• Initialization  
• Begin with a collection of K cluster centers initialized at an equally sampled regular  
grid on the image of N pixels  
• For each cluster, you define for a localized window 2S x 2S centered at the cluster  
center, where S=N/K−−−−√ is the roughly the space between the seed cluster centers  
• Iteration  
• Check whether the pixel within the 2S x 2S local window should be assigned to the  
cluster center or not (by comparing the distance in 5D space to the cluster center)  
• Once you loop through all the clusters, you can update the cluster center by  
averaging over the cluster members. Iterate the pixel-to-cluster assignment process  
till convergence or maximum iterations reached