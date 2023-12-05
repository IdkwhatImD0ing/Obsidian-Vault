Best way to draw a line to seperate two differnt points?

Many method exist

Most popular is Support Vector Machine.

It finds the Maximum Margin Seperators

Basically
Pick the line with the best margin on both sides

As far as possible from any possible points


## What about non linearly seperable?

For example a circle

Use something called a kernel trick
To embed the data into a higher dimentional spacek, which is linearly sepearble

Example. A cluster of points in the middle, and outside

Kernel trick will convert 2d to 3d point, then find a hyperplane as svm line.