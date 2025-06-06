# Eigenface Recognition

A small and lightweight application utilising eigenvectors to demonstrate human face recognition.

The VB.NET WinForms application aims to retrieve the nearest image in an enrolled dataset of faces, utilising additional pre-processing techniques to improve accuracy.

I completed this work as part of an undergraduate degree at King's College London, accompanied by a paper titled ***"An Investigation into Biometric Recognition for Mobile Devices"***.

<img src="images/eigenface_recognition_01.png" width="847" height="463"/>

> The application with face images enrolled

<img src="images/eigenface_recognition_02.png" width="564" height="522"/>

> Histogram equalisation is an optional pre-processing step to reduce lighting variation

<img src="images/eigenface_recognition_03.png" width="686" height="558"/>

> Images can be captured from a video source, such as a USB camera

**Features**
- Enrol up to 1000 images from disk
- Supports image capture from a video source, like USB webcameras
- Supports images of any size, with variable resize option
- Apply histogram equalisation to minimise impact of lighting variation
- Attempt matching of a single input face

## Why

I was curious to revisit the project, and after fixing deprecated code, I thought I'd upload a working version for anyone else interested in this domain.

## Running Eigenface Recognition
I've included a packaged executable with the necessary libraries. You can always compile the source yourself.


## Notes
- The eigenface approach to face recognition doesn't necessarily scale as the number of input images grows (especially in the naive approach utilised here), hence there is an upper bound of 1000 images for enrolment.  We observe at least a quadratic time-complexity (see table below)
- A larger image dimension increases the number of data points for which the covariance matrix needs to be computed, and thus compute time. A default dimension of 23x60 is recommended for increasing datasets, which may impact accuracy of recognition, but reduce computation time
- Eigenfaces are notoriously susceptible to face position, expression, and lighting. The best input images are front facing with good lighting, and with the face almost entirely the content of the image. The use of a histogram equalisation filter attempts to mitigate any variance in lighting

<img src="images/eigenface_recognition_04.png" width="500" height="310"/>

## Acknowledgements
- [Mapack linear algebra library for .NET](https://github.com/filgood/Mapack)
- [AForge.NET video input library](https://github.com/andrewkirillov/AForge.NET)
- [Sample face dataset from Georgia Institute of Technology](https://www.anefian.com/research/face_reco.htm)