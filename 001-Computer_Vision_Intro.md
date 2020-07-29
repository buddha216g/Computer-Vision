# Computer-Vision
Making computer see!

Teaching computer to see has wide varieties of applications.

In the context of a self driving car, on seeing the below picture, the car has to know where the lanes are in order to navigate safely.

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
 
 - Since lanes are white markings on the road, these matrices can be manipulated to filter out the irrelevant darker pixels as seen in the output below.
 
 
 <img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/001-Color-Selection/color_select.jpg" width="400" height="200" >
 
 However, this does not fully solve our problem, because you can see other white spots that are not lanes.



### Region Masking ###

Assuming the camera that took pictures of the road is mounted on a fixed position in the front of the car, the lane lines will always appear around a general region of the image.

Applying that region of interest to the images (blue dotted region) , we are now able to eliminate non lane lines, as shown below.

<img src="https://github.com/buddha216g/Computer-Vision/blob/exercises/002-Color_plus_Region_Selection/color_region_selection.jpg"  >

However, under varying lighting conditions (day, night, shade etc) and lane colors (yellow etc) the two techniques we looked at so far, may fail to detect lanes. Hence the need for more sophisticated algorithms.



### Canny Edge Detection ###

Now let's look at the first step to our state estimation: including information from our IMU.  In this step, you will be improving the complementary filter-type attitude filter with a better rate gyro attitude integration scheme.

1. Run scenario `07_AttitudeEstimation`.  For this simulation, the only sensor used is the IMU and noise levels are set to 0 (see `config/07_AttitudeEstimation.txt` for all the settings for this simulation).  There are two plots visible in this simulation.
   - The top graph is showing errors in each of the estimated Euler angles.
   - The bottom shows the true Euler angles and the estimates.
Observe that there’s quite a bit of error in attitude estimation.

2. In `QuadEstimatorEKF.cpp`, you will see the function `UpdateFromIMU()` contains a complementary filter-type attitude filter.  To reduce the errors in the estimated attitude (Euler Angles), implement a better rate gyro attitude integration scheme.  You should be able to reduce the attitude errors to get within 0.1 rad for each of the Euler angles, as shown in the screenshot below.

![attitude example](images/attitude-screenshot.png)

In the screenshot above the attitude estimation using linear scheme (left) and using the improved nonlinear scheme (right). Note that Y axis on error is much greater on left.


### Hough Transformation ###

In this next step you will be implementing the prediction step of your filter.


1. Run scenario `08_PredictState`.  This scenario is configured to use a perfect IMU (only an IMU). Due to the sensitivity of double-integration to attitude errors, we've made the accelerometer update very insignificant (`QuadEstimatorEKF.attitudeTau = 100`).  The plots on this simulation show element of your estimated state and that of the true state.  At the moment you should see that your estimated state does not follow the true state.

2. In `QuadEstimatorEKF.cpp`, implement the state prediction step in the `PredictState()` functon. If you do it correctly, when you run scenario `08_PredictState` you should see the estimator state track the actual state, with only reasonably slow drift, as shown in the figure below:

![predict drift](images/predict-slow-drift.png)

3. Now let's introduce a realistic IMU, one with noise.  Run scenario `09_PredictionCov`. You will see a small fleet of quadcopter all using your prediction code to integrate forward. You will see two plots:
   - The top graph shows 10 (prediction-only) position X estimates
   - The bottom graph shows 10 (prediction-only) velocity estimates
You will notice however that the estimated covariance (white bounds) currently do not capture the growing errors.


## Tips and Tricks ##

 - When it comes to transposing matrices, `.transposeInPlace()` is the function you want to use to transpose a matrix

