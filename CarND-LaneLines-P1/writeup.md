# **Finding Lane Lines on the Road** 

## Writeup 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on work in a written report


[//]: # (Image References)

[gray-scale-image]: ./test_images_output/gray-scale/solidWhiteCurve.jpg

[gray-scale-with-Guassina-Blur-image]: ./test_images_output/gray-scaleGB/solidWhiteCurve.jpg

[edges-image]: ./test_images_output/edges/solidWhiteCurve.jpg

[edges-with-mark-image]: ./test_images_output/edgesWithMask/solidWhiteCurve.jpg

[result-image]: ./test_images_output/results/solidWhiteCurve.jpg

---

### Reflection

### 1. Describe my pipeline. 


My pipeline consisted of 6 steps.

1. First I converted the images to grascale. 

![alt text][gray-scale-image]

2. Then I applied a Gaussian blur to the provided image using cv2.GaussianBlur method. 

![alt text][gray-scale-with-Guassina-Blur-image]

3. Third, I used a Canny transformation to find edges on the blured image. 

![alt text][edges-image]

4. Next, aftering getting edges, I eliminated parts of image which were not intersting in regards to the lane line detection. 

![alt text][edges-with-mark-image]

5. Then, I used a Hough transformation to find the lines on the masked image.

6. Last but not least, I merged the output of the previous step with the original image to draw the lines on it.

![alt text][result-image]

I also rewrote the draw_lines function. I tried to find the left lines and right lines in the image and average them to get clear lines. First, according to slope of any two points, I seperated points into two sets. Each set was formed either left lines or right lines. Then I used polyfit function in numpy to get coefficients of linear equation on each set. Next I drawed those linear lines on the image.


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be sometime it would be difficult to draw lines on dotted lines especially on unclear dotted lines.

Another shortcoming is in videos, lines shake a lot especially when the car was changing directions even a little.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be enlarge kernel size in guassian blur function, in order to remove noise in video or in image. But it is a trade-off thing, because we want to enhance lane lines but blur the noise things.

Another potential improvement could be to change a fixed mask into a flexible mask, or use a non-linear function to draw lines, like draw a curve. But the shortcoming is it would improve time consuming.