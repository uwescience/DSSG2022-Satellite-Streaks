---
layout: page
title: Detecting straight lines
---

The Hough transformation algorithm[^1] counts the number of non-zero pixels on every possible straight line in an image. Then, it returns all estimated lines that have a minimum number of non-zero pixels, the minimum being a user defined threshold. However, astronomical images have various sources of noise in them, such as bright stars, atmospheric effects, etc. This noise also contributes non-zero pixels to the image. If the image has a high amount of noise, then the algorithm will return additional straight lines that do not represent an actual streak. Hence, to increase the accuracy of Hough transformation, Satmetrics applies a collection of image processing techniques that are generalizable and progressively reduce noise. These methods are detailed below in the order they are applied.

**Background reduction**

Estimating the background noise allows us to subtract that background from the input image, getting rid of many sources of noise. In this step, the tool leverages the MedianBackground function from photutils python library[^2] to estimate the background noise in the input image. 

[![](/assets/img/methods/background_reduction.png)](/DSSG2022-Satellite-Streaks/assets/img/methods/background_reduction.png)
*The raw image (left) containing streaks and other astronomical objects and the same image (right) after the background has been removed*

**Binary thresholding**

Reducing the image to a binary array allows us to apply edge detection algorithms on it, which is essential for Hough transformation. Additionally, this processing step allows us to remove outlier values and only retain the range of pixels we expect the streak(s) to be in. We define an upper limit and lower limit of pixel intensity based on a user-defined number of standard deviations from the mean. In the background removed image, pixels above the upper limit are reduced to the upper limit and pixels below the lower limit are reduced to 0. This results in an image where only the brightest pixels are retained. 

[![](/assets/img/methods/thresholded_image.png)](/DSSG2022-Satellite-Streaks/assets/img/methods/thresholded_image.png)
*The thresholded image after a binary thresholding has been applied on the background subtracted image*

**Blurring**

Any pixel containing the streak is likely to have non-zero pixels in its neighborhood. However, random noise points such as a bright star will likely have more zero pixels surrounding it. This next step exploits this difference to remove additional noise in the image. It applies a kernel on all parts of the image and uses these neighborhood pixel properties to remove pixels that likely represent noise. However, in this process, we risk blurring out the streak pixels if the streak is not bright enough and/or a large kernel is applied. Hence, the kernel size is selected based on the proportion of pixels in the image that have an intensity higher than the mean. 

[![](/assets/img/methods/blurred_image.png)](/DSSG2022-Satellite-Streaks/assets/img/methods/blurred_image.png)
*The blurred image after median blurring is applied on the thresholded image*

**Edge detection**

The straight lines representing streaks can be many pixels wide. Hence, applying Hough transformation directly will result in multiple lines being returned for the same streak. To reduce the chances of this happening, the tool takes the blurred image and applies Canny edge detection[^3] on it. Edge detection reduces the image to only single pixel wide edges, which is an important processing step to improve the performance of Hough transformation. 

[![](/assets/img/methods/edge_detection.png)](/DSSG2022-Satellite-Streaks/assets/img/methods/edge_detection.png)
*The detected edges of objects applied on the blurred image*

Satmetrics also provides users with the option of masking the boundaries of the input images. Boundaries or edges of an astronomical image are often prone to noise generated from equipment of the telescope at the edges of its lens. Hence, masking or cropping the edges of an image can potentially help in getting rid of noise. 

Finally, the tool applies the Hough transformation algorithm on the Canny edge image and returns one or more estimated lines. However, since there is always some residual noise in the image, there can be multiple lines returned by the algorithm that represent the same streak. We cluster these lines together based on their proximity to each other in the Hough space. Accurate clustering groups the lines into one or more clusters, where each cluster represents either a single streak or noise. This allows downstream validation algorithms to apply checks at the cluster level, which increases computation efficiency.  

[![](/assets/img/methods/returned_lines.png)](/DSSG2022-Satellite-Streaks/assets/img/methods/returned_lines.png)
*The figure illustrates the estimated lines returned by Hough Transformation*

[^1]: See Hough transform: https://scikit-image.org/docs/dev/auto_examples/edges/plot_line_hough_transform.html
[^2]: Photutils is an Astropy package for detection and photometry of astronomical sources (Bradley et al 20XX)
[^3]: See Canny edge detection: https://docs.opencv.org/4.x/da/d22/tutorial_py_canny.html