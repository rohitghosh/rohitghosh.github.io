---
layout: post
title: Deep Direct Reinforcement Learning for Financial Signal Representation and Trading
arxiv_link: https://google.com/search?q=Deep+Direct+Reinforcement+Learning+for+Financial+Signal+Representation+and+Trading.
comments: true
authors: Yue Deng, Feng Bao, Youyong Kong, Zhiquan Ren, and Qionghai Dai, Senior Member, IEEE
---
In this paper, authors demonstrate the training of an effective RL based algorithm with following novel contributions
- Using actor-based RL framework instead of typical value-based learning methods, defining market states as a continuous spectrum rather than discretized form of value-based methods.
- Using a continuous and differentiable objective function that takes care of practical costs like brokerage and slippage
- Usage of fuzzy representation to account for market uncertainties
- Novel way of initialization of multiple parts of the net to facilitate convergence
- Using skip connections in BPTT to avoid gradient vanishing

#### RL framework

Conventional value-function based RL frameworks assume discrete state space. Also, in typical Q-learning, the definition of value function always involves a term recoding the future discounted returns. The nature of trading requires to count the profits in an online manner - meaning taking the best possible decision based on current state. Thus, an actor-based RL framework would be predicting action to be taken instead of learning the underlying value function.

This sort of framework can be built using RNN and a differentiable objective function. Also, the actor based framework means each action taken would in turn be affected by a memory of action history in recent past - preventing the system to enter into too many trades causing brokerage and slippage losses.

If p<sub>1</sub>, p<sub>2</sub>,..., p<sub>t</sub>,... as the price sequences released from the exchange center. Then, the return at time point t is easily determined by z<sub>t</sub> = p<sub>t</sub> − p<sub>t−1</sub> . Based on the current market conditions, the real-time trading
decision (policy) δ<sub>t</sub> ∈ {long, neutral,short}={1, 0, −1} is made on each time point t. With the symbols defined above, the profit R<sub>t</sub> made by the trading model is obtained by

![](http://imgur.com/kVJp6sl.png)

The objective function for training could simply be total return
![](http://imgur.com/yDbeubZ.png)

Else, the risk adjusted returns as given by Sharpe ratio can also be used for even better returns.

Improvising on the existing models of DRL, the authors focus on using feature learning instead of sparse encoding of inputs for more robust learning. So the model incorporates 4 hidden layers to learn the features which are then fed to the RNN as input.


Also, the authors included fuzzy representation of inputs to account for market uncertainties. The model takes in 3 fold fuzzy Gaussian representations.


#### Training & Initialization

###### Input

50 element long vector - the last 45 min returns and momentum change to the previous 3 h, 5 h, 1 day, 3 days, and 10 days - is used as input to FDDR. This input is transformed to 150 element vector using 3 fold fuzzy representation. The 150 element vector is passed through 4 hidden layers with 128, 128, 128, and 20 hidden nodes per layer. The 20 element vector finally obtained is trained using RNN and objective function defined above.

###### Output

The output could be any of the 3 δ<sub>t</sub> values which would be a function of RNN weights, feature representation of fuzzy input and last action i.e. δ<sub>t-1</sub>
![](http://imgur.com/zz8gGxo.png)

###### Fuzzy initialization

The fuzzy representations requires 3 means and sigmas for each dimension of 50 dimensions. For the same, the data is clustered into 3 clusters using k-means, and the mean and sigma of respective dimension of 3 clusters provide for good initialization of fuzzy representations

###### Hidden layer weight initialization

The hidden layer initialization follows from an old technique of initializing a DNN with encoder weights of an AE (AutoEncoder).

##### Evaluation

The FDDR model is trained on 15000 data points and tested on 5000 data points from each of  the 3 instruments separately - China Shanghai Shenzhen 300 Stock Index Futures (IF) , silver (AG) and sugar (SU) contracts from commodity markets.

The FDDR and other models trained with both total profits (TP) and Sharpe Ratio (SR) as objective functions. The performance looks like this as compared to DRL (deep reinforcement learning - actor based), SCOT (sparse coding-inspired optimal training), DDR (deep direct reinforcement learning), FDDR (fuzzy DDR)
![](http://i.imgur.com/aKeXmhv.png)

Also, the performances of market price prediction based DL methods (methods which predict if pries will go up, down or remain stationary) were compared. It's to be noted that such system performs better than FDDR when there are no transaction costs (like brokerage and slippage involved) but with inclusion of such costs, FDDR seems to be performing even better.

![](http://imgur.com/I4SQzZz.png)
