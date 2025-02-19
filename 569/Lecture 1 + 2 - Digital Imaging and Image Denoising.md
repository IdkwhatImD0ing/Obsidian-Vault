Digital images
1,1 top left
RGB 8 bits per pel
luminance is brightness, correlated with freen
chrominance, cb and cr
gray scale images, uses the luminance channle of a color image
8 bits per pel black gray and white

Image signal processors (ISP) transform camera sensor  
data into images via several digital image processing  
operations:  
n Demosaicing  
n Histogram Equalization  
n Intensity & Contrast Adjustment  
n Smoothing & Sharpening  
n 3 A’s  
• Auto Exposure (AE)  
• Auto Focus (AF)  
• Auto White Balancing (AWB)  
1/12/25

What is basic demosaicing?
Its how to reconstruct missing color values at a particular positions
Simple solution is bilinear interpolation

for red blue its horizontal followed yby vertical interpoliation, green is 4 side

ADvanced Demoisaicing MHC
malvar he cutler demosaicing

To estimate a green component ad a red pixel location, we use corerct terms and 5 point loaplacian red channel. UExplain this in a more easy to undersatnd way

Contrast Enhancement
8 bit gray scale images
Gray Scales 0, 1... 255
0 is black darkest and 255 is white brightest

IMage histogram
low brightness, all pixesl near 0
high brighness all pixels near 255

low contrasct, spread is low
high contrast, spread is high

HIstogram equilization is  spreading out the pixel valuesmakes it more high contrast
color hisogram equiliation also spread outs the values
, more correct colors

Auto exposure, makes the exposure look correct
autofocus, autofocus points are what use to determine the camera will be focusing the image

color correctiong, auto white balancing
many algorihtms, max rgb, grey world

advanced has gamut constraint, neural network etc

Image Filters
Image filter is a nxn array
Earch number in the aray represents a weight coefficient for each pixel convered by the array

examples are low pass and high pass

Another exampl e is sdge sharpening

Image Denoising

Two noise types
Additive nOise
aDDITIVE WHITE GAUSSIAN NOISE
wHITE AND GAUSSIAN

IMpulse Noise (peper/salt noise)
white is salt, sensor saturation
black is pepper noise, dead sensor

mixed noise, is both

removal of salt and pepper is using outlier decetion, then removing

median filtering, median rank order of the samples from smallest ot largest and pick the middle one

removal of awgn

Gaussian Smothing
Basic Denoising Idea
Lowpass filters
Most iomages contents are low frequency
Noise components are high frequency
Use low pass filters to supress noise
edges are high frequency and thus blurred side effect
Gaussian weighted low pass filter

bilaterial filtering
gaussian waiting according to spatial and intensity distance

non local means algorithm
denoising with non local mean
classical problem in image and video processing
x = noising signal
s = original
n = noise


