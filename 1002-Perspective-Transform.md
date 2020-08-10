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


Perspective : Objects appear smaller the farther they are from a view point, and parallel lines appear to converge to a point.
 
 Mathematically, the greater the z co-ordinate of a point in an image (z corresponds to depth), the small the object appears on an image.
 
 Perspective transform effectively transforms the apparent z co-ordinate. It warps the image and effectively drags points towards or pushes points away from the camera.
 
 Perspective transform changes our perspective, to view the same scene from different view points and angles. Birds eye view is especially helpful for road images. Similar to un-distortion, maps points from a given image to different desired image points with a new perspective.
 
 To transform an image such that we are effectively viewing objects from different angle or direction
 
 Choosing 4 points manually is not the best option. Many perspective transform algorithms will programmatically detect 4 source points based on edge or corner detection, and analysing attributes like colour and surrounding pixels.


