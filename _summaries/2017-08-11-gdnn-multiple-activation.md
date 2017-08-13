---
layout: post
title: Genetic Deep Neural Networks Using Different Activation Functions for Financial Data Mining
arxiv_link: https://arxiv.org/abs/1706.10059
comments: true
authors: Luna M. Zhang
---
In this paper, the authors discuss a evolution based learning and parameter optimization strategy for neural nets used for predicting market prices of DJIA and 30Y Treasury Constant Maturity Rate

#### Evolution strategy

The author tries evolution based learning strategy instead of traditional back-propagation strategy to optimize the cost function of the neural nets.

In normal DNNs, the weights for each connection is optimized through multiple epochs. GDNNs (Genetically evolved DNNs) are similar to DNNs in their design, except GDNNs designed so as the neurons in each layer have same activation function but the activation function can be either of the 3 - unipolar sigmoid, bipolar sigmoid, tanh. In DNNs, normally the activation function remains the same across neuron but in lieu of the specific design of GDNNs, the activation function type as well as the weights are optimized for each connection.

#### Training

The fitness function for the evolution is defined as the negative of MSE. The exact mechanism of crossover during mutation hasn't been defined explicitly in the paper. As per general evolution mechanism, the best performing GDNNs are chosen for cross-over to produce offsprings for next generation.

##### Results

The results show that the best performance is obtained for fewer hidden layers (likely due to overfitting in larger networks). The evolution strategy helps to improve the performance of networks with multiple activation across different layers as compared to same activations in each layer.
