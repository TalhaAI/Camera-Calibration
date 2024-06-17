# Camera Calibration

## Introduction

Camera calibration is a way to find the extrinsic and intrinsic parameters of the camera. We use five images of a checkerboard pattern with Jean-Yves Bouguet Camera Calibration Toolbox for MATLAB to perform camera calibration. The camera parameters can then be used for various applications such as 3D reconstruction, robotics, and augmented reality.

## Methodology

All five images of a checkerboard were loaded in MATLAB using the Toolbox. The corners of the checkerboard pattern in each image were identified manually. The window size was set to 11x11 with 13 squares along the X direction and 14 squares along the Y direction, with each square measuring 30mm. By processing all the images on the toolbox, the following camera parameters were found:

### Calibration Results After Optimization (with Uncertainties):

- **Focal Length:** `fc = [647.15106, 698.36340] +/- [8.73470, 14.25538]`
- **Principal Point:** `cc = [314.69728, 240.37709] +/- [12.88965, 10.73796]`
- **Skew:** `alpha_c = [0.00000] +/- [0.00000]` => angle of pixel axes = 90.00000 +/- 0.00000 degrees
- **Distortion:** `kc = [-0.17712, 0.44414, -0.00317, 0.00155, 0.00000] +/- [0.06620, 0.28992, 0.00458, 0.00587, 0.00000]`
- **Pixel Error:** `err = [1.77855, 1.31120]`

## Results

### a. Corners Detection

Below are the results of corner detection for all five images of the checkerboard:

- **Crosses** represent the actual corner points in the image identified by the calibration algorithm.
- **Circles** represent the predicted corner points after estimating the camera parameters.
- **Green Line** connecting the crosses and circles represents the error between the detected and predicted corner points in the images.

The reprojection error helps identify the points contributing most to the error, and this plot can be used to further refine the prediction model.

### b. Views

#### i. Camera-Centered View

- **Origin O** represents the position of the camera in its coordinates.
- **Checkerboards** numbered from 1 to 5 represent all the images used for camera calibration with their position with respect to the camera coordinate system.

#### ii. World-Centered View

- **Large Grid** at the bottom represents the stationary reference plane of the checkerboard pattern.
- **Cameras** numbered from 1 to 5 represent the orientation of the camera for all the five calibrated images of the checkerboard.

Both views are very useful for 3D reconstruction and augmented reality applications.

### c. Distortion Models

Distortion represents the bending or warping of images due to imperfections in camera lenses, making straight lines look curved or objects appear stretched or compressed in photos.

#### Camera Parameters Found by Calibration:

- **Focal Lengths:** `[647.151, 698.363]` pixels
- **Principal Point:** `[314.697, 240.377]` pixels
- **Skew:** `0` (indicating the x and y pixel axes are orthogonal)
- **Distortion Coefficients:**
  - **Radial:** `[-0.1771, 0.4441, 0]`
  - **Tangential:** `[-0.003169, 0.001554]`

The error in distortions is in the acceptable range, representing a successful calibration process.

#### i. Complete Distortion Model

Combines both radial and tangential components of distortion. Blue arrows on the plot represent the distortion direction and magnitude, with concentric circles indicating pixel error increasing towards the edges of images.

#### ii. Tangential Component

Represents the skewed or tilted effect in photos, especially towards the origin, occurring when the lens plane is not parallel to the image plane.

#### iii. Radial Component

Indicates that straight lines in the real world appear curved in images, more noticeable towards the edges.

## Discussion

### a. Impact of Initial Corner Selection Accuracy

- **Slightly Incorrect:** Limited impact on the final result, but the optimization process may require more iterations.
- **Significantly Incorrect:** Significant impact, as large initial errors may prevent convergence to a meaningful solution.

### b. Identifying Significant Errors

Difficult to accurately identify errors in camera calibration. Error metrics, visual inspection, and testing on different scenes can help identify inaccuracies.

### c. Error in Calibration Model

- **Two Images with Slight Rotation:** High error, insufficient information about camera parameters.
- **Modest Number of Images with Variations:** More accurate model, capturing large distortions and characteristics of the camera.
- **Large Number of Images with Variations:** Error does not always go to zero due to noise, redundancy, and lens distortions.

### d. Incorrect Square Size

Incorrect square size leads to incorrect corner detection and camera parameters. Can be identified visually and through error metrics.

### e. Importance of Even Lighting

Even lighting reduces variations in brightness and shadows, crucial for accurate measurements and corner detection.

### f. Window Size for Corner Detection

Larger window sizes capture more information but may increase the chances of overlapping features, making it challenging for the algorithm to differentiate corners, leading to longer processing times.

### g. Condition Number of Matrix

The condition number indicates the accuracy of numerical solutions. A lower condition number is preferred for stable and precise calibration.

### h. Floating Point Machine Arithmetic

Ensures convergence, accuracy, and precision of iterative solutions in numerical algorithms for camera calibration.

## Conclusion

The five images of a checkerboard pattern captured from different perspectives were used to estimate the intrinsic and extrinsic parameters of the camera. The Jean-Yves Bouguet Camera Calibration Toolbox for MATLAB was used for this calibration process, resulting in accurate camera parameters useful for various applications.
