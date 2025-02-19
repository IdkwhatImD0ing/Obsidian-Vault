## 1. Image and Video Compression

### Overview

Image processing can be broadly divided into two main branches:

- **Compression:** Methods that reduce the size of image and video data.
- **Understanding:** Techniques that analyze and extract meaningful features from images (e.g., edges and contours).

### Image Compression

- **History:**
    - Began in the **1920s** with early image compression methods.
    - **JPEG** is a classic example of a lossy image compression standard that became widely adopted.
- **Example:**  
    A digital photograph is compressed using JPEG to reduce file size by discarding information that is less perceptible to the human eye.

### Video Compression

- **Timeline:**
    - Development from **1990 to 2020**.
    - Notable standards include **MPEG-1, MPEG-2, MPEG-4**, and more recently **H.265**.
- **Example:**  
    Streaming services use H.265 to deliver high-quality video at lower bit rates, reducing bandwidth usage while maintaining visual fidelity.

---

## 2. Image Understanding: Edge and Contour Detection

### Goals and Definitions

- **Edge Detection:**
    
    - A _low-level vision task_ focused on identifying sharp changes in image brightness.
    - Often uses differential operations to capture discontinuities.
    - **Example:** Detecting the outline of a building in a cityscape by finding rapid changes in pixel intensity.
- **Contour Detection:**
    
    - Considered a _mid-level vision task_ that involves grouping edges to form coherent boundaries.
    - Reflects how human vision synthesizes parts into a whole.
    - **Example:** Recognizing the outline of a face where multiple edges merge into a continuous contour.

### Challenges

- **Ambiguity:**
    - There is no single definition of an "edge" or "contour" since human sketches can vary.
    - Evaluation is difficult—should one use gradient peaks, color/texture discontinuities, or object boundaries?
- **Evaluation Metrics:**  
    Commonly, ground truth segmentations are used for evaluation.
    - **Precision:**  
        $$P=\frac{\text{True Positives}}{\text{True Positives} + \text{False Positives}}$$
    - **Recall:**  
        $$R=\frac{\text{True Positives}}{\text{True Positives} + \text{False Negatives}}$$
    - **F-Measure (F1 Score):** The harmonic mean of precision and recall.
    - **Average Precision (AP):** The area under the precision-recall curve.
- **Example:**  
    In a test image, if an edge detector correctly identifies 80 out of 100 actual edges (True Positives) but falsely marks 20 non-edges (False Positives) and misses 20 real edges (False Negatives), precision and recall metrics help quantify performance.

---

## 3. Traditional Edge Detection Methods

### First Order Derivative Methods

- **Concept:**  
    Uses 2D calculus to compute the gradient (i.e., first derivative) of image intensity.
    
- **Issues:**
    
    - **Noise Amplification:**  
        Differencing filters can enhance noise.
    - **Solution:**  
        Combine a **low-pass filter** (to suppress noise) with the derivative operation—a compound filter approach.
- **Example:**  
    Applying a Sobel filter (a type of first order derivative filter) on a noisy image may first require Gaussian smoothing to reduce noise effects.
    

### Second Order Derivative Methods

- **Concept:**  
    Involves computing the second derivative of the image.
    
- **Techniques:**
    
    - **Laplacian of Gaussian (LoG):**  
        This filter first smooths the image and then applies the Laplacian operator.
        - Also known as the **Mexican Hat filter** because of its shape.
- **Example:**  
    Using LoG on an image helps highlight regions where the intensity changes rapidly, useful for detecting fine details.
    

---

## 4. The Canny Edge Detector

### Overview

The Canny Edge Detector is a popular method that refines edge maps through post-processing steps.

### Main Steps

1. **Convolution with Derivative of Gaussian:**
    - Smooth the image with a Gaussian filter.
    - Compute the gradient to detect potential edges.
2. **Non-Maximum Suppression (NMS):**
    - Retain only the local maxima in the gradient magnitude image.
    - **Example:**  
        In a gradient image of a road sign, only the pixels corresponding to the strongest gradient along an edge are kept.
3. **Hysteresis Thresholding:**
    - Apply two thresholds:
        - **High threshold:** Pixels above this are considered strong edges.
        - **Low threshold:** Pixels below this are rejected.
        - Pixels between thresholds are classified as edges only if connected to strong edges.

- **Weaknesses:**
    - Sensitive to textured regions which might result in ambiguous detections.
    - Often used as a pre-processing step because it primarily relies on luminance gradients.

---

## 5. Learning-Based Edge and Contour Detection

### Problem Definition

- **Objective:**  
    Identify visually salient contours that delineate meaningful regions in an image.
    
- **Approach:**
    
    - Use ground truth data derived from human sketches.
    - Develop discriminative models that learn from local patches and global image properties.

### Local Feature-Based Methods

- **Probability of Boundary (Pb):**
    - A learning-based method that uses local features such as:
        - Brightness gradient
        - Texture gradient (using textons—responses from convolving with multiple filters)
        - Color gradient (often using channels like $a$, $b$ for chrominance and $L$ for luminance)
    - **Method:**
        - Compute oriented gradients using half-disk regions at various scales and orientations.
        - Compare histograms between paired half-disks to determine boundary probability.
- **Variants:**
    - **MS-Pb (Multi-Scale Pb):**  
        Incorporates outputs at various scales.
    - **gPb (Global Pb):**  
        Uses spectral clustering to integrate global image information.

### Learning with Random Forests

- **Rationale for Using Random Forests:**
    - A combination of decision trees that is computationally efficient.
    - Robust to feature normalization and overfitting due to tree diversity.
- **Methods:**
    - **Sketch Token:**  
        A random forest-based method that extracts edge confidence maps from image patches.
    - **Structured Edge (SE):**  
        Builds on the assumption that edges have inherent structure, leading to:
        - Faster computation
        - Higher accuracy compared to Sketch Token.
- **Example:**  
    In a real-time video processing application, Structured Edge detection may quickly provide reliable edge maps to help segment objects like pedestrians from the background.

---

## 6. Conclusion and Future Work

### Summary

- **Local learning-based detectors** have achieved significant progress.
- **Global information** is needed to further improve the accuracy and robustness of edge and contour detection.
- **Evaluation challenges** remain due to the subjective nature of human perception and dataset bias.

### Future Directions

- **Feature Enhancement:**  
    Develop more discriminative features that capture both local and global context.
- **Generative Models:**  
    Propose models that mimic human vision more closely, integrating both low-level cues and high-level interpretations.
- **Downstream Applications:**  
    Produce edge and contour results that are directly applicable to tasks such as object recognition and scene understanding.
