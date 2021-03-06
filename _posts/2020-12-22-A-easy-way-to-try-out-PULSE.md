---
layout: post
title: An easy way to try out the PULSE algorithm
categories: machine_learning, project
permalink: articles/pulse.html
excerpt: PULSE is an algorithm for creating high resolution facial images
icon: /assets/pulse.png
author: Andrew Wong
comments: true
---

[![](https://camo.githubusercontent.com/52feade06f2fecbf006889a904d221e6a730c194/68747470733a2f2f636f6c61622e72657365617263682e676f6f676c652e636f6d2f6173736574732f636f6c61622d62616467652e737667)](https://colab.research.google.com/github/ctawong/PULSE_from_image_url/blob/master/PULSE_URL.ipynb)

[Github link](https://github.com/ctawong/PULSE_from_image_url)

PULSE (Photo Upsampling via Latent Space Exploration) is a new [algorithm](https://arxiv.org/abs/2003.03808) published in 2020 that generates a high resolution facial image from a low resolution one. The main idea is to encode a low resolution image to a latent variable with [GAN](https://en.wikipedia.org/wiki/Generative_adversarial_network), change the latent variable a little bit, and generate a new but highly similar image.

To make it easier for anyone to try out PULSE, I wrote a [COLAB notebook](https://colab.research.google.com/github/ctawong/PULSE_from_image_url/blob/master/PULSE_URL.ipynb) that takes an image URL (such as those obtained from Google image search), performs downsampling, and then upsampling with PULSE. 

Instruction to run

1. Open the [COLAB notebook](https://colab.research.google.com/github/ctawong/PULSE_from_image_url/blob/master/PULSE_URL.ipynb)
2. Click "Connect" button on top right to connect to the GPU server.
3. Replace Photo_URL with an URL of your interest
4. Click the play button on the left of the second cell.

It usually takes a minute or two to generate a new image.

Below are a few examples. Image on the left is the original, middle one is the downsampled original, and the right one is the image generated by PULSE.

![](/assets/uploads/pulse1.png)

![](/assets/uploads/pulse2.png)

Pretty good! You may think. Things go a bit haywire with some images...

![](/assets/uploads/pulse3.png)

![](/assets/uploads/pulse4.png)

![](/assets/uploads/pulse5.png)

![](/assets/uploads/pulse_senior1.png)

![](/assets/uploads/pulse_senior2.png)

As you can see, the generator is biased towards white young-looking adults. In fact there have been a lot of discussion around bias implicit in machine learning models. To sum up, it's all about the training data. The models simply fill in the gap based on what they saw from the training data. The PULSE model was trained with the a [dataset of Flickr images](https://github.com/NVlabs/ffhq-dataset) and inherited all its bias. The bias issue can likely be resolved by carefully selecting a dataset with diverse age, ethnicity and gender.