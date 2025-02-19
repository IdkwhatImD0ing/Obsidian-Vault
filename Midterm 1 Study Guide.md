z`Demosaicing Techniques

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



Denoising
Compare median and gaussian denoising, and bilateral filter
Expand on Nln Local Means denoising
Also clahe denoising

Also mention PSNR and its formula

In bilateral filtering, each pixel’s new value is computed as a weighted average of its neighbors, where the weight is the product of two Gaussian functions—one that depends on spatial distance and one that depends on intensity (or color) difference. The key parameters that control this behavior are:

1. **Filter Size:**
    
    - This is the size of the window (or kernel) over which the bilateral filter is applied.
    - **Effect:** A larger filter size means that more neighboring pixels are considered during filtering. This can result in more smoothing overall, but it also increases computational cost. If the filter size is too small relative to the spatial Gaussian (os), you might not capture the full extent of the intended spatial smoothing.
2. **os (Spatial Sigma):**
    
    - This parameter (often denoted as σₛ) controls the spatial component of the Gaussian weight.
    - **Effect:**
        - A **larger os** causes the spatial Gaussian to fall off more slowly with distance, meaning that pixels further away from the center will still have a significant influence. This can lead to a smoother output over a broader region.
        - A **smaller os** means that only pixels very near the center contribute significantly, preserving more fine spatial details.
3. **oc (Range or Color Sigma):**
    
    - This parameter (often denoted as σᵣ or σ_color) controls the range (or intensity/color) component of the Gaussian weight.
    - **Effect:**
        - A **larger oc** makes the filter less sensitive to intensity differences, so even pixels with different brightness or color can contribute to the average. This typically results in stronger smoothing, even across edges, which can diminish edge sharpness.
        - A **smaller oc** makes the filter very selective about which pixels are considered similar in intensity. This preserves edges because only pixels with very similar values contribute, but it may also leave some noise unsmoothed within homogeneous regions.

**Summary:**

- **Filter size** determines how many pixels are considered.
- **os** controls how the spatial distance between pixels affects their contribution.
- **oc** determines how much difference in intensity or color is tolerated before a neighbor’s contribution is significantly downweighted.

Explain the differences between histogram equalization for bucket filling and transfer functio nbased method


Transfer functions:
A **transfer function** in image processing is a mapping that specifies how each input pixel intensity is transformed into an output intensity. You can think of it as a function s=T(r)s = T(r)s=T(r), where rrr is the original intensity and sss is the new intensity after processing.

### How the Graph Affects the Result Image

The graph of the transfer function is plotted with the input intensity (usually on the horizontal axis) and the output intensity (on the vertical axis). The shape of this graph tells you exactly how intensities are remapped:

- **Identity Mapping:**  
    A straight diagonal line from the bottom left (0,0) to the top right (255,255) indicates that each intensity is mapped to itself. The output image will be identical to the input image—no change in brightness or contrast.
    
- **Contrast Stretching:**  
    If the graph is steeper than the identity line in certain regions, it amplifies differences in those intensity ranges, thus increasing contrast.
    
- **Compression:**  
    A graph that is less steep compresses the range of intensities, reducing contrast.

Edge Detection
DEfine canny and sobel edge detectin, how do I calculate sobel?
The **Canny edge detector** is designed to extract clean and well-localized edges from an image, and its major steps are as follows:

1. **Noise Reduction:**  
    A Gaussian filter is applied to the image to smooth out noise. This step is crucial because noise can lead to false edge detection.
    
2. **Gradient Computation:**  
    The smoothed image is then filtered with gradient operators (often similar to Sobel operators) to compute the gradient magnitude and direction at each pixel. This tells you how strong an edge is and its orientation.
    
3. **Non-Maximum Suppression:**  
    This step thins out the edges by keeping only the local maxima in the gradient direction. In other words, if a pixel’s gradient magnitude is not the highest compared to its neighbors along the gradient direction, it is suppressed (set to zero).
    
4. **Double Thresholding:**  
    Two thresholds (a high and a low) are applied to classify pixels as strong, weak, or non-relevant edges. Strong edges are those above the high threshold, and weak edges are those between the high and low thresholds.
    
5. **Edge Tracking by Hysteresis:**  
    Finally, weak edge pixels are considered true edges only if they are connected to strong edge pixels. This helps in preserving real edges while discarding isolated noise responses.
### Why Canny Performs Better than the Sobel Edge Detector

- **Noise Reduction:**  
    Canny begins with Gaussian smoothing, which significantly reduces the effect of noise. In contrast, the Sobel operator is applied directly to the image without any pre-smoothing, making it more susceptible to noise.
    
- **Edge Localization:**  
    Through non-maximum suppression, Canny precisely localizes edges by thinning them to one-pixel-wide lines. The Sobel detector, on the other hand, produces thicker edges that may not be as well localized.
    
- **Robust Thresholding:**  
    The double thresholding and edge tracking by hysteresis in Canny help to distinguish between strong and weak edges, ensuring that true edges are preserved while noise-induced edges are discarded. Sobel typically uses a single threshold, which may result in either missing weak edges or including too much noise.
    
- **Overall Accuracy:**  
    Canny’s multi-stage process (smoothing, gradient computation, non-maximum suppression, and hysteresis) is designed to optimize both the detection of true edges and the suppression of spurious responses, leading to cleaner, more continuous, and well-defined edges compared to the simpler gradient-based approach of Sobel.