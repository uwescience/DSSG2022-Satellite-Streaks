---
layout: page
title: Motivation
---

Low Earth Orbit (LEO) satellites have played an integral role in society’s innovations and development by providing wireless communications and internet access. Yet despite their importance as standalone objects, the proliferation of these satellites pose a threat to the natural resource that is the sky. LEO satellites are highly reflective of the sun’s rays and orbit the Earth in the span of 30 minutes. As such, LEO satellites appear as bright, moving objects in the night sky to the naked human eye. Because various species, cultures, and academic fields rely on a clear sky for navigation, traditional practices, and research, these bright objects reduce the integrity of the night sky as an untampered resource. More concerningly, commercial aerospace engineering companies intend to launch LEO satellites at an exponential rate each year for the foreseeable future. As time progresses, the lucidity of the night sky is projected to decrease, as there are no regulations on how reflective these companies are expected to make the satellites they plan to launch.

This problem is especially pertinent for astronomers because LEO satellites impact telescope imaging. When telescopes capture images, they do so over the span of seconds. Because LEO satellites are bright and rapidly moving, these satellites often appear as bright streaks in astronomical images, making astronomical research such as the discovery of new celestial bodies more difficult. And with the planned launch of more satellites, the incidence of these streaks in astronomical images will continue to grow. As of yet, there are few tools that allow astronomers to perform analyses on these streaks such as determining their width, their magnitudes (an astronomical unit for brightness), or their length. (Don’t know how to end. With a question maybe?)

**Motivation/Goal**

Questions: 
  * What type of tool can be created to help astronomers perform efficient streak analysis?


**Output**

The final output of this project is a Python library called Satmetrics. The library can take in any astronomical image in the form of a fits file, extract the possible satellite streaks in it and find the properties of those streaks such as brightness, width etc.

A user can provide this library with multiple astronomical images as well as an optional dictionary of parameters that this library takes. Once the library receives these images, it applies the custom written modules (described below) to identify possible streaks, validate them and measure some of its properties. The properties measured by this library are as follows:
  * Mean brightness scaled to the pixel level of the image
  * Amplitude that represents the height of the streak
  * Full width half maximum representing the width of the streak
  * Sigma

Once validated, the library outputs the result for each detected streak, categorized by the file names and image in which it was present. Once a user receives these results, it could be used in many ways, some of which are:
  * Measuring the satellite streak brightness for a particular group of satellites (such as starlink)
  * Fact checking the measured brightness against operator promised brightness
  * Analyze streak properties for a particular group of satellites
  * Add additional information for each streak in the TrailBlazer public repository
