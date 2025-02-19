# Digital Images
- **Pixel Coordinates:**
  - (1,1) is at the top left.
- **Color Representation:**
  - RGB model with 8 bits per pixel.
- **Luminance:**
  - Represents brightness.
  - Often derived from the green channel.
- **Chrominance:**
  - Contains color difference information (Cb and Cr channels).
- **Grayscale Images:**
  - Use the luminance channel.
  - 8 bits per pixel with values from 0 (black) to 255 (white).

# Image Signal Processors (ISP)
- **Purpose:**
  - Convert camera sensor data into processed images.
- **Key Operations:**
  - **Demosaicing**
  - **Histogram Equalization**
  - **Intensity & Contrast Adjustment**
  - **Smoothing & Sharpening**
  - **3 A’s:**
    - Auto Exposure (AE)
    - Auto Focus (AF)
    - Auto White Balancing (AWB)

# Demosaicing
- **Basic Demosaicing:**
  - Reconstructs missing color values at sensor positions.
  - **Simple Method:** Bilinear interpolation.
    - For red/blue: Use horizontal then vertical interpolation.
    - For green: Use 4 neighboring pixels.
- **Advanced Demosaicing (MHC - Malvar, He, Cutler):**
  - Uses correct terms and a 5-point Laplacian for refinement.
  - Example: Estimating the green component at a red pixel with better accuracy.

# Contrast Enhancement & Histograms
- **Contrast in 8-Bit Grayscale Images:**
  - Pixel values range from 0 (black) to 255 (white).
  - **Low Contrast:** Pixel values are clustered together.
  - **High Contrast:** Pixel values are widely spread.
- **Image Histograms:**
  - **Low Brightness:** Most pixels near 0.
  - **High Brightness:** Most pixels near 255.
- **Histogram Equalization:**
  - Spreads out pixel values to enhance contrast.
  - Can be applied to color histograms for improved color representation.

# Auto Exposure, Auto Focus, & Auto White Balancing
- **Auto Exposure (AE):**
  - Adjusts image brightness for correct exposure.
- **Auto Focus (AF):**
  - Uses autofocus points to determine optimal focus.
- **Auto White Balancing (AWB):**
  - Corrects color casts.
  - **Algorithms:**
    - Max RGB
    - Gray World
    - Advanced methods using gamut constraints and neural networks.

# Image Filters
- **Definition:**
  - An n×n array (kernel) where each number is a weight coefficient applied to covered pixels.
- **Examples:**
  - **Low Pass Filters:** Smooth image by reducing high-frequency noise.
  - **High Pass Filters:** Enhance edges.
  - **Edge Sharpening:** Emphasizes details.

# Image Denoising
- **Noise Types:**
  - **Additive Noise:**
    - Additive White Gaussian Noise (AWGN): White and Gaussian in nature.
  - **Impulse Noise (Salt and Pepper):**
    - Salt (white): Caused by sensor saturation.
    - Pepper (black): Caused by dead sensor pixels.
  - **Mixed Noise:** Combination of both types.
  
- **Denoising Techniques:**
  - **Salt & Pepper Removal:**
    - Use outlier detection.
    - **Median Filtering:** Rank-ordering pixel values and selecting the median.
  - **AWGN Removal:**
    - **Gaussian Smoothing:**
      - Applies a Gaussian weighted low pass filter.
      - Reduces high-frequency noise (with potential blurring of edges).
    - **Bilateral Filtering:**
      - Considers both spatial and intensity distances.
    - **Non-Local Means (NLM) Algorithm:**
      - Denoises by averaging similar patches across the image.
      - Basic model: _x = s + n_ (noisy signal = original signal + noise).
    - **Block Matching 3D (BM3D):**
      - **Process:**
        - Find similar blocks to a reference block.
        - Stack them into a 3D array.
        - Perform collaborative filtering.
      - **Collaborative Filtering Steps:**
        - Hard Thresholding.
        - Wiener Filtering.
      - Note: Steps 1 and 2 differ in their filtering approach.

# Advanced Denoising Techniques
- **Adaptive Non-Local Means Algorithm:**
  - Adjusts denoising parameters based on local image content.
  - Enhances the similarity matching process.
- **Block Classification:**
  - Classifies local blocks to apply selective denoising approaches.
- **Adaptive Block Matching:**
  - Adjusts denoising parameters based on block type.
  - Improves similarity matching accuracy.
- **Dominant Orientation Alignment:**
  - Aligns rotated blocks with the dominant orientation of the target block.
- **Adaptive Matching Window:**
  - Adjusts the size of the matching window to better capture local structures.
