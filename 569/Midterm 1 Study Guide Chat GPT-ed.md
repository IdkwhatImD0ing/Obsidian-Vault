## 1. Demosaicing Techniques

When capturing color images, each sensor element (pixel) records only one color. Demosaicing is the process of reconstructing the missing color channels at each pixel location.

### 1.1 Basic Demosaicing

- **Purpose:**  
  Each pixel in a color filter array (like the Bayer pattern) captures one color (red, green, or blue). The goal is to estimate the missing two color values for every pixel to reconstruct the full-color image.

- **Bilinear Interpolation Approach:**  
  - **Method:**  
    The simplest approach estimates missing values by averaging the values of nearby pixels of the same color.
  - **Example:**  
    - For a **red pixel**, the missing green value is computed by averaging the surrounding green pixels.  
    - For red and blue channels, often a two-step process is used: first interpolate horizontally and then vertically.
  - **For Green Pixels:**  
    Use the four directly adjacent (up, down, left, right) neighbors to interpolate missing red and blue values.

### 1.2 Advanced Demosaicing (MHC, Malvar-He-Cutler)

- **Concept:**  
  This method enhances simple bilinear interpolation by incorporating correction terms to reduce artifacts.
  
- **How It Works:**  
  - **Correction Terms:**  
    To estimate, for example, the green component at a red pixel, the algorithm not only averages the nearby green pixels but also applies a correction computed from the red channel using a 5-point Laplacian operator.
  - **Simplified Explanation:**  
    Imagine a red pixel missing its green value. Instead of simply averaging, the algorithm assesses the local changes in intensity (using a Laplacian filter on the red channel) and adjusts the green estimate accordingly. This often leads to improved color accuracy and reduced artifacts.

---

## 2. Denoising Methods

Image denoising aims to reduce noise while preserving important image details. Several methods are compared below.

### 2.1 Median vs. Gaussian Denoising

- **Median Denoising:**  
  - **Method:**  
    Each pixel is replaced by the median value of its neighborhood.
  - **Example:**  
    Best suited for removing salt-and-pepper noise because it effectively eliminates outlier values without blurring edges.

- **Gaussian Denoising:**  
  - **Method:**  
    Convolve the image with a Gaussian kernel to average pixel values based on a Gaussian weight.
  - **Example:**  
    Useful for removing random noise, but can blur fine details if the kernel size is too large.

### 2.2 Bilateral Filtering

- **Concept:**  
  Each pixel’s new value is computed as a weighted average of its neighbors. The weight is the product of two Gaussian functions:
  - One **depends on spatial distance**.
  - One **depends on intensity (or color) difference**.
  
- **Key Parameters:**
  1. **Filter Size:**  
     - Determines the window (or kernel) size over which the filter is applied.
     - **Effect:** A larger filter size increases smoothing and computational cost.
  2. **os (Spatial Sigma, $\sigma_s$):**  
     - Controls how quickly the spatial weight falls off with distance.
     - **Effect:**  
       - **Larger $\sigma_s$:** More distant pixels contribute significantly (smoother output).  
       - **Smaller $\sigma_s$:** Only nearby pixels influence the result (preserves details).
  3. **oc (Range/Color Sigma, $\sigma_r$ or $\sigma_{color}$):**  
     - Controls sensitivity to intensity differences.
     - **Effect:**  
       - **Larger $\sigma_r$:** Less sensitive to intensity differences, resulting in stronger smoothing even across edges.  
       - **Smaller $\sigma_r$:** More selective, preserving edges by considering only pixels with similar intensities.

### 2.3 Non-Local Means (NL Means) Denoising

- **Concept:**  
  NL Means denoising leverages the idea that similar image patches (even if spatially far apart) can be used to denoise each other.
- **How It Works:**  
  - For a target patch, search for similar patches within a larger window.
  - Compute a weighted average of these patches, where weights are based on similarity.
- **Example:**  
  In a textured area of an image, NL Means will average similar textures from different regions, reducing noise without overly blurring the texture.

### 2.4 CLAHE Denoising (Contrast Limited Adaptive Histogram Equalization)

