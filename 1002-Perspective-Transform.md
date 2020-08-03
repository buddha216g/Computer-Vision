# Perspective Transform
Making computer see!

Perspective : Objects appear smaller the farther they are from a view point, and parallel lines appear to converge to a point.
Mathematically, the greater the z co-ordinate of a point in an image (z corresponds to depth), the small the object appears on an image.

Perspective transform effectively transforms the apparent z co-ordinate. It warps the image and effectively drags points towards or pushes points away from the camera.
Perspective transform changes our perspective, to view the same scene from different view points and angles. 

Birds eye view is especially helpful for road images. Similar to un-distortion, maps points from a given image to different desired image points with a new perspective.

To transform an image such that we are effectively viewing objects from different angle or direction

Choosing 4 points manually is not the best option. 

Many perspective transform algorithms will programmatically detect 4 source points based on edge or corner detection, and analysing attributes like colour and surrounding pixels.

<img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/001-Color-Selection/test.jpg" width="400" height="200">


We will look at a few techniques to find lane lines.

## Techniques ##

 1. Color Thresholding
 
 2. Region Masking
 
 3. Canny Edge Detection
 
 4. Hough Transformation


### Color Thresholding ###

 - A colored image is made of a stack of 3 images, each corresponding to red, green and blue channels.
 
 - The above image can be split into three seperate images as shown below
 
 <img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/001-Color-Selection/rgb_channels.jpg" >
 

 - An image is a matrix of pixels whose values range from 0 (dark) to 255 (white)
 
 - Since lanes are white markings on the road, these can be identified, by filtering out pixels less than a certain threshold. See output below.
 
 <img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/001-Color-Selection/color_select.jpg" width="400" height="200" >
 
 However, this does not fully solve our problem, because you can see other white spots that are not lanes.



### Region Masking ###

Assuming the camera that took pictures of the road is mounted on a fixed position in the front of the car, the lane lines will always appear around a general region of the image.

Applying that region of interest to the images (blue dotted region) , we are now able to eliminate non lane lines, as shown below.

<img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/002-Color_plus_Region_Selection/color_region_selection.jpg"  >

However, under varying lighting conditions (day, night, shade etc) and lane colors (yellow etc) the two techniques we looked at so far, may fail to detect lanes. Hence the need for more sophisticated algorithms.



### Canny Edge Detection ###

Goal is to indentify edges of the following image. 

<img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/003-CannyEdgeDetection/exit-ramp.jpg" width="400" height="200" >

Since we are only interested in finding edges, we first convert the colored image into a gray scale image.


<img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/003-CannyEdgeDetection/gray-exit-ramp.jpg" width="400" height="200" >

An image is a mathematical function f(x,y) of pixels, so you can peform mathematical functions on it.
The brightness of each pixel corresponds to the strength of the gradient at that point. We find edge pixels by tracing out the pixels that follow the strongest gradients. By identifying edges, we can more easily detect objects by their shape.  The output of applying canny edge detection algorithm shows an image full of dots, that represent edges of lane lines as well as other objects.

<img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/003-CannyEdgeDetection/edges-exit-ramp.jpg" width="400" height="200" >


### Hough Transformation ###

Since we are interested in finding lane lines, we can model a line and then fit that model to the assortment of dots, to detect lane lines.
To make it easier to work with lots of dots, we use hough space. A point in image space represents a line in the hough space and vice versa.
By using polar co-ordinates, a dot in image space is transformed (hough transformation) into sine curve in hough space.

Applying Hough transformation on the previous canny edge detected image, produced the following output.

<img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/004-Hough-Transformation/hough-exit-ramp.jpg" width="400" height="200" >


## Results ##

Application of the above techniques resulted in the car accurately identifying lanes, as shown in the video below. 
 
![Video](https://github.com/buddha216g/Computer-Vision/blob/master/P1-Finding-Lane-Lines/test_videos_output/solidWhiteRight.gif)

### Acknowledgements ###
Sincere thanks to udacity. The final video is the output of my finding lanes line project, of the udacity self driving car nanodegree.


