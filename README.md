# Generative Adversarial Networks

## Introduction
In this lecture I have sammerized a presentation about Generative Adversarial Networks (GANs) written by Dr. Ian Goodfellow. The original presentation can be found [here](/files/generative_adversarial_networks.pdf)

## Overview
Take a look at the following three birds:

![](/files/bird2.png), ![](/files/bird1.png), ![](/files/bird3.png)

Which one of them is exceptional?

The left picture is exceptional. But why?

The answer is that there is not such bird in the animal kingdom. No photographer when to the Amazonas Jungles and took this picture. It is a product of a special generative algorithm called GAN.

But, what is a Generative model?

## Generative Models
We will illustrate what is a generative model by the following toy example:

Given the following 3 dimentional color space

![](/files/color_space.png)

Say, that there are 50 pixels in this color space, all of them are some kind of gray (or similar color). Your task is to generate a new pixel, which is similar to the given 50 gray pixels. How would you do that?

Say, you can put all these pixels in the color space. Since thay are all similar to each other, it is reasonable to assume that they will be put close to each other.

![](/files/color_space_gray.png)

If we will be able to define mathematically the gray area, as accurate as possible, than we will be able to generate more and more pixels which are similar to the 50 given once. Mathematically, we are talking about a density function, which can tell us where in the color space these pixels are concentrated.
When talking about 50 pixels, we are talking about 50 3-dimentional vectors, which are places in a three dimensional space. When talking about pictures, the idea is the same, but each picture is represented by a high-dimensional vector, which is put in a high-dimensional space. For example, a 32X32 gray picture can be viewed as a 1024-dimentions vector.
Therefore, given 50 32X32 pictures of faces, and putting them in a 1024-dimentional space, by calculating the density function of these pictures inside this space, we will be able to generate more and more picture of faces, which were not given before.
