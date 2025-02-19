## 1. Camera Models and Projections

### 1.1 Types of Cameras

- **Pinhole Camera (Early Pinhole Camera)**
  - **Concept:** A simple camera model where light enters a dark box through a tiny hole.
  - **Mechanism:** Light from a scene passes through the pinhole and projects an inverted image on the wall opposite the hole.
  - **Example:** Imagine a room that is completely dark except for a tiny hole. The scene outside the room is projected upside down onto the wall inside.

- **Perspective Camera**
  - **Concept:** Models the way our eyes perceive the world, accounting for depth and foreshortening.
  - **World and Image Coordinates:**
    - World coordinates: $(X, Y, Z)$
    - Image coordinates: $(u, v)$
  - **Example:** When you take a picture of a long straight road, the parallel edges seem to converge in the distance due to perspective.

- **Orthographic Camera**
  - **Concept:** Projects images without perspective foreshortening.
  - **Characteristics:** 
    - Parallel projection lines mean that objects retain their true size regardless of depth.
  - **Example:** Technical drawings and blueprints often use orthographic projection so that measurements remain accurate and undistorted.

### 1.2 Orthographic vs. Perspective Projections

- **Perspective Projection:**
  - **Property:** Lines converge at a vanishing point (typically on the horizon).
  - **Result:** Objects appear smaller as their distance from the camera increases.
  - **Visual Example:** A row of lampposts appearing to get closer together as they recede into the distance.

- **Orthographic Projection:**
  - **Property:** Projection lines are parallel; there is no convergence.
  - **Result:** Object dimensions remain constant regardless of their distance.
  - **Visual Example:** A floor plan where the scale remains the same throughout, without any distortion due to perspective.

---

## 2. Morphological Image Processing

### 2.1 Introduction to Morphology

- **Definition:** 
  - **Morph:** Refers to shape.
  - **Morphology:** The study of shapes.
- **In Image Processing:** Focuses on the structure and form within binary images.
  - **Input:** Binary images (typically with object pixels as 1 or black, and background pixels as 0 or white).
  - **Output:** Processed binary images for tasks such as denoising, thinning, and shape extraction.
- **Example:** In optical character recognition (OCR), the overall shape of letters is more important than the thickness of strokes.

### 2.2 Binary Image Connectivity

- **Connectivity Definitions:**
  - **4-Connectivity:**
    - A pixel is 4-connected if it shares the same value with one or more of its four immediate neighbors (up, down, left, right).
    - **Example:** In a grid, if the central pixel is black and at least one of its adjacent pixels (above, below, left, or right) is also black, they are 4-connected.
  - **8-Connectivity:**
    - A pixel is 8-connected if it shares the same value with any of its eight neighbors (including diagonals).
    - **Example:** A black pixel connected to another black pixel diagonally is considered 8-connected.
- **Bond Connectivity (Additional Measure):**
  - **Concept:** A quantitative measure where side connections count as 2 points and corner connections count as 1 point.
  - **Usage:** This measure can help in evaluating the strength of connectivity between pixels.

### 2.3 Hit-or-Miss Morphological Filters

- **Purpose:** Identify specific patterns in binary images.
- **Process:**
  - Use an odd-size mask (typically a $3 \times 3$ window) that scans over the image.
  - **Hit:** If the pattern under the mask matches one of the pre-defined hit masks, it is marked as a hit.
  - **Miss:** If it does not match, it’s a miss.
- **Action on Pixels:**
  - **Hit:** Change the central pixel (e.g., flip its value from 0 to 1 or vice versa).
  - **Miss:** Leave the pixel unchanged.
- **Example:** Removing isolated noise dots by detecting and altering small, isolated pixel patterns.

### 2.4 Additive and Subtractive Filters

- **Additive Filters:**
  - **Function:** Enhance or “add” pixels to the image. An example is thickening an object.
- **Subtractive Filters:**
  - **Function:** Remove or “subtract” pixels from the image. Examples include thinning, shrinking, and skeletonizing.
- **Note:** The concept is often self-explanatory by comparing the before and after of an image processing step.

### 2.5 Advanced Morphological Filters

- **Subtractive Filters:**
  - **Shrinking:** Gradually reduces the thickness of objects.
  - **Thinning:** Removes pixels to reduce objects to a simplified version while retaining their structure.
  - **Skeletonizing:** Extracts a one-pixel-wide skeleton of the object.
- **Additive Filter:**
  - **Thickening:** Increases the size of objects in the binary image.
- **One-Stage Filter Design:**
  - When using a single-stage hit-or-miss approach, a larger mask such as $5 \times 5$ (totaling 25 pixels) might be required to capture more complex patterns.

### 2.6 Image-Set-Based Morphology

- **Operations:**
  - **Reflection:** Flipping the image or mask along an axis.
  - **Union:** Combining two sets (or images) by taking the pixel-wise maximum.
  - **Intersection:** Overlapping two sets (or images) by taking the pixel-wise minimum.
- **Example:** In shape retrieval, one might reflect a mask to match features in various orientations and then combine the results using union or intersection operations.

### 2.7 Opening and Closing

- **Opening:**
  - **Definition:** A morphological operation that smooths the contour of an object, breaks narrow isthmuses, and eliminates thin protrusions.
  - **Process:** Typically involves an erosion followed by a dilation.
  - **Example:** Removing small objects or noise from the boundaries of a larger object.
- **Closing:**
  - **Definition:** A morphological operation that fuses narrow breaks and long thin gulfs, eliminates small holes, and fills gaps in the contour.
  - **Process:** Typically involves a dilation followed by an erosion.
  - **Example:** Filling small holes within a segmented object in a binary image.

