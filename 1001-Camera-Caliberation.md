# Camera Caliberation


Camera Calibration is used to un-distort the distorted images. Take pictures of a chessboard, pass it through find corners function to get co-ordinates to obtain image points. Object points are the true corners of a chess board. Use these two to calibrate camera (find distortion coefficients and matrix)

<img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/001-Color-Selection/test.jpg" width="400" height="200">




## Types of Distortion ##

 1. Radial Distortion
 
 2. Tangential Distortion
 



### Radial Distortion ###

 - Radial Distortion : Distortion at the edges of images, so that lines or objects appear more or less curved than they actually are.
 
 - Tangential Distortion : When a camera's lens is not aligned perfectly parallel to the imaging plane, where the camera film or sensor is, it makes an image look tilted so that some objects appear farther away or closer than they actually are.
 
 <img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/001-Color-Selection/rgb_channels.jpg" >
 
 
 However, this does not fully solve our problem, because you can see other white spots that are not lanes.



### Region Masking ###

Tangential Distortion : When a camera's lens is not aligned perfectly parallel to the imaging plane, where the camera film or sensor is, it makes an image look tilted so that some objects appear farther away or closer than they actually are.



<img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/002-Color_plus_Region_Selection/color_region_selection.jpg"  >

However, under varying lighting conditions (day, night, shade etc) and lane colors (yellow etc) the two techniques we looked at so far, may fail to detect lanes. Hence the need for more sophisticated algorithms.



## Results ##

Application of the above techniques resulted in the car accurately identifying lanes, as shown in the video below. 
 
![Video](https://github.com/buddha216g/Computer-Vision/blob/master/P1-Finding-Lane-Lines/test_videos_output/solidWhiteRight.gif)

### Acknowledgements ###
Sincere thanks to udacity. The final video is the output of my finding lanes line project, of the udacity self driving car nanodegree.


