---
title: What are Convolutional Neural Networks?
date: 2021-05-14
tags: [data-science,image-processing]
---
![]()
Images Source — Google

First things first, how are images even stored in a computer?

![Image Credits : [PacktPub](https://subscription.packtpub.com/)](https://cdn-images-1.medium.com/max/2000/1*5tYiY5eyRkkVDjKLMmhrXQ.png)*Image Credits : [PacktPub](https://subscription.packtpub.com/)*

![](https://cdn-images-1.medium.com/max/2000/1*sCSOg0W-FhEY09IPOxBnNQ.png)

In the above image, look how the brighter section of the channel plotted is the corresponding colour. Red in first channel, green in second, blue in the third.

These 3 channels or matrices come together to give us different colours, each element of the matrix denotes a pixel value ranging from 0 to 255.

Gray-scale Images have one channel in them, in further discussion, when I refer to image, it is a gray-scale image.

### Why not use just traditional neural networks?

![Image Credit : [DLpng](https://dlpng.com/png/6033845)](https://cdn-images-1.medium.com/max/2000/1*ehZ7LhczF1rANBM5dcmXPg.png)*Image Credit : [DLpng](https://dlpng.com/png/6033845)*

**Input Size**: For every small increase in the size of the input matrix, the number of parameters that have to be trained in the network increases greatly.

For Example: If we had an image size of **150 x 150 x 3**, indicating a 150 x 150 image with 3 colour channels, we would have to train **67,500 parameters**, but for a **160 x 160 x 3** image we would have to train **76,800 parameters**. That’s around 9000 parameters for the addition of just 10 pixels on each side!

These are just small images, most images we deal with in Deep Learning problems are easily over 500 pixels in height and width. Training these many parameters will eventually lead to over-fitting and increased training times.

**Spatial and Translation Variance:** A traditional neural network can’t gives different outputs for the cat in the bottom left corner of the picture and the same cat in the top right corner of the picture. This is a major drawback since, we cannot possibly train the model on every single variation of the picture!

It is just not feasible!

That’s the reason why we need Convolutional Neural Networks…

![Images Source — Google](https://cdn-images-1.medium.com/max/2510/1*F2Ik_XFzmu5jZF-byiAKQQ.jpeg)*Images Source — Google*
> CNN’s are the visual cortex of the deep learning world. They don’t train on the values of the pixels, but rather remember the features in the object by using filters.

![The Best Illustration I could find for a convolution operation : Images Source — Google](https://cdn-images-1.medium.com/max/2000/1*7p6rKLpjP0u3x0KxsDYrTw.gif)*The Best Illustration I could find for a convolution operation : Images Source — Google*

A Convolutional kernel is applied on the image channel and the value is stored and a feature-map is generated, convolution is further performed on the same feature map to ultimately extract the features in the image.
> # **Every Convolutional Kernel has specific properties, some can detect edges in the image, some can blur the image, but ultimately they preserve the features and discard any spatial data, like what angle the object is in with respect to the vertical or what direction the object is facing. This is why, CNN’s are preferred against traditional networks.**

![Image Credit: [Blogs SAS](https://blogs.sas.com/content/subconsciousmusings/2019/07/03/convolutional-neural-networks-briefly/#prettyPhoto)](https://cdn-images-1.medium.com/max/2000/1*iUKYx5tV60vpTleaw6A33A.png)*Image Credit: [Blogs SAS](https://blogs.sas.com/content/subconsciousmusings/2019/07/03/convolutional-neural-networks-briefly/#prettyPhoto)*

Have a look at this notebook, I created to visualise the outputs of each layer,
[**Intel Image Classification(Feature Map Extraction)**
*Explore and run machine learning code with Kaggle Notebooks | Using data from Intel Image Classification*www.kaggle.com](https://www.kaggle.com/saaisudarsanand/intel-image-classification-feature-map-extraction)
> Why does this work?

Each Filter is used to efficiently identify a feature, how, take a look at this,

![Images Source — Google](https://cdn-images-1.medium.com/max/2000/1*RWhCmpNyp8GBTU62w8e9gA.png)*Images Source — Google*

The receptive field is the part of the input considered for feature identification, it is equal to the filter-size, **the size of the filter is hence, a hyper-parameter.**
> **KERNEL** : One channel in a filter
> **FILTER** : Combination of the 3 kernels used for the 3 different channels

The Receptive Field in ‘Fig 1’ is multiplied and summed with the filter, the given filter is able to identify the feature and hence we get a large value, but in case the filter is held against a receptive field that doesn’t contain the feature,

![Images Source — Google](https://cdn-images-1.medium.com/max/2000/1*4WSBStbo4VHb_hRD4icmSA.png)*Images Source — Google*

The filter when held over a different receptive field, gives a value of 0 or near zero, indicating the **absence of the feature** it represents in that image.

After every Convolution, operation followed by a few steps, the features become more and more undefinable, take a look,

![The Full Image Size(150 x 150)](https://cdn-images-1.medium.com/max/2000/1*_fzcpK_Alw3_zA16xSmw4g.png)*The Full Image Size(150 x 150)*
> **After 1 Convolution Operation,**

![](https://cdn-images-1.medium.com/max/2000/1*UcG4BAba4t6OIXx5cAQ8_Q.png)

It is kind of describable at this layer, now these are called feature maps and are not to be called images anymore.

Look how the feature size has reduced, this is due an operation called pooling. That is a intermediary step.
> **After 2 Operations,**

![](https://cdn-images-1.medium.com/max/2000/1*Zok87NjZpzCLaamOVoi03Q.png)

OKAY, things have gotten worse, now if I haven’t seen the initial image, I won’t be able to identify this as a image of buildings.
> **After 3 Operations,**

![](https://cdn-images-1.medium.com/max/2000/1*Kd0BEXUkAc587U6bYw2hLQ.png)

Its totally gone now, indescribable to human eyes, but these feature maps are further extracted to this state,

![](https://cdn-images-1.medium.com/max/2000/1*DIcCt2rWgzc1GnSlVKCJKA.png)

These are the features that will be detected or searched for by the filters of the CNN, these feature maps will be flattened and learnt by the fully connected layers later-on.

CNN’s were **designed by bio-mimicry of the mammalian visual cortex**, so **the next time you call yourself an idiot, remember, your idiocy isn’t a product of your marks or grades or ranks, it is a product of your own belief**. So, its time to start believing in yourself, now continue this article with this refreshing thought.

The filters are optimised by the Back propagation algorithm.

Filters can be applied on multiple channels too,

![Actual Representation of a Filter in a CNN, C = No. of channels and F = Kernel Size, defined by us. : Images Source — Google](https://cdn-images-1.medium.com/max/2000/1*ECr1NlqLymjiExU0Ue5J9g.png)*Actual Representation of a Filter in a CNN, C = No. of channels and F = Kernel Size, defined by us. : Images Source — Google*

You might have noticed that, filters reduce the image’s size, causing unwanted shrinking of the image, which **might also result in the loss of data in the boundaries of the image**.

![](https://cdn-images-1.medium.com/max/2000/1*aJTCU26VdtLQG3-_JX3M9Q.gif)

**In the first image, the padding is ‘valid’**, the other 3 images have a padding as ‘same’. The 3rd image being given a padding of 1, will be able to give rise to the image of the same size. Padding, simply refers to zeros being added to the edges of the image, along the rows and columns.

**Stride **: The number of pixels by which the filter moves after when performing each convolution operation is the stride.

![Images Source — Google](https://cdn-images-1.medium.com/max/2000/1*OZRaavOBf50uLEAk4Ae-1A.png)*Images Source — Google*
> **Pooling**

**Pooling** is done in order to** reduce the dimensions of the feature maps**, which ultimately ends up reducing the number of parameters in the model. The no. of parameters must be reduced if possible, in order to reduce computational pressure. This also allows the model to be **even more spatially invariant, since we are discarding any remaining spatial data**.

![Images Source — Google](https://cdn-images-1.medium.com/max/2000/1*u7f0kRKQnpDAbF_EWdFTCw.png)*Images Source — Google*

This operation is also done by moving kernels over the feature map.

![How stride affects the size of the output : Images Source — Google](https://cdn-images-1.medium.com/max/2000/1*lhiWMFM8tw4s-a2FOdn3RA.png)*How stride affects the size of the output : Images Source — Google*

**Max Pooling** selects the **brightest pixel**, and therefore **emphasising the sharp edges** in the images. It works well for images with a black or dark background, where there will be a sharp drop in the distribution of pixel values in the kernel.

**Average Pooling** outputs the average and **smooths out the image**, it is doesn’t do a great job in detecting sharp edges, but most of the image data is preserved, since nothing is eliminated and all values in the kernel are involved in the operation.
> **If we want to reduce dimensions anyway, why do we use padding?**

Simple, Pooling doesn’t cause as much data loss, it almost never. But, when dimensionality reduces by filters, the valuable data in the boundaries is lost, this is uncontrollable, without padding, whereas, **Pooling is controlled by us by addition and removal of pooling layers.**
> **Activation : ReLU (Rectified Linear Unit)**

**Why ReLU?**

![F(x) = max(0,x) : Images Source — Google](https://cdn-images-1.medium.com/max/2000/1*jOU3PnNiB0YIH1Y_t-iXng.png)*F(x) = max(0,x) : Images Source — Google*

The ReLU function completely **eliminates the possibility of negative values in the filters**. It **acts and looks like a linear function** when the input is above zero, but its **non-linearity is visible only when the input value is less than zero**.

This property of the ReLU unlike all other activation function makes it possible for the model to **learn complex relationships in the data**.

Networks that use the rectifier function for the hidden layers are referred to as rectified networks.

ReLU also is easy to code, and is **faster to implement** in Neural Networks, which implies, lesser computational requirements.

It has been found that rectifying non-linearity is the single most important factor in improving recognition accuracy of the model.

All this makes ReLU suitable for CNN’s.
> **Finally, the fully connected layers,**

![Images Source — Google](https://cdn-images-1.medium.com/max/2000/1*N8Drw_7X7OTSINgzhOydpw.png)*Images Source — Google*

The **Flatten layer is a simple process where the 2D matrix is converted to a 1D Matrix for giving it as an input for the Fully Connected layers.**

The Fully Connected Layer is just a normal Feed-Forward Neural network that gives as output a set of “n” probabilities for an input image being a part of one of “n” classes. We use a Soft-max Activation to achieve this.

![The Soft-max Activation Function : Images Source — Google](https://cdn-images-1.medium.com/max/2000/1*cbmtTZt2j-0cAfiwbb3GEQ.png)*The Soft-max Activation Function : Images Source — Google*

Thank You, your valuable feedback is definitely appreciated.

Remember never to stop having fun when creating new things : )
