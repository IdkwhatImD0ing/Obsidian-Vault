Two main branches of image processing
Image vdeo compression
IMage compression came in 1920
JPEG
Video COMpression 1990-2020
Mpeg1,2,4, etc, h.265

Image undersatnding
Image analysis
computer vision
slow prgress from 1980 ot 2010, rapid progress in last decade

classif edge dection methods
1st order derivative
2nd oprder dervative
canney edge dection from 1986

1st order derivative uses 2d calculus
Differencing filoters often amplify noise
TO supres noise we use low pass filtering and 1st order derivative image filter, compound filter

2nd order derivative edge detector uses 2nd order derivatives
is denoising followed by edge detection
Laplacian of Gaussian (LoG) filters  
– also known as (a.k.a.) the Mexican hat filte

Learning based edge and contour detection
problem definitions:

Find those Visually Salient Contours to help image  
understanding  
• Indicate the intersection of different meaningful regions  

What is edge vs contour?
Low level v.s. Mid level vision task  
• Edge detection  
Ø Sharp changes in image brightness  
Ø Differential operation capture the discontinuities  
Ø Pixel-based  
• Contour Detection  
Ø Contour/Boundary is generalized definition of edge  
Ø Synthesis ability of human vision system  
Ø Patch-based  
Motivation  comes from human vision system, getalt laws
hard to dfefine an edge and contour

How to evaluate?  
• Hard to define an edge/contour...  
Ø Peak gradient magnitude?  
Ø Discontinuity between color/texture?  
Ø Boundary of an object?  
Ø Even the edge sketched by human are different from person to  
person?  
• For the time being, we utilize the segmentation ground  
truth for our goal  
Ø Not aim to match the taste of these subjective results  
Ø Need to be generalized further  
Ø Dataset Bias  


F-measure (Precision-Recall)  
Ø Precision(P) = True Positive / (True Positive + False Positive)  
Ø Recall(R) = True Positive / (True Positive + False Negative)  
Ø Average Precision (AP): Area under the F-curve



Classif Methods

Traditional  
• Very local information about “Edge”  
• Focus on brightness discontinuities  
• Differential operation capture the strength and position

Problems
Sensitive to noise
Weak localization
Pixel weise detection

Differentian based
Soberl 
Prewitt
Log
CAnny


Canny Edge Detector  
• Utilize Post-processing to refine edge maps  
Ø Consider the connectivity of “contour”  
• Three Main Steps  
Ø Convolution with derivative of Gaussian  
Ø Non-maximum Suppression  
Ø Hysteresis Thresholding  
Non-maximum Suppression (nms)  
Ø Suppress the pixels in ‘Gradient Magnitude Image’ which are not  
local maximum

Hysteresis Thresholding  
Ø Choose two thresholds: “high” and “low”  
Ø Above “high”: Edge  
Ø Below “low”: Non-Edge  
Ø Between “high” and “low”: Whether it connect to “Edge” or not

Canny Edge Detector  
• Weakness  
Ø Sensitive to textured regions  
- Ambiguity for understanding  
Ø Not enough for image interpretation  
- Gradient on luminance only  
• Mostly used as a pre-processing step  
Ø Low-level cues still play an important role  
Ø When low precision -> High Recall  


Learning BAsed
Ground truth driven model
Descriminative model
Labe