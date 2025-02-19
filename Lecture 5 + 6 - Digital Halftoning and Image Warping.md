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



