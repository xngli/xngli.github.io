---
layout: post
title:  "Motion Tracking in Python"
date:   2015-11-13
categories: Python
---
Motion tracking is a common technique for identifying the position of moving objects in automated image/video processing. Several research projects of mine involved motion tracking tasks, so I decided to write a general motion tracking script. The script was written in Python and used [PyQt](https://wiki.python.org/moin/PyQt) for GUI and [scikit-image](http://scikit-image.org/) for image processing.

The requirements for this script is

- Python 2.7
- [PyQt4](https://wiki.python.org/moin/PyQt)
- [scikit-image 0.11.3](http://scikit-image.org/)

The first step in motion tracking is the import the images or videos. The Python Image library [Pillow] (http://pillow.readthedocs.org/en/3.0.x/handbook/image-file-formats.html) supports a variety of commonly used image formats, including .jpg, .png, .fig, .bmp, and .eps, but it doesn't support importing of videos. For motion tracking of videos, there needs to be a proper way for importing videos and converting them into Numpy arrays. There are a few Python library for importing videos, most notably [OpenCV-Python](https://opencv-python-tutroals.readthedocs.org/en/latest/#). The drawback of this OpenCV module is that it lacks detailed documentation, so it's hard to get started. 

When deciding on which module to use for importing videos in the motion tracking script, another consideration is that my research projects involve processing videos taken by microscopes. Therefore, most of the video I need to process has strange formats like .nd2 (by Nikon), and every microscope manufacturer has its own formats. Fortunately, since microscopy and imaging processing is a critical pillar in modern biology, there is a well-developed Python module for dealing with these bioimaging files called [Python-Bioformats](http://pythonhosted.org/python-bioformats/), which I'm going to use in this motion tracking script. The module is a Java library, so [javabridge](https://pypi.python.org/pypi/javabridge) is used for starting Java virtual machine (JVM). In summary, to process microscopic videos with formats like Nikon .nd2, we also need

* [Java Runtime Environment](http://www.oracle.com/technetwork/java/javase/downloads/index.html) (for starting JVM)
* [javabridge 1.0.11](https://pypi.python.org/pypi/javabridge)
* [python-bioformats 1.0.5](http://pythonhosted.org/python-bioformats/)

###My setup on Windows

I use [WinPython 2.7 32 bit](http://winpython.github.io/) and JRE 32 bit. The reason for choosing 32 bit is that when you import QuickTime (.mov) videos in Bioformats, 32 bit JVM is required.

###My setup on Mac

I use [Anaconda](https://www.continuum.io/downloads). They only have 64 bit so I'm yet to figure out how to run a 32 bit JVM and import QuickTime video.

[VIEW SOURCE ON GITHUB](https://github.com/xngli/Microtissue-Image-Registration)