- **Concept:**  
  Although primarily used for contrast enhancement, CLAHE can help in reducing noise in low-contrast areas by equalizing local regions of the image.
- **How It Works:**  
  - Divides the image into small blocks.
  - Applies histogram equalization locally, but limits contrast amplification to avoid noise over-enhancement.
- **Example:**  
  In medical imaging, CLAHE can enhance subtle details in regions with low contrast while mitigating the risk of noise amplification.

### 2.5 Peak Signal-to-Noise Ratio (PSNR)

- **Definition:**  
  PSNR is a metric used to measure the quality of a denoised image relative to the original.
- **Formula:**  
  $$
  \text{PSNR} = 10 \cdot \log_{10} \left(\frac{MAX_I^2}{\text{MSE}}\right)
  $$
  where:
  - $MAX_I$ is the maximum possible pixel value (e.g., 255 for 8-bit images).
  - $\text{MSE}$ (Mean Squared Error) is computed as:
    $$
    \text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
    $$
- **Example:**  
  A higher PSNR value indicates better image quality and less error between the denoised image and the original.

---

## 3. Histogram Equalization & Transfer Functions

### 3.1 Histogram Equalization: Bucket Filling vs. Transfer Function-Based Methods

- **Bucket Filling Approach:**  
  - **Method:**  
    Adjusts the histogram by redistributing pixel intensities so that they are more evenly spread out over the available range.
  - **Effect:**  
    Enhances the overall contrast by "filling buckets" more uniformly, but might not provide fine control over specific intensity mappings.

- **Transfer Function-Based Method:**  
  - **Method:**  
    Uses a predefined or adaptive transfer function $s = T(r)$, where $r$ is the original intensity and $s$ is the transformed intensity.
  - **Graphical Interpretation:**  
    - **Identity Mapping:**  
      A straight diagonal line ($s = r$) indicates no change.
    - **Contrast Stretching:**  
      A graph steeper than the identity line in certain regions amplifies differences, increasing contrast.
    - **Compression:**  
      A less steep graph compresses the range of intensities, reducing contrast.
  - **Example:**  
    In an image with a narrow intensity range (low contrast), applying a transfer function that stretches mid-tone values can reveal hidden details and improve visibility.

### 3.2 Transfer Functions in Detail

- **Definition:**  
  A transfer function maps each input pixel intensity $r$ to an output intensity $s$.
- **Formula:**  
  $$
  s = T(r)
  $$
- **Example Graphs:**  
  - **Steeper than Diagonal:**  
    Amplifies intensity differences (enhances contrast).  
  - **Flatter than Diagonal:**  
    Compresses the intensity range (reduces contrast).

---

## 4. Edge Detection

Edge detection identifies significant intensity changes, which typically correspond to object boundaries.

### 4.1 Sobel Edge Detection

- **Concept:**  
  Uses gradient operators (Sobel kernels) to approximate the first derivative (gradient) of the image intensity.
- **Sobel Kernels:**
  - **Horizontal Gradient ($G_x$):**  
    $$
    G_x = \begin{bmatrix}
    -1 & 0 & +1 \\
    -2 & 0 & +2 \\
    -1 & 0 & +1 \\
    \end{bmatrix}
    $$
  - **Vertical Gradient ($G_y$):**  
    $$
    G_y = \begin{bmatrix}
    -1 & -2 & -1 \\
     0 &  0 &  0 \\
    +1 & +2 & +1 \\
    \end{bmatrix}
    $$

