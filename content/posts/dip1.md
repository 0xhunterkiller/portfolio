---
title: Intro to Image Manipulation
date: 2021-06-01
tags: [image-processing]
--- 

What are Images? What form do they exist in?

![](https://cdn-images-1.medium.com/max/2000/1*ybfjlwDfxtFvQpYNw_9Fcw.jpeg)

Note: This series assumes that you have a intermediate level understanding of Python, and a basic level understanding Linear Algebra (esp. Matrices and Matrix Operations) and Calculus.

Images are everywhere, starting from X-Rays used to save people’s physical lives to memes that are used to save their mental lives.

Being blind in this beautiful world is a very depressing thing indeed, so why let the computers miss out on the fun ?

One might argue that, that’s why cameras exist, but the thing about it is, cameras only help us capture the image data and put it into a frame or a computer. You can view it, but it means nothing to the computer. To a computer, all images are simply matrices.

If you keep zoom in to an image, you might start seeing squares all over your image. These squares are pixels. Each Pixel has 3 channels.

In a R.G.B image, the 3 channels are [Red, Blue, Green]. The colour of the pixel is a mixture of the red, blue and green channels.

If the Red Channel has a value of 1 and the other 2 channels have a value of 0. Then the pixel will be Red in colour. Most computers have pixel colour values ranging from 0 to 255(uint8). Some might have them range from 0 to 65535(uint16).
> White — [255,255,255]
> Black — [0,0,0]
> Red — [255,0,0]
> Green — [0,255,0]
> Blue — [0,0,255]

![This is the image we’ll work on! — PC Suraj Nukala](https://cdn-images-1.medium.com/max/3840/1*dYkCOoHM8mmOQQaX6zh_BQ.jpeg)*This is the image we’ll work on! — PC Suraj Nukala*

We start by importing the required packages…

    import matplotlib.pyplot as plt
    import numpy as np

We read the image using the ‘pyplot’ inbuilt function,

    img = plt.imread(‘asuma.jpg’)

Now, the img variable has the data of the image, ‘asuma.jpg’

![This is a numpy array, of the first 5 rows and columns in the image.](https://cdn-images-1.medium.com/max/2000/1*oyq8CYhrQDam-EiH3ni6Dw.png)*This is a numpy array, of the first 5 rows and columns in the image.*

Numpy is a Python Library that helps one work with Linear Algebra, Matrices and Fourier Transforms. It was created in 2005 as an open-source project by Travis Oliphant. It remains one of the standard libraries in the field of Data Science.

![The Image size is 1080 x 1920, but what is the 3?, it is the number of channels.](https://cdn-images-1.medium.com/max/2000/1*02XjuT2MV7L5ey5dudKA0w.png)*The Image size is 1080 x 1920, but what is the 3?, it is the number of channels.*

Let us look at the pixel on the 1000th row and 500th column, and check if it is grey in colour.

![We were right! [rows, columns, channels]](https://cdn-images-1.medium.com/max/2000/1*rSyjY4ZO1PV-A1Ccdy0g_g.png)*We were right! [rows, columns, channels]*

Let’s now cover the dude’s face with a big blue square. The face region spans from 0th to 500th rows and 1150th to 1650th columns.

![](https://cdn-images-1.medium.com/max/2000/1*3ZnD60xV-F0JPlXuKNj_Ow.png)

Lets, create our own image, and give colours to it,

![](https://cdn-images-1.medium.com/max/2000/1*vnKmiYix-ApMJ5X614O-Dw.png)

Let’s extract each channel of the image we created,

![](https://cdn-images-1.medium.com/max/2000/1*U_C3Zr3Yql-UcFICzSw1bw.png)

Look at how the Red channel has only the Red part brightened and similarly for the other 2 channels, manipulating these 3 channels is crucial for efficient image processing.

There are many computer vision libraries, some of the best of skimage and opencv-python. SciPy is also a good alternative.

SK-Image does not allow video-processing in realtime, but opencv does. OpenCV is also faster than skimage, but has lesser pre-implemented algorithms. Pillow is the standard library for image processing in python.

Thank you, do leave your feedback in the comments.
