# **Finding Lane Lines on the Road**

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteRight_out.jpg "SolidWhiteRight"
[image2]: ./test_images_output/solidWhiteCurve_out.jpg "solidWhiteCurve"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consissted of 5 steps:
1. Convert image to grayscale
2. Define a kernal size and apply the Gaussian smoothing
3. Define Canny algorithm and apply
4. Create a masked edges image
5. Define the Hough transform paramter and get the Hough lines
6. Draw the Hough lines on the edge images

In order to draw the single line one the left and right lanes, I modified the draw_lines() function. Using the scope of lines, which is (y2 - y1) / (x2 - x1), to seperate the right or left lines, I combine the left lines using the average position. Then select the bottom left point in left lines as the left single line point and top right point in left lines as left single line point. Do the same thing in right single line. So, I got the stable lane lines.

Here show some result of my pipeline:

![image1][image1]
![image2][image2]

### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be what would happen when the lanes have big gap or some worn lanes. The Hough transform did not work well.

Another shortcoming could be the stability of the single lane. When the lane has the turn type, the pipeline could not show the right lanes.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to predict the lanes' curve. I can calculate the curvature in each lane segment and interpolate the whole lanes.