- **Example Calculation:**

  **Given 5×5 image:**
  $$
  \begin{array}{ccccc}
  11 & 19 & 17 & 1  & 22 \\
  2  & 2  & 7  & 4  & 23 \\
  7  & 8  & 6  & 12 & 7  \\
  5  & 10 & 22 & 10 & 10 \\
  27 & 12 & 10 & 17 & 12 \\
  \end{array}
  $$

  - **Central Pixel:** Located at row 3, column 3 (value 6).
  - **Extracted 3×3 Neighborhood (rows 2–4, columns 2–4):**
    $$
    \begin{array}{ccc}
    2 & 7 & 4 \\
    8 & 6 & 12 \\
    10 & 22 & 10 \\
    \end{array}
    $$

  **Step 1: Compute $G_x$**

  Multiply the corresponding elements of the $G_x$ kernel with the patch:
  $$
  \begin{array}{ccc}
  -1\cdot2 & 0\cdot7 & +1\cdot4 \\
  -2\cdot8 & 0\cdot6 & +2\cdot12 \\
  -1\cdot10 & 0\cdot22 & +1\cdot10 \\
  \end{array}
  $$
  - First row: $-2 + 0 + 4 = 2$  
  - Second row: $-16 + 0 + 24 = 8$  
  - Third row: $-10 + 0 + 10 = 0$  

  **Sum:**  
  $$
  G_x = 2 + 8 + 0 = 10.
  $$

  **Step 2: Compute $G_y$**

  Multiply the $G_y$ kernel with the patch:
  $$
  \begin{array}{ccc}
  -1\cdot2 & -2\cdot7 & -1\cdot4 \\
  0\cdot8  &  0\cdot6 &  0\cdot12 \\
  +1\cdot10 & +2\cdot22 & +1\cdot10 \\
  \end{array}
  $$
  - First row: $-2 - 14 - 4 = -20$  
  - Second row: $0$  
  - Third row: $10 + 44 + 10 = 64$  

  **Sum:**  
  $$
  G_y = -20 + 0 + 64 = 44.
  $$

  **Step 3: Compute Gradient Magnitude**

  $$
  |G| = \sqrt{G_x^2 + G_y^2} = \sqrt{10^2 + 44^2} = \sqrt{100 + 1936} = \sqrt{2036}.
  $$
  Alternatively, express as:
  $$
  |G| = 2\sqrt{509}.
  $$

- **Drawback of the Sobel Detector:**  
  It is sensitive to noise. **Solution:** Pre-smooth the image with a Gaussian filter:
  $$
  I_s = I * G,
  $$
  where $G$ is a Gaussian kernel, and then apply the Sobel operator to $I_s$.

### 4.2 Canny Edge Detection

- **Overview:**  
  The Canny detector is a multi-step algorithm designed to produce clean, well-localized edges.

- **Steps:**
  1. **Noise Reduction:**  
     Apply a Gaussian filter to smooth the image.
  2. **Gradient Computation:**  
     Compute the gradient magnitude and direction (often using operators similar to Sobel).
  3. **Non-Maximum Suppression (NMS):**  
     Thin the edges by retaining only the local maxima along the gradient direction.
  4. **Double Thresholding:**  
     Apply a high and a low threshold:
     - **Strong Edges:** Pixels with gradient values above the high threshold.
     - **Weak Edges:** Pixels with gradient values between the two thresholds.
  5. **Edge Tracking by Hysteresis:**  
     Weak edges connected to strong edges are preserved; isolated weak responses are discarded.

- **Why Canny Performs Better than Sobel:**
  - **Noise Reduction:** Gaussian smoothing minimizes noise before gradient computation.
  - **Edge Localization:** NMS produces thin, one-pixel-wide edges.
  - **Robust Thresholding:** The double threshold and hysteresis steps help distinguish true edges from noise.
  - **Overall Accuracy:** Results in clean, continuous, and well-localized edges compared to the thicker, noisier output from the Sobel operator.

- **Double Threshold Importance:**  
  It prevents isolated noisy responses from being marked as edges. Only weak edges connected to strong edges are considered valid, ensuring that the final edge map is both accurate and reliable.

- **Comparative Edge Map Appearances:**
  1. **Sobel with Single Thresholding:**  
     - Thick, rough edges with potential noise.
  2. **Canny Edge Detector:**  
     - Thin, crisp, and continuous edges.
  3. **Structured Edge Detector (with NMS and thresholding):**  
     - Very clean and semantically aligned with object boundaries.
  4. **Structured Edge Detector (without NMS):**  
     - Thicker, more diffuse edge responses.

---

## 5. Digital Halftoning

Digital halftoning simulates continuous-tone images on devices (like printers or certain displays) that can only render a limited number of tones (often binary or a few discrete levels).

### 5.1 Purpose and Error Diffusion

- **Digital Halftoning:**  
  Converts a continuous-tone image into a pattern of discrete dots that gives the illusion of varying shades and gradients.

