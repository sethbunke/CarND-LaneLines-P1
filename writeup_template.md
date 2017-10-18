# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline (pipeline2()) consists of 6 steps:
1 - convert image to grayscale
2 - remove "noise" in the image by applying Gaussian blur and make it easier to identify edges
3 - apply Canny edge detection to identify lines in the image
4 - mask the output of the edge detection to limit the area in which we are looking for lines/remove extraneous lines
5 - apply Hough transform identify lines in the image and draw lines on image
6 - merge the original image with the image that has the Hough lines on it

The Jupyter notebook contains the images that are the output of each of these steps.

The draw_lines() function was modified to use the slope to remove entraneous lines. The slope was then used to determine 
which lines were for the left and right lane lines based on their slope (left lane has a slope < 0). Once the lines were
determines to be left or right, the left-most and right-most lines were kept for the left and right lane lines, respectively.


### 2. Identify potential shortcomings with your current pipeline

One potential shortingcoming is the fact that only the left-most and right-most lines are kept and used. It would probably be
better to use an average of the points of the left and right lines to get an "average" line with an "average" slope for each
of the lane lines. Additionaly, there are conditions where no lines are identified for the left or the right in which case the
code could be modified to use the most recently found line. Also, the lines above the height of the road and don't always extend
to the bottom of the image. 


### 3. Suggest possible improvements to your pipeline

See suggestions included in item 2 above. 
