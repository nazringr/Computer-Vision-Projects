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
![Frame with Trajectory](https://raw.githubusercontent.com/nazringr/Computer-Vision-Projects/main/Project%201:%20Object%20Tracking%20and%20Parabolic%20Curve%20Fitting/Frame%20with%20Trajectory.png)


_________

## Project 2: Video Processing Pipeline and Image Stitching

**Description**  
This project focuses on designing a video processing pipeline to detect the four corners of a piece of paper in a video, using techniques such as edge detection, Hough Transform, and corner detection. The goal is to overlay the detected boundaries and highlight the corners of the paper in each frame, while also removing any blurry frames.

### Task 1: Paper Corner Detection and Boundary Overlay

**Key Features**
- Video frame extraction and processing using OpenCV.
- Detection and skipping of blurry frames using Variance of the Laplacian.
- Background segmentation to isolate the paper from the surroundings.
- Edge detection and Hough Transform to identify straight lines.
- Corner detection using Harris Corner Detector.
- Overlay of boundaries and corners in the output video.

**Steps Implemented**
1. **Read Video and Extract Frames**:  
   The video is read, and individual frames are extracted using OpenCV.

2. **Skip Blurry Frames**:  
   Variance of the Laplacian is applied to detect blurry frames. Any frame with a variance below 150 is considered blurry and skipped.

3. **Segment Background**:  
   Each frame is converted to grayscale, and unwanted background areas are segmented out by thresholding, retaining only the white regions.

4. **Edge Detection**:  
   An edge detector (e.g., Canny) is used to identify edge pixels in each frame.

5. **Hough Line Detection**:  
   The Hough Transform is applied to extract straight lines from the detected edges. Short lines are filtered out to retain the dominant ones.

6. **Corner Detection**:  
   The intersections of the detected lines are computed as potential corners. The Harris Corner Detector is then used to verify these intersections.

7. **Filtering Corners**:  
   Any extraneous corners that are not part of the four corners of the paper are filtered out.

8. **Overlay Results**:  
   An output video is generated with overlaid blue boundary lines and red corners for the paper in each frame, excluding blurry frames.

**Output**  
An output video with the detected edges, boundaries, and corners of the paper highlighted in each frame.
[Link to the Output Video](https://drive.google.com/file/d/1kXk8kiJp7Vsdj-XWEdOgZZ8g6iOou2XV/view?usp=sharing)


### Task 2: Image Stitching (Panoramic Mosaic)

**Description**  
This task involves creating a panoramic mosaic from four overlapping images of a far-away building, utilizing feature extraction, feature matching, and homography computation.

**Key Features**
- Feature extraction using a method like SIFT to identify key points and descriptors.
- Feature matching between consecutive image pairs using RANSAC to filter outliers.
- Homography computation for aligning images.
- Image stitching to create a single panoramic image.
- Post-processing to crop black borders from the stitched image.

**Steps Implemented**
1. **Feature Extraction**:  
   Key points and descriptors are extracted from the overlapping images using a feature extractor (e.g., SIFT).

2. **Feature Matching**:  
   Features are matched between consecutive image pairs using RANSAC to filter out any outliers.

3. **Homography Computation**:  
   Homographies between consecutive image pairs are computed to align the images.

4. **Image Stitching**:  
   The computed homographies are used to warp and stitch the images together to form a single panoramic image.

5. **Post-processing**:  
   Any black borders from the stitched image are cropped to enhance the final result.

**Output**  
A panoramic image created from the four input images.
![Frame with Trajectory](https://github.com/nazringr/Computer-Vision-Projects/blob/main/Project%202%3A%20Video%20Processing%20Pipeline%20and%20Image%20Stitching/task2_output.png)
_______

## Project 3: Camera Calibration and Reprojection Error Analysis

### Task 1: Image Collection and Calibration Pipeline

**Description**  
This project involves calibrating a camera using a calibration board (chessboard or circular pattern) and analyzing reprojection errors. The objective is to collect images, detect corners or centroids, and optimize camera parameters for accurate image representation.

### Key Features
- Collection of approximately 50 images of a calibration board.
- Utilization of OpenCV functions for camera calibration.
- Step-by-step explanation of the calibration pipeline, including image undistortion.
- Analysis of reprojection errors to evaluate calibration accuracy.
- Visualization of detected corners/centroids before and after calibration.

### Steps Implemented
1. **Image Collection**:  
   Collected around 50 images of a calibration board, which are stored in Google Drive.  
   [Link to images](https://drive.google.com/drive/folders/194hs49UdUlIuKUsUzio2JRcmzz97ho__?usp=share_link)

2. **Calibration Pipeline**:  
   - Chose a chessboard pattern for calibration.
   - Utilized OpenCV functions for corner detection.
   - Provided a detailed explanation of each stage, including:
     - Initialization of calibration parameters
     - Image undistortion
     - Optimization of camera intrinsic and extrinsic parameters
   - Displayed the original image and the undistorted image.

3. **Reprojection Error Analysis**:  
   Plotted the reprojection error for each image used in the calibration process.  
   Discussed the significance of reprojection error concerning calibration accuracy.

4. **Visualization of Calibration Results**:  
   Drew detected corners on the original images and displayed results before and after calibration.  
   Used different colors to differentiate between original and reprojected points.

### Output

   A plot showing the reprojection error for each image used in calibration, giving insights into calibration accuracy.

<img src="https://github.com/nazringr/Computer-Vision-Projects/blob/main/Project%203%3A%20Camera%20Calibration%20and%20Reprojection%20Error%20Analysis/task1_error.png" height="300" />

  

![Calibration Output](https://github.com/nazringr/Computer-Vision-Projects/blob/main/Project%203%3A%20Camera%20Calibration%20and%20Reprojection%20Error%20Analysis/task1_output.png)

### Task 2: Stereo Vision System

**Link to the images**: [Google Drive Link](https://drive.google.com/drive/folders/1wkjEqhttgPs0nDvFVnsBeinE7ukYL2-f?usp=sharing)

In this task, three datasets are provided, each containing two images of the same scene captured from different camera perspectives. Each dataset includes a `calib.txt` file detailing the camera matrices, baseline, image size, and other parameters necessary for calibration and stereo vision.

### Pipeline for Creating a Stereo Vision System:
1. **Calibration**:
   - **a.** Identify matching features between the two images in each dataset using any feature matching algorithms.
   - **b.** Estimate the Fundamental matrix using RANSAC method based on the matched features.
   - **c.** Compute the Essential matrix from the Fundamental matrix considering calibration parameters.
   - **d.** Decompose the Essential matrix into rotation and translation matrices.

2. **Rectification**:
   - **a.** Apply perspective transformation to rectify images and ensure horizontal epipolar lines.
   - **b.** Print the homography matrices (H1 and H2) for rectification.
   - **c.** Visualize epipolar lines and feature points on both rectified images.

3. **Compute Depth Image**:
   - **a.** Calculate the disparity map representing the pixel-wise differences between the two images.
   - **b.** Rescale the disparity map and save it as grayscale and color images using heat map conversion.
   - **c.** Utilize the disparity information to compute depth values for each pixel.
   - **d.** Generate a depth image representing the spatial dimensions of the scene.
   - **e.** Save the depth image as grayscale and color using heat map conversion for visualization.

### Parameters in `calib.txt`:
- **cam0, cam1**: Camera matrices for the rectified views, in the form `[f 0 cx; 0 f cy; 0 0 1]`
  - `f`: focal length in pixels
  - `cx, cy`: principal point
  - `doffs`: x-difference of principal points, doffs = cx1 - cx0 (here always == 0)
  - `baseline`: camera baseline in mm
  - `width, height`: image size
  - `ndisp`: a conservative bound on the number of disparity levels; the stereo algorithm MAY utilize this bound and search from `d = 0 .. ndisp-1`
  - `vmin, vmax`: a tight bound on minimum and maximum disparities, used for color visualization; the stereo algorithm MAY NOT utilize this information

### References:
[1] D. Scharstein, H. Hirschmüller, Y. Kitajima, G. Krathwohl, N. Nesic, X. Wang, and P. Westling. High-resolution stereo datasets with subpixel-accurate ground truth. In *German Conference on Pattern Recognition (GCPR 2014)*, Münster, Germany, September 2014.


