Demosaicing Techniques

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

Expand on Nln Local Means denoising
Also clahe denoising
