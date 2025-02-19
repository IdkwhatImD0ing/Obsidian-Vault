Gray-Scale Image Halftoning  

Use black-white (two-tone) images to render gray-level  
images  
n Why called halftoning?  
• Normalize intensities of gray-level images to [0,1]  
• Need to find a threshold to split it into two values – 0 or 1  
• How to do thresholding?  
• Fixed thresholding does not work properly

Printing
uses ink
dpi
rak is black dots
birhtness paper color no ink
goal rendering the illusion of gray level images on two tone devices like printers
darker region to densor black pixels per area
white is sparse black pixels
2 method
dithering and error diffusion
what is ditering?
why is noise needed?

noise = random variable
diterhing via additive white noise and blue noise

practical dfithering algo
instead of using additive noise, use adaptive threadholding
normalize input dynamic range
threadhold matrix
shortcomings of dithering
texture like visual pattersn

so what is error diffusion?
in 1995
feedback to neighboring pixels
error diffusion mask


next
basic color science
color mixing
get more colors based on the primary colors
additive color mixing
rgb
subtractive color mixing
cmy


additive color mixing
additive mixture
overlap spotilights in dark rooms
primary colors
red
green blue
red is longest wavelength
blue is shortest wavelength
secondary colors
magenta
cyan yellow


applications are cry phosphors and multiple projects aimed at a screen

subtractive color mixing
employed with ppaints and pigments
primary colors
yellow
white light subtracts blue
magenta white light substracts green
cyan, white light subtracts red
all lights subtracted, = black

applications
photographic film, paint and crayons

cym is used for prnting
cymk adds pure black, richer black and less ink consumption
conversion from rgb model is simple
to produce more colors tricks like half toning and dithering must be used


color image halftoning
converts 24gpp to 8 options
color cartridge
cyan 0/1 = 1 dot
magenta, yellow = same

color digital halftoning is converting from rgb to cmy color space
digital halftoning, quality does not look so good
why?

minimal brightness variation criterion
Algorithm  
• Find the corresponding tetrahedral volume for a given pixel  
• Quantize its color to that of its nearest corner  
• Diffuse the error to its neighboring pixels in C, M, Y channels  


DBS is another algorithm


Image Geometrical Manipulation  
and Warping

Introduction  
• Geometrical Manipulation  
• Translation  
• Scaling (zoom-in and zoom-out)  
• Rotation  
• Affine transformation  
• Advanced Manipulation  
• Image warping  
• 3D object warping  
• Computer graphic rendering (from 3D world coordinates to 2D image  
coordinates)  
Applications
Image registration
image warping
image coordinates vs cartesian coordinates
start with 1 at top right
transformation between image and cartesian coordinates simple
nverse Address Mapping  
• Render the output image (in integer pixel locations) by tracing back to  
the corresponding input pixel locations  
• The input pixel locations can be fractional numbers  
• Use the interpolation technique to generate the corresponding values