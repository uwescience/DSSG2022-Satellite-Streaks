---
layout: page
title: Validating that the detected lines are streaks.
---

Validating a streak involves taking the median intensity pixel values* of each row of an image containing a streak to obtain the profile of that image. This analysis is most efficient when the streak is horizontal. Therefore before the algorithm before validation analyses, it rotates all streaks in an image such that they are horizontal. *insert image shown on presentation with rotated streak*

**Rotation Algorithm for One Streak**

The rotation algorithm rotates an image by each cluster of hough lines determined. In some cases, an image only contains one cluster with a single hough line. The algorithm starts by finding two cartesian coordinates for the hough line since scikit image returns information about hough lines in polar coordinates. The two points found are the points at which the line enters the image and the point at which the line exits the image, or the edge points. These the edge points are used to calculate the slope, using the slope formula, and the angle of rotation is found by taking the inverse tangent of the slope.

Before rotating the image, an anchor point is set to accurately determine the location of the streak after rotation for easier cropping methods. The anchor point is determined to be the midpoint of the hough line. The image is rotated then cropped to isolate the streak into its own image

**Median Pixel Intensity Values**

After the image has been rotated and the streak has been isolated, we can now plot its pixel intensity values. Plotting pixel intensities tells us what and where the brightest object is located in our image. We take the median of the pixels because since a streak consists of clustered and extended pixel intensities, it offsets any outliers such as background noise or other bright objects. When we plot an image that doesn’t contain a streak, the plot outputs very narrow peaks. Whereas when we plot an image that does contain a streak, the plot generates a peak that looks approximately gaussian. Since the peak looks approximately gaussian, we use a gaussian as our model to fit a line through in order to determine whether or not we measured a streak from the image.

[![](/assets/img/methods/median_pix_val.png)](/DSSG2022-Satellite-Streaks/assets/img/methods/median_pix_val.png)

We only want to measure the image data when it contains a streak in it. As mentioned before, when we try to plot the pixel intensity values of an image without a streak, the plot generates narrow peaks and does not look approximately gaussian. Because of this, when we try to fit a line through it, it does not converge and does not pass our validation algorithm. At this point of the process, Satmetrics would not continue onto the next step of measuring properties since there is no streak to measure, therefore throwing this data away. 

[![](/assets/img/methods/median_pix_val_noise.png)](/DSSG2022-Satellite-Streaks/assets/img/methods/median_pix_val_noise.png)

