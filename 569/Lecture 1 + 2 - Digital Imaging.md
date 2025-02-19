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