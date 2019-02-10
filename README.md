# Generative Adversarial Networks

## Introduction
In this lecture I have summarized a presentation about Generative Adversarial Networks (GANs) written by Dr. Ian Goodfellow. The original presentation can be found [here](/files/generative_adversarial_networks.pdf)

## Overview
Take a look at the following three birds:

![](/files/slide02_2.png), ![](/files/slide02_1.png), ![](/files/slide02_3.png)

Which one of them is exceptional?

The left picture is exceptional. But why?

The answer is that there is not such bird in the animal kingdom. No photographer whet to the jungles and took this picture. It is a product of a special generative algorithm called GAN.

But, what is a Generative model?

## Generative Models
A generative model can be illustrated by the following toy example:

Given the following 3 dimensional color space

![](/files/slide05.png)

Given 50 pixels in this color space, all of them are some kind of gray (or similar color). Your task is to generate a new pixel, which is similar to the given 50 gray pixels. How would you do that?

Say, you can put all these pixels in the color space. Since they are all similar to each other, it is reasonable to assume that they will be put close to each other.

![](/files/slide06.png)

If we will be able to define mathematically the gray area, as accurate as possible, than we will be able to generate more and more pixels which are similar to the 50 given once. Mathematically, we are talking about a density function, which can tell us where in the color space these pixels are concentrated.
When talking about 50 pixels, we are talking about 50 3-dimensional vectors, which are placed in a three dimensional space. When talking about pictures, the idea is the same, but each picture is represented by a high-dimensional vector, which is put in a high-dimensional space. For example, a 32X32 gray picture can be viewed as a 1024-dimensions vector.
Therefore, given 50 32X32 pictures of faces, and putting them in a 1024-dimensional space, by calculating the density function of these pictures inside this space, we will be able to generate more and more picture of faces, which were not given before.

### Generative Models - Why?
The question is why do we need generative models? why it is so important? It looks like the Internet is full of pictures, why do we need to create more?

There are several reasons for our interest in generative models:
- Generative models are excellent test of our ability to represent and manipulate high-dimensional probability distributions. High-dimensional probability distributions are important objects in math and engineering domains.
- Using generative models which are based on time-series of data, we can simulate several possible futures, for a given situation. Using such models it is possible to train an agent to select the best possible action for a given situation, after examining several possible futures.
- Generative models and especially GAN, can provide predictions on input with missing data. Modern models of supervised learning often requires large amount of data, which is usually hard to achieve. Generative models can be used to produce good result even if part (or even most) of the data is missing. This approach is called semi-supervised learning.
- For many tasks, there are several possible solutions all are acceptable. Traditional algorithms uses Mean Square Error (MSE) since they are not able to learn from a model when there is more than a single correct answer. For example, a model which needs to predict the next frame of the below picture. In this example we try to predict the next frame of a 3D rotating head. 
  - We use the left picture as the "ground truth" - or at least one of the "correct" results for reference.
  - The middle picture is an example for the MSE solution, in which the algorithm average all possible correct solutions. In this result we see that the eye and the ear of the head are blurred, since in every possible correct solution the location of the ear is different, so the average is actually erase the ear from the picture.
  - The right picture is a result of GAN
  
  ![](/files/slide08.png)
  
- In some cases we are required to create realistic images from the same distributions as the input picture. For example in "Single image super-resolution" we are required to create a high-resolution image from a low-resolution image. In fact, we are required to add information to the image which is not there in the first place. This is illustrated in the below picture:
  - The left picture is the "original" picture in high-resolution. This picture is down-sampled, in order to lower its resolution, and use various algorithms to reconstruct the original image.
  - Bicubic is a simple interpolation which just expand the image. No sophisticated statistic method was used.
  - SRResNet is the output of a deep neural network which uses the MSE.
  - SRGAN is the output of a GAN network, which uses the pixel distribution of the low-resolution image to reconstruct the original picture.
  
  ![](/files/slide09.png)
  
- Realistic generation tasks:

  [![](/files/slide10.png)](https://youtu.be/9c4z6YsBGQ0 "Generative Visual Manipulation on the Natural Image Manifold")

- Text to image translation:
  ![](/files/slide11.png)
  
- Image to image translation:
  ![](/files/slide12.png)
  
  
## How do generative models work?
Generative model is a type of Unsupervised Learning. One can think about generative models as the opposite of discriminative model. For example: discriminative model classifies an email as "Spam" or "not-Spam" based on statistic modeling of words. While generative model asks the opposite question: how can the algorithm generate an email which will look like a "Spam"? 

 

