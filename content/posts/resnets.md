---
title: Residual Networks
date: 2021-08-13
tags: [deep-learning]
---

Deep Convolutional Networks are said to prevail over Wider Networks during performance, but, these networks are difficult to train. Image Classification and Image Recognition tasks have benefited greatly from deeper networks.

### **Convergence :**

A Model is said to have been converged, when additional training will not improve the accuracy of the model.

![Illustration of Convergence in a model.](https://cdn-images-1.medium.com/max/2000/1*OREMxrB-OMazJ1pWrRCAEw.png)*Illustration of Convergence in a model.*

**Vanishing Gradient : **During Back-propagation, the derivative of the error function with respect to the weights have to be calculated, what if this **derivative is too small**, and then we apply the chain rule. All these small derivatives, contribute to the final value of the gradient making it extremely tiny.

![](https://cdn-images-1.medium.com/max/2000/1*eaLj6Nv8QzTzhFC3rsRunw.png)

So, when we take a step according to the magnitude of this resulting gradient, it is a very small step and the model almost never converges.

![Sigmoid(Left) — Derivative of Sigmoid(Right)](https://cdn-images-1.medium.com/max/2000/1*Ko236Kck7NakGtMZIxgLxQ.png)*Sigmoid(Left) — Derivative of Sigmoid(Right)*

So, from this we get to know that the sigmoid activation’s derivative becomes super small. Making the gradient small, ultimately. In short networks, this problem isn’t that prevalent, but in deep ones, it is.

![](https://cdn-images-1.medium.com/max/2000/1*XCTh18yWso3MZ6DRL0LspQ.png)

When the Derivative w.r.t Weight becomes too small during back propagation in the initial layers, the update on the Weight in turn becomes small too. As a result of this “Vanishing Gradient”, the Initial layers of the model, train too slowly or stay the same. This makes it difficult for the model to converge.

**Solution : **Batch Normalization, it is making sure that the input to the activation function is always such that, the derivative doesn’t become too small.

![](https://cdn-images-1.medium.com/max/2000/1*xKiWSgqFatIf1ARb8CHwqQ.png)

This however can only be used to an extent. There seemed to be a limit as to the number of layers you can stack onto a network before facing the vanishing gradient problem.

**ReLU** for activation is another method we can use to help solve the vanishing gradient problem.

Now, another problem is degradation or saturation of accuracy over increasing the number of layers. This degradation is not being caused by over fitting, since the training error also increases. Then, what is causing this degradation?

![See how the training error for the 56 layer network is also lower that that of the 20 layer one. This degradation is hence not being caused by over fitting.](https://cdn-images-1.medium.com/max/2000/1*xaDYH0ZqRLMlbmOa18Uq-Q.png)*See how the training error for the 56 layer network is also lower that that of the 20 layer one. This degradation is hence not being caused by over fitting.*

To investigate this further, they **constructed** a deep model and compared it with its shallower counter part.

### The Experiment :

They added layers of identity mapping and copied the other layers from the shallow model to construct the deeper network.

![](https://cdn-images-1.medium.com/max/2002/1*rSxE4joRXKbPH3cyauTBiw.png)

So, this network will essentially learn the same function as the shallow model, the extra layers being, just identity mappings.

This constructed model gave training errors no higher than its shallower counterpart.

Then why isn’t it easy for a deeper model, completely trained(not constructed), to just learn the identity mapping and give us an output, that is not better, but not worse either.

When tested a fully trained model(of the same dimensions), gave a less accurate output compared to the constructed one.

It seems that learning the identity function is just as hard as learning any other function for a model. So, to get a way around this we made residual networks.

### Residual Connections :

![Residual Connection](https://cdn-images-1.medium.com/max/2000/1*ik_QI92uXPiA_Bg_kSAWQQ.png)*Residual Connection*

The above block is called a Residual Block, or just give it any fancy name you want, but the important part is what it does.

Lets say, you want the model or particular set of layers to learn the function H(x),

Well what can we do? Just sit and hope the model learns the function, or you go about making it learn. How though?

![](https://cdn-images-1.medium.com/max/2000/1*ip8dLQI0pzV9U2HSdcleFQ.png)

So, we just gotta make F(x) zero to get a identity mapping, and **hypothesize that it is now easier to fit F(x)**.

Adding, these shortcut connections don’t add any extra parameters or any extra complexity to the model. Actually shortcut connections had been used for a long time before even the existence of this paper, to address the vanishing/exploding gradient issue and in [highway networks](https://en.wikipedia.org/wiki/Highway_network), where they were used with gating-functions.

Highway Networks were just another attempt to increase the model depth, but haven’t been very successful at it.

![Structure of a Highway Network](https://cdn-images-1.medium.com/max/2000/1*z7EUvoSsgWaAoG34C6WAZQ.png)*Structure of a Highway Network*

Residual Representations, have been used in CG and Low-Level Vision tasks to **solve Partial Differential Equations and in Image Recognition operations**.

### Woah, how is it magically easier to fit the residual function F(x)?

I will try explaining this part, but the paper explains it super well, I encourage you all to read it.

So remember when we constructed a deeper model, this model can approximate the function that can be approximated by a shallower counter-part, along with identity mappings that make it deep.

Now this is where it gets interesting, remember how we face a degradation problem because it not easy to make multiple non-linear layers learn the identity mapping.

If we make the residual learning reformulation, we’ll end up giving it **x** and tell it to learn a function such that the the output will be **x.**

To be precise, the multiple non-linear layers will simply b**e driven to learn the zero function or its approximate as the residual function F(x), if it is optimal, that is the error if H(x) were a identity mapping is lesser than in any other case.**

This way we are sort of preconditioning the multiple non-linear layers to approximate the function, which is better than learning it own your own.

![H(x) = Identity Mapping](https://cdn-images-1.medium.com/max/2000/1*ttchyjCPfDa_s9FTt4tArQ.png)*H(x) = Identity Mapping*

Why should the multiple non-linear layers learn the zero function, because remember we want the layers to learn F(x), not H(x), and then we add **x **to the result and get H(x).

![And there you go, we have the identity mapping in place](https://cdn-images-1.medium.com/max/2000/1*veBqoClo_yzWi9rebIZ5Bg.png)*And there you go, we have the identity mapping in place*

In real world scenarios, there might be other functions that are optimal, not just the identity function, for example if the zero function is found to be more optimal, the multiple non-linear layers will find it easier to find ways to deviate from the identity mapping in order to get a zero function, rather than learning it entirely on its own.

![](https://cdn-images-1.medium.com/max/2000/1*yBi3O8_hnH4_Po_B-Pntmw.jpeg)
> Well, philosophically speaking, humans need such guides to help them achieve, but, sadly not a lot get such guidance.

### The Math :

Now, the math, the researchers have adopted the strategy of applying residual learning to every few stacked layers.

![](https://cdn-images-1.medium.com/max/2000/1*FYQRvcGF1LvQYNu0GlC98Q.png)

This is the ReLU activation function, can you find out why it handles the vanishing gradient problem, better than Sigmoid?

![](https://cdn-images-1.medium.com/max/2000/1*njuH4XVXf-l9pR_RorUOrA.png)

### Comparison between, VGG Nets, Plain Networks and ResNets :

![](https://cdn-images-1.medium.com/max/2000/1*xSIe60SVNRXsTu-6p5tgRA.png)

The ResNet model has comparably lower complexity and fewer filters compared to the VGG Nets. It has 3.6 Billion Floating Point Operations, which is only 18% of VGG Nets which has a whopping 19.6 Billion Floating Point Operations. The Plain Network has 3.6 Billion FLOPs too, but is less accurate.

### Legacy

ResNets were used in the ImageNet competition, where they trained on 1.28 Million training images, and evaluated on 50k validation images. They were tested on 100K test images and were reportedly having the top-1and top-5 error rates. *It also achieved 1st place in ILSVCRC 2015.*

The ResNet-1202 was able to overfit the CIFAR10 dataset, and yes 1202 means 1202 layers!! Take a moment to thank ResNets for making it possible.

The Paper came out in 2015, I looked up **Deep Learning** on **Google Trends,**

![](https://cdn-images-1.medium.com/max/2300/1*iXEXbf1TPbGYrc8fFtvjGg.png)

I would say that it was either perfectly timed or it was the key factor in popularizing Deep Learning.

### References :
> [The ResNet Paper](https://arxiv.org/abs/1512.03385)
> [Batch Normalization](https://towardsdatascience.com/batch-normalization-the-greatest-breakthrough-in-deep-learning-77e64909d81d)

Please excuse me if there are any flaws, and do correct me.

Thank you for reading.
