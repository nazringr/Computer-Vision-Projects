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