- **Error Diffusion Method:**  
  - **Purpose:**  
    Distribute the quantization error from each pixel to its neighboring, unprocessed pixels.  
  - **Requirements for a Good Scanning Pattern:**
    - **Avoid Directional Bias:**  
      Errors should be spread uniformly.
    - **Minimize Error Clustering:**  
      Use scanning patterns such as:
      - **Serpentine (zig-zag) scanning**
      - **Hilbert curve scanning**
      - **Spiral scanning**

- **MBVQ-Based Color Diffusion:**  
  - **Concept:**  
    Instead of processing each color channel independently, the MBVQ (Minimum Brightness Vector Quantization) method considers the correlation among color channels.
  - **Advantage:**  
    Improved color fidelity and fewer artifacts, since it selects candidate vertices in the color space that best represent the original color.

### 5.2 Bayer Dithering

Bayer dithering is a method that uses a threshold matrix (Bayer matrix) to convert a continuous-tone image into a binary (halftoned) image.

#### 5.2.1 Bayer Dithering Formula

- **Threshold Calculation:**
  $$
  T(x,y) = \frac{I_n(x,y) + 0.5}{N^2} \times 255,
  $$
  where:
  - $I_n(x,y)$ is the value from an $N \times N$ Bayer index matrix.
  - $N^2$ is the total number of elements (e.g., $16$ for a $4 \times 4$ matrix).
  - Multiplication by $255$ scales the threshold to the image intensity range (0–255).

#### 5.2.2 Generating the Bayer Matrix

1. **Start with a Base 2×2 Bayer Matrix:**
   $$
   I_2 = \begin{pmatrix}
   1 & 2 \\
   3 & 0 \\
   \end{pmatrix}.
   $$
2. **Recursive Construction:**  
   Using the formula:
   $$
   I_{2n}(x,y) = 4 \times I_n(x,y) + \text{offset},
   $$
   where the offset depends on the quadrant, one possible $4 \times 4$ Bayer matrix is:
   $$
   I_4 = \begin{pmatrix}
   5 & 9 & 6 & 10 \\
   13 & 1 & 14 & 2 \\
   7 & 11 & 4 & 8 \\
   15 & 3 & 12 & 0 \\
   \end{pmatrix}.
   $$

#### 5.2.3 Applying Bayer Dithering

- **Process:**
  1. Divide the image (e.g., an 8×8 image) into blocks matching the Bayer matrix size.
  2. For each pixel, obtain its corresponding threshold from the tiled threshold matrix $T(x,y)$.
  3. Compare the pixel’s intensity with $T(x,y)$:
     - If the pixel value is greater than $T(x,y)$, output white (255).
     - Otherwise, output black (0).

- **Effect on Different Tone Regions:**
  - **Mid-tone Regions (e.g., intensity ≈ 125):**  
    A mix of black and white pixels simulates medium gray.
  - **Dark Regions (e.g., intensity ≈ 25):**  
    Most pixels fall below the threshold, resulting in predominantly black.
  - **Light Regions (e.g., intensity ≈ 225):**  
    Most pixels exceed the threshold, resulting in predominantly white.

#### 5.2.4 Expected Output Comparisons

When applying various halftoning methods (as seen in experiments on the Tower image), you might observe:

1. **Fixed Thresholding:**
   - **Appearance:**  
     Large uniform regions rendered completely black or white with abrupt transitions. Subtle tonal variations are lost.
2. **Random Thresholding:**
   - **Appearance:**  
     Noisy, grainy patterns with broken smooth transitions due to random threshold perturbations.
3. **Stucki Error Diffusion with Serpentine Scanning:**
   - **Appearance:**  
     Fine detail and smooth tonal transitions. Edges and textures are well preserved with only slight directional artifacts.
4. **Dithering with Bayer’s Matrix $I_2$:**
   - **Appearance:**  
     A coarse, repeating pattern (checkerboard-like) that is very noticeable.
5. **Dithering with Bayer’s Matrix $I_{32}$:**
   - **Appearance:**  
     A smoother, less obvious periodic pattern with a gradual dot density variation, yielding a more visually pleasing halftone.
