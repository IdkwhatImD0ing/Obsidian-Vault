# Digital Images: Basics

- **Pixel Coordinate System:**  
    Most image processing systems use a coordinate system where the top-left pixel is designated as (1, 1). This helps standardize operations such as cropping and filtering.
    
- **Bit Depth & Color Representation:**
    
    - **RGB Images:** Each pixel is typically represented by three channels: Red, Green, and Blue. In many cases, each channel is stored using 8 bits, meaning each channel can take values from 0 to 255.
    - **Luminance & Chrominance:**
        - **Luminance:** Represents brightness and is often correlated with the perceived intensity of the color.
        - **Chrominance:** Represents color information, often split into two components (Cb and Cr) in color spaces like YCbCr.
    - **Grayscale Images:**  
        These images use only one channel (usually the luminance channel) and have 8 bits per pixel. Here, 0 corresponds to black, 255 to white, and values in between represent varying shades of gray.

---

# Image Signal Processors (ISP)

An ISP transforms raw camera sensor data into a viewable image using a series of digital image processing operations:

- **Demosaicing:** Reconstructs a full-color image from the incomplete color samples output by an image sensor (usually with a Bayer filter pattern).
- **Histogram Equalization:** Enhances contrast by spreading out the most frequent intensity values.
- **Intensity & Contrast Adjustment:** Fine-tunes the brightness and contrast to improve image appearance.
- **Smoothing & Sharpening:** Reduces noise and enhances edges, respectively.
- **The “3 A’s”:**
    - **Auto Exposure (AE):** Adjusts the sensor’s exposure settings to ensure the image isn’t too dark or too bright.
    - **Auto Focus (AF):** Determines and maintains the sharp focus of the image, often using dedicated focus points.
    - **Auto White Balancing (AWB):** Corrects color casts so that white appears neutral under varying lighting conditions.

_(Lecture Date: 1/12/25)_

---

# Demosaicing Techniques

## Basic Demosaicing

- **Purpose:**  
    The goal is to reconstruct missing color values at each pixel location since each sensor element only records one color.
- **Simple Approach – Bilinear Interpolation:**
    - **Example:** For a red pixel, estimate missing green values using surrounding green pixels. For red and blue, often use a two-step process: first interpolate horizontally, then vertically.
    - **For Green Pixels:** Typically, use the four directly adjacent neighbors.

## Advanced Demosaicing (MHC, Malvar-He-Cutler)

- **Concept:**  
    Improves upon simple bilinear interpolation by incorporating correction terms.
- **How It Works:**  
    To estimate, for example, the green component at a red pixel location, the algorithm uses not just the neighboring green values but also a correction computed from the red channel using a 5-point Laplacian.
    - **Simplified Explanation:** Imagine you have a red pixel and you need to guess what the missing green value should be. Instead of just averaging nearby greens, you also check the red values around it, calculate how “sharp” the red information is (using a Laplacian filter), and then adjust your green estimate accordingly.

---

# Contrast Enhancement & Histogram Equalization

## Contrast Enhancement in Grayscale Images

- **8-bit Grayscale Range:** 0 (black) to 255 (white).
- **Image Histogram:**
    - **Low Brightness:** Most pixels are near 0.
    - **High Brightness:** Most pixels are near 255.
    - **Low Contrast:** Pixel values are concentrated in a narrow range.
    - **High Contrast:** Pixel values are spread out over a wide range.

## Histogram Equalization

- **Purpose:**  
    Spreads out the pixel intensity values, enhancing contrast.
- **Application:**  
    Can be applied to both grayscale and color images (with adaptations for color images to maintain natural color balance).

---

# Auto Exposure, Autofocus, and Color Correction

- **Auto Exposure (AE):** Automatically adjusts the camera settings (shutter speed, aperture, ISO) to ensure the image has a balanced exposure.
- **Autofocus (AF):** Uses specific focus points within the image to ensure that the area of interest is sharp.
- **Auto White Balancing (AWB):**
    - **Methods:**
        - **Max RGB:** Assumes the highest values in each channel should be equal.
        - **Gray World Assumption:** Assumes that the average color of a scene is gray.
    - **Advanced Techniques:** Include using gamut constraints or neural networks to improve color accuracy.

