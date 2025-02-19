# Digital Images: Basics

- **Pixel Coordinate System:**  
  Most image processing systems use a coordinate system where the top-left pixel is designated as (1, 1). This standardization simplifies operations like cropping and filtering.

- **Bit Depth & Color Representation:**  
  - **RGB Images:** Each pixel is typically represented by three channels: Red, Green, and Blue. Often, each channel is stored using 8 bits, meaning each channel can take values from 0 to 255.
  - **Luminance & Chrominance:**  
    - **Luminance:** Represents brightness (the perceived intensity of the color).  
    - **Chrominance:** Represents color information, typically divided into two components, such as $C_b$ and $C_r$ in the YCbCr color space.
  - **Grayscale Images:**  
    These images use only one channel (usually the luminance channel) and have 8 bits per pixel. Here, $$0$$ corresponds to black, $$255$$ to white, and intermediate values represent various shades of gray.

---

# Image Signal Processors (ISP)

An ISP transforms raw camera sensor data into a viewable image using several digital image processing operations:

- **Demosaicing:**  
  Reconstructs a full-color image from the incomplete color samples (typically arranged in a Bayer filter pattern) captured by the sensor.
- **Histogram Equalization:**  
  Enhances contrast by redistributing the pixel intensity values.
- **Intensity & Contrast Adjustment:**  
  Fine-tunes brightness and contrast to improve the overall appearance of the image.
- **Smoothing & Sharpening:**  
  Smoothing reduces noise, while sharpening enhances edges and details.
- **The “3 A’s”:**  
  - **Auto Exposure (AE):** Adjusts the sensor’s exposure settings (shutter speed, aperture, ISO) to balance brightness.  
  - **Auto Focus (AF):** Utilizes specific focus points to ensure that the area of interest is sharp.  
  - **Auto White Balancing (AWB):** Corrects color casts to ensure white objects appear neutral under varying lighting conditions.

*(Lecture Date: 1/12/25)*

---

# Demosaicing Techniques

## Basic Demosaicing
- **Purpose:**  
  Since each sensor element records only one color, basic demosaicing reconstructs missing color values at every pixel.
- **Simple Approach – Bilinear Interpolation:**  
  - **Example:** For a red pixel, estimate the missing green value by averaging the surrounding green pixels. For red and blue, often a two-step process is used: first interpolate horizontally, then vertically.  
  - **For Green Pixels:** Use the four directly adjacent neighbors for interpolation.

## Advanced Demosaicing (MHC, Malvar-He-Cutler)
- **Concept:**  
  Improves upon simple bilinear interpolation by including correction terms.
- **How It Works:**  
  To estimate the green component at a red pixel location, the algorithm not only uses neighboring green values but also applies a correction computed from the red channel using a 5-point Laplacian.  
  - **Simplified Explanation:** Think of a red pixel whose missing green value needs to be estimated. Instead of merely averaging nearby green pixels, the algorithm also examines the surrounding red pixels to gauge local changes (using a Laplacian filter) and adjusts the green estimate accordingly.

---

# Contrast Enhancement & Histogram Equalization

## Contrast Enhancement in Grayscale Images
- **8-bit Grayscale Range:**  
  Pixel values range from $$0$$ (black) to $$255$$ (white).
- **Image Histogram:**  
  - **Low Brightness:** Most pixels are near $$0$$.  
  - **High Brightness:** Most pixels are near $$255$$.  
  - **Low Contrast:** Pixel values are concentrated in a narrow range.  
  - **High Contrast:** Pixel values are spread out over a wide range.

## Histogram Equalization
- **Purpose:**  
  Spreads out the pixel intensity values to enhance image contrast.
- **Application:**  
  Can be applied to both grayscale and color images (with adaptations to maintain natural color balance in color images).

---

# Auto Exposure, Autofocus, and Color Correction

- **Auto Exposure (AE):**  
  Automatically adjusts camera settings (such as shutter speed, aperture, and ISO) to achieve balanced exposure.
- **Autofocus (AF):**  
  Uses designated focus points to ensure that the subject or area of interest is in sharp focus.
- **Auto White Balancing (AWB):**  
  - **Methods:**  
    - **Max RGB:** Assumes the highest values in each color channel should be equal.  
    - **Gray World Assumption:** Assumes the average color of a scene is gray.
  - **Advanced Techniques:** Incorporate methods like gamut constraints or neural networks to improve color accuracy.

