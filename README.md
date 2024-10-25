# Computer-Vision-Projects
This repository contains computer vision-based projects focused on solving perception problems for autonomous systems. Implementations include lane detection, motion estimation, 3D object reconstruction, and more, using Python, OpenCV


## Project 1: Object Tracking and Parabolic Curve Fitting

**Description**  
This project focuses on detecting and tracking the pixel coordinates of a black object thrown against a wall in a video. The objective is to calculate the object's centroid in each frame and fit a parabolic trajectory using the **Standard Least Squares** method.

**Key Features**
- Frame extraction and object tracking using OpenCV.
- Object centroid calculation using color-based detection.
- Fitting a parabolic curve through the tracked centroids using the least squares method.
- Prediction of the object's y-coordinate for a given x-coordinate.
- Visualization of the object's trajectory on a selected video frame.

**Steps Implemented**
1. **Frame Extraction**:  
   The video is read, and individual frames are extracted using OpenCV.
   
2. **Object Detection and Centroid Calculation**:  
   The black object is detected based on color, and its centroid is computed for each frame.
   
3. **Parabolic Curve Fitting**:  
   Using the Standard Least Squares method, a parabolic equation is fit through the object's centroid positions. The equation of the parabola is:
   ```bash
   y = 0.0006476425225924483x^2 - 1.2418693086210888x + 992.2886782577352

4. **Prediction of y-coordinate at x = 1000**
   For x = 1000, the predicted y-coordinate is:
   ```bash
   y_1000 = 398.06
   
5. **Plotting the Parabolic Trajectory**
   A frame from the video (frame number 400) is captured, and the parabolic curve is plotted on it. The object’s centroid positions are also marked.
