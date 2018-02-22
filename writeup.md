# **Finding Lane Lines on the Road** 

## Writeup 


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: /test_images_output/output_whiteCarLaneSwitch.jpg "Output"

---

### Reflection

### Pipeline:

My pipeline consisted of 6 steps. First, I converted the images to grayscale, then I pass the image in grayscale to the canny edge detection function and then apply gaussian blur to it. Then I created a region of interest for the image, so that the operation will be performed only that specific portion. Then lane lines are generated with the help of Hough Line Transform and by using the hough_lines() helper function.


###draw_lines() function:
In order to draw a single detected line on the left and right lanes, I modified the draw_lines() function by finding the slope and intercepts. Here's the steps that I followed

1.Find the slope of the lines that are detected.
2. If the slope is less than 0, then add it to the list of left slopes and corresponding x and y values to left and right x and y values list, and if the slope is greater than 1, then add it to the list of right slopes
3. Then take mean of the the left and right slopes,x's and y's from the list created.
4. Then using the slope intercept form, find the intercepts from left and right lane lines using following equation
intercept = mean of y - mean of slope*mean of x
(b = y - m*x)
5. Then using this intercepts, we can construct the extrapolated lines, by finding the x values of the co-ordinates, by using following equation.
x= (y-b)/m
6. The y values can be provided by taking the max of y co-ordinates of the image and the least value of the left or right y list that we calculated previously.
7. After knowing the values we can simply plot the lines.




### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the road is curved, then it will be difficult for the algorithm to detect lines as they are curved.
Another shortcoming could be if there's line like structure on another car that is front of our car and is in the region of interest, then it confuse the algorithm.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to develop is for curved lane lines, this would increase the credibility of the algorithm

Another potential improvement could be to improve lane line detection when the visibility of the camera is not that good.