---

# Image Filtering

- **Definition:**  
    An image filter is an n×nn \times n array (or kernel) where each number represents a weight that is applied to the corresponding pixel and its neighbors during convolution.
- **Examples:**
    - **Low-Pass Filters:** Smooth the image by averaging pixel values (e.g., Gaussian blur).
    - **High-Pass Filters:** Enhance edges by emphasizing rapid intensity changes (e.g., sharpening filters).
    - **Edge Sharpening:** Combines high-pass filtering with the original image to accentuate details.

---

# Image Denoising

## Noise Types

- **Additive Noise:**
    - **Additive White Gaussian Noise (AWGN):**
        - **Characteristics:** “White” (uniform across frequencies) and follows a Gaussian distribution.
- **Impulse Noise (Salt & Pepper Noise):**
    - **Salt Noise:** White spots caused by sensor saturation.
    - **Pepper Noise:** Black spots due to dead sensor pixels.
- **Mixed Noise:** A combination of both types.

## Removal Techniques

### Salt & Pepper Noise

- **Method:**  
    Outlier detection and removal, often using **median filtering**.
- **Median Filtering:**  
    Sorts the neighboring pixel values and replaces the center pixel with the median value.
    - **Example:** In a 3×3 window, if the values are [12, 15, 14, 16, 200, 15, 13, 14, 15] (with 200 being an outlier), the median (15) replaces the central pixel.

### Additive White Gaussian Noise

- **Gaussian Smoothing:**
    - **Idea:**  
        Most images have low-frequency content (smooth variations), while noise is high-frequency. A Gaussian low-pass filter suppresses noise but may also blur edges.
    - **Gaussian Filter:**  
        Uses a Gaussian kernel where pixels closer to the center have higher weight.
- **Bilateral Filtering:**
    - **Concept:**  
        A non-linear, edge-preserving filter that combines spatial proximity and intensity similarity.
    - **Example:**  
        When smoothing a portrait, the bilateral filter reduces noise in the skin areas while preserving the sharpness of the eyes and lips.

### Advanced Denoising Methods

#### Non-Local Means (NLM) Algorithm

- **Concept:**  
    Instead of only considering the local neighborhood, NLM denoises by averaging pixels with similar patterns found throughout the image.
- **Mathematical Representation:** x=s+nx = s + n where xx is the noisy signal, ss is the original image, and nn is the noise.
- **Example:**  
    For a given pixel in a textured area, similar patterns may be found in other parts of the image. NLM assigns weights to these pixels based on similarity and averages them to reduce noise.

#### Block Matching 3D (BM3D)

- **Process:**
    1. **Block Matching:**  
        Identify and group similar blocks (small patches) from across the image.
    2. **Collaborative Filtering:**  
        Stack these similar blocks into a 3D array and apply transform-domain filtering.
- **Filtering Steps:**
    - **Collaborative Hard Thresholding:** Zero out coefficients below a certain threshold.
    - **Collaborative Wiener Filtering:** Refine the estimate by weighing coefficients based on their estimated signal-to-noise ratio.
- **Example:**  
    When processing an image with repetitive textures (like bricks), BM3D finds similar brick patterns, stacks them, and denoises the group, thereby preserving detail while reducing noise.

---

# Adaptive Denoising Techniques

## Adaptive Non-Local Means

- **Idea:**  
    Adjust denoising parameters based on local image content to fully exploit self-similarity.
- **Benefits:**  
    Better noise reduction in smooth areas and better preservation of details in textured regions.

## Block Classification & Adaptive Block Matching

- **Block Classification:**  
    Determine the type (or texture) of each image block so that tailored denoising methods can be applied.
- **Adaptive Block Matching:**  
    Modify the denoising parameters based on the block type, improving the accuracy of finding similar blocks.

## Dominant Orientation Alignment

- **Concept:**  
    Rotate candidate blocks so that their dominant orientations align with the target block.
- **Benefit:**  
    Improves the similarity matching process by accounting for rotated patterns.

## Adaptive Matching Window

- **Function:**  
    Adjusts the size of the matching window based on local structure.
- **Outcome:**  
    Captures more relevant local features, leading to better block matching and more effective denoising.
