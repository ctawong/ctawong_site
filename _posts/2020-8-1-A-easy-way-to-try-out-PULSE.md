---
title: An easy way to try out the PULSE algorithm
layout: post
categories: machine_learning
permalink: articles/pulse.html
excerpt: PULSE is an algorithm for creating 
author: Andrew Wong
---

[![](https://camo.githubusercontent.com/52feade06f2fecbf006889a904d221e6a730c194/68747470733a2f2f636f6c61622e72657365617263682e676f6f676c652e636f6d2f6173736574732f636f6c61622d62616467652e737667)](https://colab.research.google.com/github/ctawong/PULSE_from_image_url/blob/master/PULSE_URL.ipynb)


PULSE (Photo Upsampling via Latent Space Exploration) is a new [algorithm](https://arxiv.org/abs/2003.03808) published in 2020 that generates a high resolution facial image from a low resolution one. The main idea is to encode a low resolution image to a latent variable with [GAN](https://en.wikipedia.org/wiki/Generative_adversarial_network), change the latent variable a little bit, and generate a new but highly similar image.

To make it easy for anyone to try out PULSE, I wrote a [COLAB notebook](https://colab.research.google.com/github/ctawong/PULSE_from_image_url/blob/master/PULSE_URL.ipynb) that takes an image URL (such as those obtained from Google image search), perform downsampling, and then upsampling with PULSE. 

Instruction to run

1. Open the [COLAB notebook](https://colab.research.google.com/github/ctawong/PULSE_from_image_url/blob/master/PULSE_URL.ipynb)
2. Click "Connect" button on top right to connect to the GPU server.
3. Replace Photo_URL with an URL of your interest
4. Click the play button on the left of the second cell.

It usually takes a minute or two to generate a new image.

Below are a few examples
