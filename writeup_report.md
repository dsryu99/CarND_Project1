# **Finding Lane Lines on the Road**

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve.jpg

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. First, I converted the images to grayscale, then applied Gaussian smoothing.
Canny edge detection algorithm is peformed to find edges of the input image. Using the polygon, the region of the image we are interested in is only remained. By using Hough transformation, I found lane lines on the road. Finally, the original image and the lane lines detected are added in one image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by checking if the slope of each line segment is positive or negative. The right lanes have the positive slope and the left lanes have the negative slope. In order to remove outliers, the angle ranging from 25 to 75 degrees is only considered valid.  

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be the region of interest will not be correctly recognized when different images or videos are used as input. The reason is that the specific values are set for the vertices.

Another shortcoming could be the way to address the outlier detection will not succeed because the valid range of the angle is manually configured.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to identify the region of interest automatically by analyzing each image.

Another potential improvement could be to apply more advanced outlier detection algorithms to find the valid line segments after the Hough line detection.
