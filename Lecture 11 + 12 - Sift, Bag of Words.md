Scale Invariant Feature Transform
Edge Detector, separator between two regions
Blob detector separator of a thin line in a backgorund region
Corner detector, separator of a saleint point in a line

Problem with harris corner is that it is rotation invariant but not scale invariant

Scale Invariatn Feature Transform was proposed by davis lowe in iccv 1999

Generates image features ca;led key points
Invaraint to scaling and rotation
Partially invariant to change in illumination and 3d camera viewpoint
Can be extracted from typical images
Highly distinctive

1d blob manipulation
1d blob (Dob)
1st order detivative
2nd order derivative = LOB

Scale-space extrema detection  
– Uses difference-of-Gaussian function to  
approximate the Laplacian operator  
Keypoint localization  
– Sub-pixel location and scale fit to a model  
Orientation assignment  
– 1 or more for each keypoint  
Keypoint descriptor  
– Created from local image gradients

Keypoints are detected using scale-space  
extrema in difference-of-Gaussian function D
Efficient to compute

Relation of D to o2delta2G

Close approximation to scale normalized Laplacian of Gaussian

Diffusion equation
When D has scales difference by a constant  
factor it already incorporates the σ 2 scale  
normalization required for scale-invariance

A key point is selected only if it is a local  
minimum or maximum in the 3D DoG scale  
space

Key Point Localization (1)  
3D quadratic function is fit to the local  
sample points  
Start with Taylor expansion with sample  
point as the origin  
– where  
Take the derivative with respect to X, and  
set it to 0, giving  
is the location of the key point  
This is a 3x3 linear system  
Derivatives approximated by finite  
differences,

If x ius > 0.5 in any dimension, process is repeated

Post-Processing via Filtering  
Contrast (use prev. equation):  
– If | D(X) | < 0.03, throw it out  
Edge point removal:  
– Use ratio of principal curvatures to throw out  
poorly defined peaks  
– Curvatures come from Hessian:  
– Ratio of Trace(H)2 and Determinant(H)  
– If ratio > (r+1)2/(r), throw it out (SIFT uses r=10)

Keypoint Orientation Assignment (1)  
An orientation is assigned to each keypoint to  
achieve invariance to image rotation.  
A neigborhood is taken around the keypoint  
location depending on the scale, and the  
gradient magnitude and direction is calculated in  
that region.  
An orientation histogram with 36 bins covering  
360 degrees is created. It is weighted by  
gradient magnitude and Gaussian-weighted  
circular window with its sigma equal to 1.5 times  
the scale of the keypoint.

Key Point Orientation Assignment (2)  
The highest peak in the histogram is taken  
and any peak above 80% of it is also  
considered to calculate the orientation.  
– It creates keypoints with the same location  
and scale, but different directions  
It contributes to stability of matching

SIFT Descriptor (1)  
A 16x16 neighborhood around the keypoint  
– Divided into 16 sub-blocks of 4x4 size  
For each sub-block, 8 bin orientation  
histogram is created  
– A total of 128 (=8x16) bin values are available  
– It is represented as a vector to form keypoint  
descriptor  
– Besides, several measures are taken to achieve  
robustness against illumination changes,  
rotation, etc  
212/24/25