---

# Image Filtering

- **Definition:**  
  An image filter is typically defined by an $$ n \times n $$ array (or kernel) where each number represents a weight coefficient applied to the corresponding pixel and its neighbors during convolution.
- **Examples:**
  - **Low-Pass Filters:** Smooth the image by averaging nearby pixel values (e.g., Gaussian blur).
  - **High-Pass Filters:** Emphasize edges by highlighting rapid intensity changes (e.g., sharpening filters).
  - **Edge Sharpening:** Combines high-pass filtering with the original image to enhance details.

---

# Image Denoising

## Noise Types
- **Additive Noise:**  
  - **Additive White Gaussian Noise (AWGN):**  
    - **Characteristics:** Noise is "white" (affecting all frequencies uniformly) and follows a Gaussian distribution.
- **Impulse Noise (Salt & Pepper Noise):**  
  - **Salt Noise:** White spots caused by sensor saturation.  
  - **Pepper Noise:** Black spots caused by dead sensor pixels.
- **Mixed Noise:** A combination of both additive noise and impulse noise.

## Removal Techniques

### Salt & Pepper Noise
- **Method:**  
  Outlier detection and removal, commonly using **median filtering**.
- **Median Filtering:**  
  Sorts the neighboring pixel values and replaces the center pixel with the median value.  
  - **Example:** In a $$3 \times 3$$ window with values $$[12, 15, 14, 16, 200, 15, 13, 14, 15]$$ (with $$200$$ being an outlier), the median value (15) replaces the central pixel.

### Additive White Gaussian Noise
- **Gaussian Smoothing:**
  - **Idea:**  
    Since most image content is low frequency (smooth), while noise is high frequency, a Gaussian low-pass filter can suppress noise.  
  - **Gaussian Filter:**  
    Uses a Gaussian kernel where pixels closer to the center have higher weights.
- **Bilateral Filtering:**  
  - **Concept:**  
    A non-linear, edge-preserving filter that considers both spatial proximity and intensity similarity.  
  - **Example:**  
    When smoothing a portrait, the bilateral filter reduces noise in skin areas while preserving sharp features like the eyes and lips.

### Advanced Denoising Methods

#### Non-Local Means (NLM) Algorithm
- **Concept:**  
  Instead of solely using a local neighborhood, NLM denoises by averaging pixels with similar patterns found throughout the image.
- **Mathematical Representation:**  
  $$ x = s + n $$  
  where $x$ is the noisy signal, $s$ is the original image, and $$n$$ is the noise.
- **Example:**  
  For a given pixel in a textured area, similar patterns might be found in other parts of the image. NLM assigns weights to these pixels based on similarity and averages them to reduce noise.

#### Block Matching 3D (BM3D)
- **Process:**
  1. **Block Matching:**  
     Identify and group similar blocks (small patches) across the image.
  2. **Collaborative Filtering:**  
     Stack these similar blocks into a 3D array and apply transform-domain filtering.
- **Filtering Steps:**  
  - **Collaborative Hard Thresholding:** Zero out coefficients below a certain threshold.
  - **Collaborative Wiener Filtering:** Refine the estimate by weighing coefficients based on their signal-to-noise ratio.
- **Example:**  
  In an image with repetitive textures (like bricks), BM3D identifies similar brick patterns, stacks them, and denoises the group—preserving details while reducing noise.

---

# Adaptive Denoising Techniques

## Adaptive Non-Local Means
- **Idea:**  
  Adjust denoising parameters based on local image content to better exploit self-similarity.
- **Benefits:**  
  More effective noise reduction in smooth regions and better detail preservation in textured areas.

## Block Classification & Adaptive Block Matching
- **Block Classification:**  
  Determines the type or texture of each image block, allowing for tailored denoising approaches.
- **Adaptive Block Matching:**  
  Modifies the denoising parameters based on block type, improving the accuracy of finding similar blocks.

## Dominant Orientation Alignment
- **Concept:**  
  Rotates candidate blocks so their dominant orientations align with that of the target block.
- **Benefit:**  
  Enhances the similarity matching process by accounting for rotated patterns.

## Adaptive Matching Window
- **Function:**  
  Adjusts the size of the matching window based on the local structure.
- **Outcome:**  
  Captures more relevant local features, leading to improved block matching and more effective denoising.

