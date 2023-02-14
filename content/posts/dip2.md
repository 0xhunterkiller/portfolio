---
title: Why Image Processing?
date: 2021-07-12
tags: [image-processing]
--- 

What in the world is it?

An image may be defined as a two-dimensional function f(x,y), where x and y are spatial blah blah blah…

Let’s not worry ourselves with the definition for now, but before that I believe nothing in this world should be given to someone, if they don’t know the essence of it. You first need to know the actual grace and history of this field, before you get into the nitty witty details. I am following a textbook alright.

**Digital image processing by Rafael C. Gonzalez, Richard E. Woods** to be precise. I am gonna be using it to make sure, I cover all the topics. The code however and many other examples may or may not be found in there.

The very first use of this system came about in the 1920’s in the Bartlane Cable picture transmission system. It used submarine cables to carry digitised newspaper images across the Atlantic, drastically reducing the time for moving images from New York to London, from weeks to hours. It served as a major nerve during that period. It perceived the image with 5 grey levels, they later increased to 15 grey levels.

![A photo transmitted with the help of Bartlane System](https://cdn-images-1.medium.com/max/2000/1*2xM8EoqevHz-Psun8sAoig.jpeg)*A photo transmitted with the help of Bartlane System*

It is all fun and games until the wars begin, right… the wars started, and eventually came to an end, and soon enough we were in the space era, mankind wanted to put as many satellites in space as possible. USSR and USA even had a space race going on. But, what is the use of satellites in the orbit, if the images they give you made absolutely no sense.

We can’t blame them, coz, a few clouds are enough to cause signal distortion, to make salt and pepper out of the images. Images had to be enhanced and for this we used DIP.

CAT & CT scans heavily rely of X-ray Imaging technology. They have been game-changers in the field of medicine and have been used to saves hundreds of lives. The inventor, Godfrey Hounsfield even received a Nobel Prize in Medicine for the invention.

Mankind had to wait till the 1960’s to put DIP in the common man’s hands. Computers were finally powerful but yet, cheap enough to allow common people to buy and use them.

Imaging in general can have various sources, like EM Waves, Ultrasonic, Electronic,etc. We’ll quickly look into all of em’.

![](https://cdn-images-1.medium.com/max/2000/1*QZrZckgGk7v3gOo4Xtiuqw.jpeg)

An EM wave in the EM Spectrum, short for Electro-magnetic wave, consists of photons, which are bundles of energy.

### Gamma Ray Imaging:

Gamma Rays have a super small wavelength, if you remember wavelength is inversely proportional to frequency and directly proportional to energy of the photon in the wave.

I do not suggest that you walk into a room filled with gamma-rays, since it is highly unlikely that you’ll walk out.

They are used in the field of nuclear medicine. The equipment is easily portable and is comparatively cheap, moreover the higher penetrating power of gamma-rays is useful, but the images produced are of poor quality and not sharp.

![Images produced via Gamma Ray Imaging](https://cdn-images-1.medium.com/max/2000/1*_tk-88J3n1RaHezM01NXhQ.gif)*Images produced via Gamma Ray Imaging*

### X-Ray Imaging:

X-rays are super cool, and I’m pretty sure you know how they are used for imaging, but, apart from the wide range of medical uses, like Mammography, Diagnostics and other treatments, they are used in airport scanners to check for dangerous items.

![Some random dude’s suitcase](https://cdn-images-1.medium.com/max/2000/1*JKkddWR9MKxv9JHqZ9iHcg.jpeg)*Some random dude’s suitcase*

### UV Imaging:

Photographs with a UV source has various uses, one important use is in criminal forensics, photographs taken with UV Source can reveal hidden bruises and scars, sometimes even long after visible healing has completed.

### Infrared Imaging:

Infrared (IR) imaging technology is used to measure the temperature of an object. All objects emit electromagnetic radiation, primarily in the **IR** wavelength, which cannot be seen by the naked eye. However, **IR** radiation can be felt as heat on one’s skin. The hotter the object, the more **IR** radiation it emits.

These thermal cameras are of great use and can save lives in events of natural disasters, where soldiers search for people who are alive by using these cameras. There are so many uses, like Conditional Monitoring, Night Vision, etc.

### Microwave Imaging:

Microwaves are amazing, they do really help in heating up your popcorn, but, let’s discuss images here,

On of the most profound uses of Microwaves in Imaging is for RADAR(Radio Detection and Ranging). Apart from being a concept that I hated during my physics lessons in school, it turned out to be one of the coolest concepts when I did some research for this story.

Microwaves have a large wavelength, hence have a lower energy and don’t scatter easily when they come into contact with dense fog or other distortion media.

They can withstand clouds, but can’t stand a chance against a single water droplet, and don’t get absorbed easily due to their low wavelength.

Microwave Radar is widely used for meteorologic mapping and weather forecasting. They are of great use in mapping terrains, detecting air-planes, ships and speeding motorists.

**Radio Waves** are used in MRI scans and are applicable in RADAR as well.

**Ultrasonic Imaging:**

This involves the use of sound, sound is bounced of the surface of an object and the attributes of the returning sound waves are used to create a map of the structure it bounced off of. It is used in searching for Oil and Gas fields under the ocean.

It is comparable to how, blind people train themselves in echolocation to get a mental picture of their surroundings.

Okay, so why do we need Image Processing? I gave a lots of cool looking examples alright, but, why do you need it?

One can use Image Processing for various purposes,

Converting a Image into its Digital form, in order to perform operations like enhancement, restoration, recognition, segmentation, feature extraction on it.

A person can also use DIP to extract a particular attribute from an image which maybe of use to him/her.

Apart from the above example, you might have noticed that I haven’t covered the field of visible light imaging. I haven’t done so, because the applications are too versatile for me to cover in one post, let aside one subheading. So, do give the 1st chapter of the mentioned book a read.

Now that I have discussed fairly well, the origins and the fields of uses of Digital Image Processing. It is finally time to tell you what a digital image is…

An Image maybe defined as a 2D function f(x,y), where x and y are spatial coordinates and the amplitude of f at any pair of coordinates is the intensity or the grey level at that point.

<iframe src="https://medium.com/media/03a8d7e3927c9f54a5c6ba60b1aab322" frameborder=0></iframe>

If x, y and f(x,y) are all finite quantities, then it is called a digital image.

Thank you, hoping to see you on my next post…
