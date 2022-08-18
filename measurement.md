---
layout: page
title: Measuring streaks
---

When an image does contain a streak in it, its plotted median pixel intensity values will look approximately gaussian, which is the model that we used to determine whether or not we measured a streak. 

[![](/assets/img/methods/approx_gaussian_profile.png)](/DSSG2022-Satellite-Streaks/assets/img/methods/approx_gaussian_profile.png)

Through the creation of the algorithm, we had to first determine what gaussian metrics would indicate that we have measured a streak. After trial and error, we came down to some general thresholds that seem to pass on all the image data we have tested on. When we fit a line through the plot of streaked image, the normalized root mean squared deviation, distance from the middle and full width half maximum have to pass the given streak thresholds that passes our validation algorithm. If the line converges and passes validation, we confirm we have measured a streak. 

When we have a good fit line and pass validation, we keep this data and extract all the quantification metrics from the image. The quantification metrics that are outputted are the mean brightness scaled to the pixel level of the image, the amplitude that represents the height of the streak, the full width half maximum representing the width of the streak and the sigma value.

**Furthering the rotation angle algorithm**

Through the development of the rotation angle algorithm, we had an initial problem of the streak not being completely horizontal. The streak has to be completely horizontal so that we could have more precise streak analysis.

A great benefit of fitting a line through our data is that we were able to use these metrics to help further the rotation angle algorithm. To do this, we had to rotate the angle on the hough transform line with new angle calculations that were close to the original calculated angle we had. Once we had these new angles, we tested them to see which one was the most accurate angle that straightens our line. 

[![](/assets/img/methods/rotation_fits.png)](/DSSG2022-Satellite-Streaks/assets/img/methods/rotation_fits.png)

We tested this by applying the fitting function on the new angle calculation plots. We assume an image with a smaller normalized root mean squared deviation is more representative of a straighter streak, since that is what seemed to be true for most of the streaks as we were comparing other angle calculation plots. As the normalized root mean squared deviation got smaller, the more closely our red fitted line got to our blue real data line.  Because we saw this pattern, we used the angle calculation with the least normalized square root mean deviation that we had for the image or graph, as the new angle calculation used in the rotation algorithm. This process has helped us refine the algorithm and measure our streak properties with more accuracy.
