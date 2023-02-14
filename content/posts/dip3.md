---
title: Image Functions, Pixels and Types of Image Processing
date: 2021-07-13
tags: [image-processing]
--- 

Some Mathematics to begin with….

In my previous post, I gave a definition, and now I’m obligated to elaborate,

![](https://cdn-images-1.medium.com/max/2000/1*vDr11MZC45MHaYO713QexQ.png)

An Image maybe defined as a 2D function f(x,y), where x and y are spatial coordinates and the amplitude of f at any pair of coordinates is the intensity or the grey level at that point.

Any Analog Image has to be Sampled and Quantised in order to convert it into digital images for it to be read by our computer. Else, we will be facing the** ‘infinity’ **problem.

A digital image is an image composed of picture elements or pixels, each of which has a finite and discrete quantity of numeric value representing its intensity or the grey level.

![Each little square is a pixel](https://cdn-images-1.medium.com/max/2000/1*6nxQFHM1kS1fAzYO65kMSA.png)*Each little square is a pixel*

In the above 10*10 image consider the origin is in the top left corner and the **Rows span along Y-Axis** and **Columns span along X-Axis**.

If the color black has an intensity of 1 and white has an intensity of 0, then,
> # We say that, the pixel with x = 4(Column) and y = 5(Row) has an intensity of 1 and hence f(4, 5) = 1.

Each pixel can be represented by ‘k’ bits, and will have 2^k number of different values of intensities or grey levels.

The value of ‘k’ is called the **bit-depth.**

![[Credit](https://gregbenzphotography.com/photography-tips/8-vs-16-bit-depth-photoshop) How many shades of grey are you able to see? *Purely Representational*](https://cdn-images-1.medium.com/max/2000/1*QZd9XkX0kz-IAVJclGsTQg.png)*[Credit](https://gregbenzphotography.com/photography-tips/8-vs-16-bit-depth-photoshop) How many shades of grey are you able to see? *Purely Representational**

So, if there is a image with a bit-depth of 3, then we will have 8 different grey levels and for a bit-depth of 8, we will have 256 different grey levels.

The bit-depth also helps in improving the efficiency of digitization, and gives us the closest possible image of the real thing. We get a more accurate representation of the signal that is converted into the image. Allowing us to record even subtle changes in the signal.

This is comparable to how we increase the number of digits after the decimal point to increase the precision of the measurement. Do not confuse this with Image Resolution which is a independent concept.

Why can’t we just keep raising the bit-depth? Read on…

**Channels:**

The Number of numbers we will need to define the color value of each pixel determines the number of channels the pixel has, for example, each pixel in an RGB image has 3 channels, namely, Red, Green and Blue channels, each channel has a grey level,

![[Credit](https://www.geeksforgeeks.org/matlab-rgb-image-representation/)](https://cdn-images-1.medium.com/max/2560/1*AT7SPmKOA-mIn9ffnU9Eqg.jpeg)*[Credit](https://www.geeksforgeeks.org/matlab-rgb-image-representation/)*

So, the intensity of the pixel in each channel will ultimately decide the color of the pixel, by combining the different levels of Red, Green and Blue. For more intuition on this topic read [this](https://saaisudarsanan.medium.com/computer-vision-python-1-3a8af9b3616).

An RGB image of dimensions 800x400 with a bit depth of 8, will have a total of **800 x 400 x 3 = 960,000 pixels** and if each pixel has 8 bits, we will have a image of size **7,680,000 bits = 960,000 bytes = 960 Kilobytes, which is too much for this image. **This is however the raw size of the image, it is uncompressed, we can compress the image using various, compression algorithms like PNG and JPG, to reduce the size.

PNG images are reduced without any loss and are hence of better quality but larger in size, but this is not the case for JPG images, which have some loss and help in reducing the size by a greater deal instead.

**What is an RGB Signal?**

With what you have read, you should now be able to understand, how a video plays… simple,

![This is the values for One Pixel](https://cdn-images-1.medium.com/max/2000/1*dgZDOO-Q7X-miLFg7jcVnA.png)*This is the values for One Pixel*

The above image shows how an RGB signal looks like, continuously changing the values of the 3 channels of the pixels.

### **Noise as Functions:**

As I previously mentioned, images are nothing but 2d functions, and like all functions we can transform them and perform operations of them to get different other results.

A Color Image has 3 such functions stacked as a vector, each pixel will have 3 values. One each for R,G and B.

![f(x,y) is a vector valued function](https://cdn-images-1.medium.com/max/2000/1*m-xmbyuQ62xTKyZ2HZwQzA.png)*f(x,y) is a vector valued function*

Images are often not pure, they are susceptible to noise.

![I’(x,y) is the impure image](https://cdn-images-1.medium.com/max/2000/1*_fIGPtMUXh-ZE8dCe_Lh2Q.png)*I’(x,y) is the impure image*

**N(x,y) is the noise function**. Noise Functions can be mostly classified into 3 categories,

![Left(Pure) — Right(Salt and Pepper Noise)](https://cdn-images-1.medium.com/max/2000/1*ZAYeiPgim8Mn0WbU42LxQA.png)*Left(Pure) — Right(Salt and Pepper Noise)*

**Salt and Pepper Noises **can easily be identified as random black and white spots appearing on the image.

### **Types of Image Processing:**

Image processing can be classified into 3 types based on the output of the process.

![](https://cdn-images-1.medium.com/max/2000/1*P-lnANLhsNwBODwgdsdX4w.png)

Low Level Processes include, Image Acquisition, Image Enhancement, Image Restoration, Color Image Processing, etc.

Mid Level Processes include, Representation and Description, Segmentation, Object Recognition, etc.

High Level Processes include, tasks where the agent has to respond to a scene or a image based on previously understood relations, it is a growing field and is usually associated with Artificial Intelligence. This field is however highly constrained by limited amount of computation power.

Image Processing algorithms often involve a heavy amount of Matrix Multiplications, and require a GPU for running, this is where it gets expensive.

Some algorithms, related to Convolutional Neural Networks may take days or sometimes weeks to complete, and this leaves the programmers with very low margins of error.
