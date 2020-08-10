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



But to get the correct perspective, you need to correct for image distortion.
 

 - Image distortion occurs when a camera looks at 3D objects in the real world and transforms them into a 2D image; this transformation isn't perfect
 
 - So, the first step in analysing camera images, is to undo any distortion that exists.
Types of Distortion : Radial and Tangential
 
 Radial Distortion : Distortion at the edges of images, so that lines or objects appear more or less curved than they actually are.
 
 Tangential Distortion : When a camera's lens is not aligned perfectly parallel to the imaging plane, where the camera film or sensor is, it makes an image look tilted so that some objects appear farther away or closer than they actually are.
 
 Camera Calibration is used to un-distort the distorted images. Take pictures of a chessboard, pass it through find corners function to get co-ordinates to obtain image points. Object points are the true corners of a chess board. Use these two to calibrate camera (find distortion coefficients and matrix)
 
 Birds eye view, lets us fit a polynomial to the lane lines. We then extract line curvatures from the polynomial.






