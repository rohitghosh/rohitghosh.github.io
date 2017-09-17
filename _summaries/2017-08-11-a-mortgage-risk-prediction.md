---
layout: post
title: Deep Learning for Mortgage Risk
arxiv_link: https://arxiv.org/abs/1607.02470
pid: mortgage-risk-dl
comments: true
authors: Justin A. Sirignano, Apaar Sadhwani, and Kay Giesecke
---
In this paper, the authors explore usage of ensemble of deep neural networks for predicting the possibility of one of the many mortgage states - current, 30 days past due, 60 days past due, 90+ days past due, foreclosure, REO (real estate owned), and paid off using dataset of 25 million subprime and 93 million prime mortgages.

There are few notable differences from any previous work on mortgage pricing and state prediction:

1. For the first time, so many discrete states of mortgage were considered, most of the previous work involved default or prepayment. The granularity of the data in terms of labels is important since the transitions across states is an important metric to monitor over a long time horizon

2. The granularity and size of features is also unprecedented in the study. The broad set of risk factors describing borrower, product, and performance characteristics, as well as local and national economic conditions were not studied in collection before this.

3. This is the first time deep learning was used in a mortgage risk prediction setup wherein deep neural nets were trained. The most important reason for successful training was the huge amount of data the authors had used for their studies.

#### Method

The networks are trained on 294 features on a 1-month period data predicting the conditional probability of the mortgage state at the end of the month given the features at start of month.  Of the 294 explanatory variables, 233 are loanlevel
feature and performance variables, 25 are indicators for missing features, and 36 are economic variables. The entire ensemble of 8 neural nets with 5 hidden layers is trained on cloud over roughly 3.5 billion samples.


#### Prediction

For prediction, there are 2 implementations that have been explored.

- The dynamic model gives transition probabilities between the states for 1-month ahead transitions. The transition probability matrix for t-months (2 month, 6 month, 1 year, etc.) ahead is simply the expectation of the product of the transition probability matrices at months 0, 1, . . . , t − 1. However for the subsequent predictions, a time series of Monte Carlo simulations of the features needs to be computed starting from initial t=0.

- An alternate assumption, which is advantageous for reducing the computational burden and can be accurate for shorter time horizons, is that the economic covariates in X<sub>t</sub> are frozen at t = 0. That is, only the state of the mortgage and deterministic elements of X<sub>t</sub> (e.g., the balance of a fixed rate mortgage and time to maturity) are allowed to evolve over time. Then, the transition probability matrix for a horizon t > 1 is the product of the deterministic transition probability matrices at months 0, 1, . . . , t − 1

##### Results

An investor desires a loan portfolio with uninterrupted cashflow. Delinquency often produces a loss of cashflow while prepayments lead to early cashflows that might have to be reinvested at lower interest rates. Uninterrupted cashflows require loans which are both unlikely to be delinquent and unlikely to prepay. This is equivalent to a portfolio of loans which are
highly likely to remain current. An example is a bank which originates loans and retains some loans on their balance sheet. Another example is an investment fund or structurer who constructs a loan portfolio. Given an available pool of loans to select a portfolio from, an investor can rank those loans by the likelihood that they remain current according to their
model of choice.For a portfolio of size N, the investor will choose the N loans with the highest probabilities of remaining current.

The deep learning model’s area under the ROC curve (AUC) is over 10% greater than the logistic regression’s AUC
for predicting transitions to paid off. The deep learning model’s superior accuracy directly translates into improved profit and loss for an investor or lender. Portfolios constructed using the deep learning model outperform portfolios chosen via the logistic regression model, with a 50% reduction in prepayments over a 1 year out-of-sample period. The neural network
portfolio has a 46% smaller loss than the logistic regression portfolio at a 1 year time horizon.
