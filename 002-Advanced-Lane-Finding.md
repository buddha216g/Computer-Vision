# Advanced Lane Finding Project
Making computer see!

In my previous article, i discussed about four techniques to accurately identify lanes, as shown in the video below. 
 
![Video](https://github.com/buddha216g/Computer-Vision/blob/master/P1-Finding-Lane-Lines/test_videos_output/solidWhiteRight.gif)

However, the car will not be able to find lanes during steep curves or under abnormal lighting conditions or when lanes are of different colors.


We will look at a few techniques to overcome the following issues.

## Issues ##

 1. Steep Curves
 
 2. Different coloured lanes
 
 3. Varying lighting conditions
 

### Steep Curves ###

 - A Self driving car needs to know the lane curvature, apart from speed and car dynamics, to determine the steering angle necessary to stay in the lane.
 
 - To know lane curvature, you need to map lanes from a different perspective (Birds eye view : look from above). 
   But to get the correct perspective, you need to correct for image distortion.
 

 - Image distortion occurs when a camera looks at 3D objects in the real world and transforms them into a 2D image; this transformation isn't perfect
 
 - So, the first step in analysing camera images, is to undo any distortion that exists.
Types of Distortion : Radial and Tangential
 
 Radial Distortion : Distortion at the edges of images, so that lines or objects appear more or less curved than they actually are.
 
 Tangential Distortion : When a camera's lens is not aligned perfectly parallel to the imaging plane, where the camera film or sensor is, it makes an image look tilted so that some objects appear farther away or closer than they actually are.
 
 Camera Calibration is used to un-distort the distorted images. Take pictures of a chessboard, pass it through find corners function to get co-ordinates to obtain image points. Object points are the true corners of a chess board. Use these two to calibrate camera (find distortion coefficients and matrix)
 
 Birds eye view, lets us fit a polynomial to the lane lines. We then extract line curvatures from the polynomial.
 
 Perspective : Objects appear smaller the farther they are from a view point, and parallel lines appear to converge to a point.
 
 Mathematically, the greater the z co-ordinate of a point in an image (z corresponds to depth), the small the object appears on an image.
 
 Perspective transform effectively transforms the apparent z co-ordinate. It warps the image and effectively drags points towards or pushes points away from the camera.
 
 Perspective transform changes our perspective, to view the same scene from different view points and angles. Birds eye view is especially helpful for road images. Similar to un-distortion, maps points from a given image to different desired image points with a new perspective.
 
 To transform an image such that we are effectively viewing objects from different angle or direction
 
 Choosing 4 points manually is not the best option. Many perspective transform algorithms will programmatically detect 4 source points based on edge or corner detection, and analysing attributes like colour and surrounding pixels.
 
 
 Gradient Thresholds: We can use gradients in a smarter way to detect steep edges that are more likely to be lanes.
With canny we take derivatives with respect to x and y.



### Coloured Lanes and Lighting conditions ###

Colour Spaces and Thresholds : In canny and sobel , we converted image to grayscale to find edges. By doing so we lost valuable colour information.

Colour Spaces : RGB works well only for white lanes. It does not work under varying light conditions or when lanes are a different colour like yellow. Image with yellow lines, when split into RGB, only R and G channels show high pixel intensities corresponding to lane lines. Blue channel has zero yellow pixel intensity. Furthermore, R and G channels, do not show yellow lane pixel intensities under brightness and shadows.

HSV (Hue, Saturation, Value) and HLS (Hue, Lightness, Saturation ) colour spaces.
Hue represents colour that is independent of any change in brightness.

Lightness and Value are different ways to measure lightness or darkness of a colour
Saturation is the measure of colourfulness

Finding Lanes : Histogram peaks
Sliding Windows
Search from prior : This is equivalent to using a customised region of interest for each frame of video, and should help you track the lanes through sharp curves and tricky conditions. If you lose track of the lines, go back to your sliding windows search or other method to rediscover them.


<img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/003-CannyEdgeDetection/edges-exit-ramp.jpg" width="400" height="200" >




## Results ##

Application of the above techniques resulted in the car accurately identifying lanes, as shown in the video below. 
 
![Video](https://github.com/buddha216g/Computer-Vision/blob/master/P1-Finding-Lane-Lines/test_videos_output/solidWhiteRight.gif)

### Acknowledgements ###
Sincere thanks to udacity. The final video is the output of my finding lanes line project, of the udacity self driving car nanodegree.


