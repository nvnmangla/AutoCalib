
## I. INTRODUCTION

Camera Calibration is one of the most time consuming but
significant process for any computer vision research involving
3D geometry, of which robotics research is a very prime example. An automatic way to perform efficient and robust camera
calibration was provided by **Zhengyou Zhang of Microsoft**.
In this report is summarized the implementation of Zhang’s
technique for calibration.

## Running Instructions

```
git clone git@github.com:nvnmangla/AutoCalib.git
cd Autocalib/
python3 Wrapper.py 

```

## Data
For the purpose of calibration, total of 13 images of checker-
box of known dimensions were given clicked from different
angle and positions

## Calibration Approach
The Approach for calibration the camera required following
steps
- Find the checker box points $(9 \times 6 = 54)$
- Find the 4 corner points of checker-board (Here we are
ignoring the boundary boxes)
- Calculate Homography Matrix for every image.(Warld to
image coordinates)
- Compute the Intrinsic parameters by solving for $B = A^TA$ where A is the intrinsic camera matrix. 
- This K matrix is used to estimate Matrix R (Rotational)
and t

## Discussion and Results 
The newly obtained Intrinsic Matrix is more accurate as it
is computed keeping distortion in account, this is achieved
by minimizing the euclidean distances between computed
and obtained corners. using the intrinsic camera matrix A,
extrinsic camera matrix R, t and the distortion coefficients Kc.
After optimization there is still some error left because this
optimization gives a local minima. This is why a good initial
guess is necessary. To evaluate the accuracy of the calibration
matrices obtained we compute the re-projection error. To find
the average error we calculate the arithmetical mean of the
errors calculate for all the calibration images. This value comes
out to be **2.3638** 

As can be seen in the following image, we can clearly see
the difference in the original point and the point once the
un-distortion has been performed. The blue circle was the
original point and the red circle represents the point after the
calibration. These calibration matrices are then used to rectify
the images.

![Rectified Image](https://github.com/nvnmangla/AutoCalib/blob/07fbf20fe9165a9074312c22c34ee708917b2e92/processed_imgs/1.png)*Rectified Image*