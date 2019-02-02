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
 My pipeline consisted of 5 steps.
 
a) First, I converted the images to grayscale and applied the gaussian function for smoothining the images.Then I applied the canny function to select the color transition area and find the edges.

b) I selected the vertex points based on the image shape(540,960,3).

   I initially used the example code for defining the 
   vertices (vertice = np.array([[(0,imshape[0]),(450, 290), (490, 290),(imshape1],imshape[0])]], dtype=np.int32))
   but the lines are forming a triangle and having contact. 
   
   
   Instead of defining the vertices , i tried on different value onassumptions and taken the following values as the areaofinterest    Vertices   
    vertex_1 = (130,540) 
    vertex_2 = (425,320) 
    vertex_3 = (540,320) 
    vertex_4 = (900,540)  
    
    and created the image with masked areas of interest.

c) Now i passed the masked image to the hough transformation with certain values and tried on different combinations of variables (rho, theta, threshold, min_line_len, max_line_gap)
  I got the output but the lines are not aligned properly.

d) In order to draw a single line on the left and right lanes, I modified the draw_lines() function asper suggesting given to find the slope of the two line and confirm the left and right side lines. taken the average values of (x,y) values.
   
c) Then i added the created lines ove rthe orginal image by add weight function.
 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


Potential shortcoming would be 
1. The drawn lines are not perfect for the challenge.mp4 video because the car is moving at different speed compared to white, yellow right.mp4 the image frame condisered  has a curvy image , the code cannot draw the lines along the white lane.

2.If the road is filled with white snow or unable to see the lanes this code cannot be helped.



### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

1. Improve the captured image from the frame to identify the vertices perfectly. 

