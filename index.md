---
layout: default
---

<img src="{{ site.url }}{{ site.baseurl }}/assets/img/eScience.png">


# Quantifying the Impact of Satellite Streaks in Astronomical Images

## The Team

**Project Lead/s:** Meredith Rawls and Dino Bektesevic

**Data Science Lead/s:** Vaughn Iverson

**DSSG Fellows:** Abhilash Biswas, Ashley Santos, Kilando Chambers

# Abstract or executive summary

Artificial satellites in Low-Earth orbit (LEO) reflect the sun’s light and leave bright streaks in astronomical images taken by ground-based telescopes. There has been an exponential growth in the number of such satellites in the past few years, a phenomenon which is expected to continue into the foreseeable future. While these satellites are primarily aimed at providing satellite based internet access, they also disrupt night sky based cultural practices, may harm migratory patterns of wildlife, and are causing a rapid  increase of bright streaks in astronomical images, which negatively impacts astronomical research.

The quantification and analysis of satellite streaks in astronomical images is crucial to understand the problem better, draw more attention towards it, and motivate policy actions. However, current efforts in this regard is largely limited to manual analyses of specific images by a few researchers. Our project aims to generalize this process by facilitating large scale analysis of diverse astronomical images containing streaks from telescopes around the world.

Our project uses images collected by the Trailblazer project, an open data repository containing images affected by streaks. We have created a python library called Satmetrics that can ingest a wide variety of images in FITS format, detect streaks in them, and return various properties of those streaks such as brightness and width.  Satmetrics is a starting point for generating information about satellite streaks that will help astronomers study the problem better, aid satellite operators in adopting better brightness mitigation strategies, and provide a firm evidence base for future policy actions.


[![](/assets/img/summary/joined.jpg)](assets/img/summary/joined.jpg)
