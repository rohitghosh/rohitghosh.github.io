---
layout: post
title: Deep learning for finance - deep portfolios
arxiv_link: https://www.google.co.in/search?q=Deep+learning+for+finance%3A+deep+portfolios
pid: deep_portfolio
comments: true
authors: J. B. Heaton, N. G. Polson, and J. H. Witte
---
In this paper, the authors discuss deep learning based methods for portfolio selection and optimisation. There are 2 objectives of deep learning - selecting the right constituents of the index and choosing their corresponding weights in the portfolio so as to achieve a specific objective. The objective could be something like -  outperform a specified index (in this case IBB Index) by a pre-defined margin (in this case 1%) over an year with least number of stocks possible.


#### Choosing stock basket

The idea behind choosing a stock basket is to keep minimum number of stocks and yet be able to mimic requisite performance.For this purpose, weekly returns of all the components of the index are predicted using auto-encoders (AE).

AEs are just a 2 layer neural nets in their simplest form, which is trained to predict the input itself. So if an input has 100 dimension, the fist layer would consist of say 5 nodes and the second and final layer consists of again 100 nodes.If trained perfectly, they would be able to represent a 100 dimension vector effectively in a 5 dimension vector space. The training error for AE task here is chosen as L2 loss between input and predicted output (the auto-encoded part).

Here's a figure explaining AEs

![](http://imgur.com/dYxIxUQ.png)

After AE is performed the components are ordered in order of their L2 loss. The component with minimum L2 loss has the most similarity to the rest of the components. This is because the 5 dimension representation of the AE could effectively capture the signature of that particular component leading to a lower L2 loss. For choosing purposes 3 subsets of the component were proposed in the paper - in the form of 10+X components where X can be 15, 35, 55. This structure implies 10  components with most communal information (having least L2 losses) are chosen along with X number of components with highest L2 loss. The idea being limiting redundant similar components to 10, and choosing the most non-similar components thereafter

##### Choosing weights of selected components

Herein the authors use the selected components and train a normal 2 layer network with ReLU activations for predicting returns of the index. For the purpose of choosing weights such that the basket outperforms the index , the returns of the index less than 5% were replaced by 5% - ensuring anti-correlation in periods of drawdowns.

Here's a pictorial representation of the process - indicating the 4 phases

1. AE for component selection
2. Calibration for weight selection (the pic represents the case where returns of index are predicted as it is without the drawdown manipulation) for all 3 subsets
3. Validating the performance of the 3 subsets against index
4. Choosing the final model

![](http://imgur.com/tRDV5vp.png)

A central observation to the application in a finance setting is that univariate activation functions can frequently be interpreted as compositions of financial put and call options on linear combinations of the input assets. As such, the deep feature abstractions implicit in a deep learning routine become deep portfolios, and are investible – which gives rise to a deep portfolio theory.
