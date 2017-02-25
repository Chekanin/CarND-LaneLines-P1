#**Finding Lane Lines on the Road** 


**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report



### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps:

1. I converted the images to grayscale
2. I blured image with kernel size **9**
3. I found image boundaries by Canny algorithm
4. I detected all line segments by Hough transform
5. I filtered all lines by vertical position, angle with horisont and classify to probably left and right line segments
6. I classified all left and right segments (independently) on probably lines by K-Means algorithm with class number **5** and **100** iteration. I used linear interpolation for calculate center (line) of each class. and I used distance for each class for this line for find nearest class for each segment.
7. I had <= 5 probably lines as candidates for left and <= 5 for right. I also filtered this candidate by angle and by point variance. And I choice one nearest to viewpoint line as left lane line and one as right lane line.


###2. Identify potential shortcomings with your current pipeline

I used hard-coded the valid intervals for line angles and horizon level. The algorithm overfited on the position of the camera and require calibration. Also this is overfitted for daylight and probably will be work bad at night.


###3. Suggest possible improvements to your pipeline

First possible improvement is usage information from from several previous frames (weighted mean of previous and current result for example). This should give more stability

Second possible is auto tune algorithms hyper parameters for a lot markuped different videos