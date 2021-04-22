# object_detection_by_active_contours_Canny_algorithm

. Using Canny and active contour algorithms to detect cars on a street. Thresholding has been used to detect
the right size of the contour to show.
. A trained SVM model is later applied on the contour area to predict the color of the cars. The SVM model
is in the repository as pickle file. It has been trained on histogram of kmeans of cars with 9 bins for the histogram.

## Process

1. Read the video frame.
2. Apply a blur and median blur lter on each frame to denoise by keeping the borders. This can be bilateral
or Gaussian lter as well.
3. Calculate Canny algorithm of each ltered frame.
4. Calculate active contours of each Canny output.
5. Loop on all the contours on each frame and approximate the polygon of each contour.
6. Find the bounding rectangle of each polygon from the previous step.
7. Draw the bounding rectangles on each frame and look for the right type of thresholds to only get the cars.
8. Set your thresholds on contour area, bounding circle radius, bounding rectangle width and height.
9. Make a mask on each bounding rectangle and bitwise and it to the original frame.
10. Load an SVM trained classier from previous tasks an apply it on each masked car in each frame.
11. Show the predicted color of each car via the classier.

The result is shown in Fig. 1, 2, 3 and 4.

All frames together are shown in Fig. 5
Note: The classier used in this activity is an SVM classier with poly kernel with default values for C and
gamma, trained on a set of about 20 to 30 cars for colors: black, white, red, blue, gray and yellow. The confusion
matrix is shown in Fig. 6 and 7. The accuracy of this classier is only 62%. In real world application this needs
to be replaced.
