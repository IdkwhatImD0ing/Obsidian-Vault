There are different types of camera
Pinhole camera
perspective camera
orthographic camera
early pinhole camera
light enters a dark box through a small hole and creates an inverted image on the wall opposite the hole
perspective camera model
X,Y,Z) world coordinates  
(u,v) image coordinates  



Orthographic versus Perspective Projections  
Orthographic projection does not include perspective foreshortening;  
namely, a viewing box whose sides are parallel, instead of one whose  
sides meet in a point at the scene's horizon  

Morphological Image Processing
What Is Morphology?  
• Morph: shape  
• Morphology: study of shapes  
• In the context of image processing  
• Input: binary images  
• Output: processed binary images  
• Denoising  
• Thinning  
• Etc.

Example
shape of a letter has nothing to do with stroke length
Morphological Processing  
• Some objects contain shapes formed by line segments, arcs and  
curves  
• Applications  
• Optical character recognition (OCR)  
• Fingerprint recognition  
• Shape retrieval  
• Etc.

Binary Image Connectivity  
• 1: object pixel (black)  
• 0: background pixel (white)  
• 4-connectivity:  
• A pixel is 4-connected if its value is the same as one (or more) of its four  
nearest neighbors  
• 8-connectivity:  
• A pixel is 8-connected if its value is the same as one (or more) of its eight  
nearest neighbors

ANother connectivity measure is bond
side connectivity, 2 pts
corner 1pt

Hit or Miss Morphological Filters  
• Use an odd-size mask (typically 3x3) to scan a binary image  
• Pre-define a set of hit masks  
• If the underlying patch pattern matches one of the hit masks, it is  
called a “hit”. Otherwise, it is called a “miss”  
• Action:  
• Hit -> take action on the central pixel (usually, change 0 to 1, change 1 to 0)  
• Miss -> no action on the central pixel (copy the central pixel value to the same  
location of the output image)

example, isolated dots removal

additive and subtractive filters
self explanatory

Advanced Morphological Filters
Advanced Morphological Filters  
• Three subtractive filters  
• Shrinking  
• Thinning  
• Skeletonizing  
• One additive filter  
• Thickening

One-Stage Filter Design  
• If we adopt the single-stage hit-or-miss filter solution, the filter size  
has to be of 5x5=25