# **Finding Lane Lines on the Road** 

## Writeup 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

[gray-scale-image]: ./test_images_output/gray-scale/solidWhiteCurve.jpg "=100x20"

[gray-scale-with-Guassina-Blur-image]: ./test_images_output/gray-scaleGB/solidWhiteCurve.jpg

[edges-image]: ./test_images_output/edges/solidWhiteCurve.jpg

[edges-with-mark-image]: ./test_images_output/edgesWithMask/solidWhiteCurve.jpg

[result-image]: ./test_images_output/results/solidWhiteCurve.jpg

---

### Reflection

### 1. Describe my pipeline. 

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]

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

To average and interpolate the lines on the draw_lines function, I try to find the lines going on the left and right side of the image. Each point of those sides were accumulated and first degree polynomial was fit to those points using numpy.polyfit. When the line equation was found, it was evaluated on the region of interest to define the points where the line would be shown on the image.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...

The lines shake a lot on the videos, a better way to average them should be possible.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...

The line size should be improved.

Bright points outside the lines were taking into account.