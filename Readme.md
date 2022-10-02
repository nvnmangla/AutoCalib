# CMSC733: Homework 1, AutoCalib!

```
Naveen, Mangla
nmangla@umd.edu
```
## I. INTRODUCTION

Camera Calibration is one of the most time consuming but
significant process for any computer vision research involving
3D geometry, of which robotics research is a very prime exam-
ple. An automatic way to perform efficient and robust camera
calibration was provided by Zhengyou Zhang of Microsoft?.
In this report is summarized the implementation of Zhang’s
technique for calibration.

## II. DATA

For the purpose of calibration, total of 13 images of checker-
box of known dimensions were given clicked from different
angle and positions.

## III. CALIBRATIONAPPROACH

The Approach for calibration the camera required following
steps.

```
1) Find all the checker box points(9×6 = 54)
2) Find the 4 corner points of checker-board (Here we are
ignoring the boundary boxes)
3) Calculate Holography Matrix for every image.(Warld to
image coordinates)
4) Compute the Intrinsic parameters by solving for B = AT
A, where A is the intrinsic camera matrix. The initial
intrinsic camera matrix computed for this project is
```
```
Kintial=
```
## 

## 

## 2034 .7510 0.4928 772. 7039

## 0 2017 .9046 1360. 9098

## 0 0 1

## 

## 

```
5) This K matrix is used to estimate Matrix R (Rotational)
and t (Transitional)
6) From these parameters, we calculated distortion
coefficients k 1 .k 2 initializing with zero with
[0,0]T and minimizing the error function using
scipy.optiize.leastsquarefunction.The following values
of the intrinsic camera matrix and distortioin coefficients
were obtained
```
```
Koptiized=
```
## 

## 

## 2039 .3168 0.4539 775. 0797

## 0 2026 .3194 1364. 8693

## 0 0 1

## 

## 

```
k 1 , k2 = 0. 01887696 ,− 0. 10494365
```
## IV. DISCUSSION AND RESULTS

```
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
out to be2.
As can be seen in the following image, we can clearly see
the difference in the original point and the point once the
un-distortion has been performed. The blue circle was the
original point and the red circle represents the point after the
calibration. These calibration matrices are then used to rectify
the images. The output rectified images are shown below:
```
```
Fig. 1: Corners before (blue) and after(red) Distortion
```




- Fig. 2: Rectified Image
- Fig. 3: Rectified Image
   - Fig. 4: Rectified Image
   - Fig. 5: Rectified Image
- Fig. 6: Rectified Image
- Fig. 7: Rectified Image
   - Fig. 8: Rectified Image
   - Fig. 9: Rectified Image
   - Fig. 10: Rectified Image
- Fig. 11: Rectified Image
      - Fig. 12: Rectified Image
      - Fig. 13: Rectified Image
- Fig. 14: Rectified Image


