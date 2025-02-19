## 1. Gray-Scale Image Halftoning

Halftoning is a technique used to simulate continuous tones using only two colors (black and white). This is especially useful in printing, where devices often work with a single color of ink.

### 1.1. Concept and Motivation

- **Goal:** Render the illusion of a gray-level image on a two-tone (black-white) medium.
- **Why "Halftoning"?** In printing, darker areas are produced by packing more black dots in a given area, while lighter areas have fewer dots, allowing the paper’s white background to show through.

### 1.2. Pre-Processing: Normalization and Thresholding

- **Normalization:** Scale the image intensities to the range $[0,1]$, where:
  - $0$ represents black
  - $1$ represents white
- **Thresholding:** Decide a cutoff value $T$ such that:

  $$
  \text{Output}(x,y) =
  \begin{cases}
  1, & \text{if } I(x,y) > T \\
  0, & \text{if } I(x,y) \leq T
  \end{cases}
  $$

  However, a fixed global threshold often fails to capture local details.

### 1.3. Halftoning Methods

#### 1.3.1. Dithering

Dithering intentionally adds noise to the image to prevent abrupt transitions and to produce smoother gradients.

- **Why Add Noise?**  
  Noise (a random variable) helps break up the regularity that might otherwise create visible artifacts or “bands” in the image.
  
- **Types of Noise:**
  - **Additive White Noise:** Equal power at all frequencies.
  - **Blue Noise:** Has minimal low-frequency components, reducing visible patterns.
  
- **Adaptive Thresholding:**  
  Instead of simple additive noise, many algorithms use a **threshold matrix** (or dithering matrix) that adapts to local variations. For instance, a $4 \times 4$ matrix assigns different threshold values to pixels within a block, thereby dispersing quantization errors.

- **Shortcomings:**  
  While dithering smooths out transitions, it can sometimes introduce a texture-like pattern that may be noticeable in areas of uniform color.

#### 1.3.2. Error Diffusion

Error diffusion improves upon simple thresholding by redistributing the quantization error to neighboring pixels.

- **How It Works:**
  1. **Thresholding:** Process the current pixel with a chosen threshold.
  2. **Error Calculation:** Compute the error between the original intensity and the quantized value.
  3. **Error Distribution:** Distribute this error to adjacent pixels that have not yet been processed using a weighted mask.

- **Example – Floyd-Steinberg Algorithm:**

  For a pixel at position $(x,y)$, if the error is $e$, the distribution might be:

  $$
  \begin{array}{ccc}
  & \frac{7}{16}e & \\
  \frac{3}{16}e & \frac{5}{16}e & \frac{1}{16}e \\
  \end{array}
  $$

  This feedback mechanism helps preserve overall brightness and detail.

---

## 2. Basic Color Science

Understanding how colors mix is fundamental for both digital displays and printing.

### 2.1. Additive Color Mixing (RGB)

- **Principle:** Colors are created by adding light.
- **Primary Colors:** Red, Green, and Blue.
- **Secondary Colors:**
  - **Red + Green = Yellow**
  - **Green + Blue = Cyan**
  - **Blue + Red = Magenta**

**Example:** In a dark room, overlapping red and green spotlights create yellow light. This model is used in screens and projectors.

### 2.2. Subtractive Color Mixing (CMY/CMYK)

- **Principle:** Colors are produced by subtracting (absorbing) certain wavelengths from white light.
- **Primary Colors:** Cyan, Magenta, and Yellow.
- **Role of Black (K):**  
  Adding black (forming the CMYK model) deepens blacks and reduces ink usage.

**Example:** When painting:
- Yellow pigment absorbs blue light.
- Magenta absorbs green.
- Cyan absorbs red.
  
Mixing all three ideally yields black (in practice, a muddy brown, hence the need for black ink).

### 2.3. Color Image Halftoning

Color halftoning converts a high-quality color image (typically 24-bit RGB) into a format suitable for printers that use discrete color dots.

- **Conversion:** Often involves transforming from the RGB color space to CMY (or CMYK).
- **Technique:** Similar to gray-scale halftoning, techniques like dithering and error diffusion are used—only now they are applied independently to each color channel.

- **Advanced Algorithms:**  
  - **Tetrahedral Quantization:**  
    - **Step 1:** Locate the pixel’s color within a tetrahedral volume in color space.
    - **Step 2:** Quantize it to the nearest vertex.
    - **Step 3:** Diffuse the quantization error to neighboring pixels in the C, M, and Y channels.
  
  - **DBS (Direct Binary Search):** An alternative algorithm that optimizes the placement of halftone dots based on a minimal brightness variation criterion.

---

## 3. Image Geometrical Manipulation and Warping

Beyond color processing, manipulating the geometry of images is essential in graphics, from simple resizing to complex warping.

### 3.1. Basic Geometric Transformations

These operations change the position, size, or orientation of an image.

- **Translation:**  
  Shifting an image by a fixed amount.

  $$
  \begin{pmatrix} x' \\ y' \end{pmatrix} =
  \begin{pmatrix} x + t_x \\ y + t_y \end{pmatrix}
  $$

- **Scaling:**  
  Changing the image size by multiplying the coordinates by scaling factors.

  $$
  \begin{pmatrix} x' \\ y' \end{pmatrix} =
  \begin{pmatrix} s_x & 0 \\ 0 & s_y \end{pmatrix}
  \begin{pmatrix} x \\ y \end{pmatrix}
  $$

- **Rotation:**  
  Rotating an image by an angle $\theta$.

  $$
  \begin{pmatrix} x' \\ y' \end{pmatrix} =
  \begin{pmatrix}
  \cos \theta & -\sin \theta \\
  \sin \theta & \cos \theta
  \end{pmatrix}
  \begin{pmatrix} x \\ y \end{pmatrix}
  $$

- **Affine Transformation:**  
  A combination of translation, scaling, rotation, and shearing that can be represented as a single matrix multiplication.

### 3.2. Image Warping

Image warping maps the coordinates of an image to new positions based on a transformation that may be non-linear.

- **Applications:**
  - **Image Registration:** Aligning images from different sources or viewpoints.
  - **3D Object Warping:** Converting 3D world coordinates to 2D image coordinates in rendering pipelines.

### 3.3. Inverse Address Mapping

When transforming images, output pixels are at integer positions. However, these may correspond to fractional positions in the input image.

- **Backward Mapping:**  
  For each output pixel, compute its corresponding input coordinate. This often results in non-integer coordinates.
  
- **Interpolation:**  
  Estimate the intensity or color at these fractional coordinates using methods such as:
  - **Nearest-Neighbor**
  - **Bilinear Interpolation**
  - **Bicubic Interpolation**

**Example:**  
When rotating an image, a pixel in the rotated output might map to position $(3.4, 2.7)$ in the original image. Bilinear interpolation will compute its value based on the four nearest pixels.

### 3.4. Combined Address and Intensity Mapping

In advanced applications, one may simultaneously map pixel locations (addresses) and adjust their intensity or color values. This combined approach is more complex but can yield powerful effects like simultaneous geometric correction and color enhancement.
