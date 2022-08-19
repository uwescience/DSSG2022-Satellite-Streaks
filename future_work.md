---
layout: page
title: Future Work
---

Satmetrics’ current functionality serves as a foundation to begin the kind of analysis work astronomers and/or enthusiasts would want to have for their own projects. The package is at a great starting point for streak analysis.

We outline three main areas for the future development of Satmetrics below:

**Converting pixel intensity into magnitudes**

Brightness in astronomical images is characterized through units called magnitudes, which are typically calibrated to the brightness of known bright stars or other standard reference points. In the future, it will be important to convert the measured pixel intensities into magnitudes, so astronomers have more additional useful information of the streaks. This is possible through a process called aperture photometry, which will then allow us to calibrate the magnitudes of the streaks. This will also help with evaluating if streaks would be visible to the unaided eye.

**Characterizing performance of Satmetrics on a larger dataset**

We have only tested Satmetrics on select streaked images from the Trailblazer repository. We want to continue testing it on images that are not reduced or pre-processed to evaluate  how well it performs in different situations. Some considerations we would like to measure are false positive rates, false negative rates, and actual performance (how long it takes per image).

**Integrating with Trailblazer**

Ultimately, we seek to integrate Satmetrics into the Trailblazer service. When someone uploads their streaked images, Satmetrics would automatically generate quantifiable information about the streak to aid researchers or enthusiasts in their work to mitigate the impact of bright satellites on astronomy.




