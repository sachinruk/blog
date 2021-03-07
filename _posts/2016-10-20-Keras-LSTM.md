---
layout: post
title: "Keras LSTMs"
modified:
categories: blog
excerpt: How to Use LSTMs and stateful LSTMs
tags: [Machine Learning, Keras]
image:
  feature:
date: 2016-10-20
share: true
ads: true
---

Keras has been one of the really powerful Deep Learning libraries that allow you to have a Deep Net running in a few lines of codes. Best part, don't worry about the math. In the following videos you will find how to implement a popular Recursive Neural Net (RNN) called Long Short Term Memory RNNs (LSTM).

Note: You could easily replace the LSTM units with Gated Recurrent Units (GRU) with the same function call.

Source code: https://github.com/sachinruk/PyData_Keras_Talk/blob/master/cosine_LSTM.ipynb

<iframe width="560" height="315" src="https://www.youtube.com/embed/ywinX5wgdEU" frameborder="0" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/e1pEIYVOtqc" frameborder="0" allowfullscreen></iframe>

### FAQ:
1. Why do we need a Dense Layer?
The output is still one dimensional (y) and therefore the 32 hidden layers need to be projected down to one. Hence the dense layer is used.
2. How do you decide number of layers and number of nodes in each layer?
Personally for me this is trial and error. Generally larger number of layers (deeper) is better than going wide (more nodes). But I usually limit myself to 5 at most unless there is a truly large dataset (100MB+)

### References
1. To understand the maths behind LSTM:
http://colah.github.io/posts/2015-08-Understanding-LSTMs/
2. For another guide to Keras LSTMs:
http://machinelearningmastery.com/time-series-prediction-lstm-recurrent-neural-networks-python-keras/
3. If you are still confused (try my stackoverflow post):
http://stackoverflow.com/questions/38714959/understanding-keras-lstms
