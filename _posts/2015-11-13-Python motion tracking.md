---
layout: post
title:  "Motion Tracking in Python"
date:   2015-11-13
categories: Python
---
Motion tracking is a common technique for analyzing moving objects in automated image/video processing. Several of my research project involved motion tracking, so I decided to write a motion tracking script for my own convenience. The script was written in Python and used [PyQt](https://wiki.python.org/moin/PyQt) for GUI and [scikit-image](http://scikit-image.org/) for image processing.

The requirement for this script is

- Python 2.7
- PyQt4
- scikit-image 0.11.3

The above setup is good enough for single-frame image analysis. For motion tracking of videos, there needs to be a proper way for importing videos and converting them into numpy arrays. There are a few Python library for importing videos, most notably [OpenCV-Python](https://opencv-python-tutroals.readthedocs.org/en/latest/#). The drawback of this OpenCV module is it lacks proper documentation, so it hard to get started for beginners (like me). The other concern is that my research project involve processing videos taken by microscopes, whose formats are wildly varied - every manufacturer of microscopes has their own formats. Since imaging processing is a critical topic in modern biology, there is a well-developed Python module for dealing with these microscopic video files called [Python-Bioformats](http://pythonhosted.org/python-bioformats/), which is used in my motion tracking script. The module is a Java library, so [javabridge](https://pypi.python.org/pypi/javabridge) is used for starting Java virtual machine. In summary, to process microscopic videos with file formats like Nikon .nd2, we also need

* javabridge 1.0.11
* python-bioformats 1.0.5

###My setup on Windows

I use [WinPython 2.7 32 bit](http://winpython.github.io/). I also have JDK 32 bit and JRE 32 bit. The reason for choosing 32 bit is that when you import QuickTime (.mov) videos in Bioformats, 32 bit JVM is required.

###My setup on Mac

I use [Anaconda](https://www.continuum.io/downloads). They only have 64 bit so I'm yet to figure out how to run a 32 bit JVM and import QuickTime video.

[VIEW SOURCE ON GITHUB](https://github.com/xngli/Microtissue-Image-Registration)
