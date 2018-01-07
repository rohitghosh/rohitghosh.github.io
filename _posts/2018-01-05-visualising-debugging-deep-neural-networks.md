---
layout: post
title: Visualizing and debugging deep convolutional networks
comments: true
excerpt: Have you been ever stuck while the neural network executes smoothly across epochs but the loss doesn't decrease ? Or may be the loss decreases but not the way you would like it to ? Debugging a deep neural network is helpful if not essential for a lot of use cases.
---
Have you been ever stuck while the neural network executes smoothly across epochs but the loss doesn't decrease ? Or may be the loss decreases but not the way you would like it to ? Debugging a deep neural network is helpful if not essential for a lot of use cases.

If you want to know why building a visualisation algo is important, especially in radiology - you can have a read [here](http://www.towards.ai/building-trustable-ai/)

In this series of posts we describe the different visualization techniques for explaining decisions of convolutional neural nets. These posts are a summary of the different techniques that existed in research, starting all the way back from deconvolution based attribution systems in 2013.

The visualization technique posts are divided into 2 parts:

- In [Part 1](http://blog.qure.ai/notes/visualizing_deep_learning) we talk about perturbation based methods which includes - Occlusion, LIME & Integrated Gradients

- In [Part 2](http://blog.qure.ai/notes/deep-learning-visualization-gradient-based-methods) we talk about back propagation based methods. They are again divided into gradient based back propagation (Deconvolution, Guided backpropagation, GradCAM) & relevance score based (LRP, DeepLIFT)
