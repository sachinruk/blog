---
layout: post
title: "Deep Learning Quantile Regression -  Keras"
modified:
categories: blog
excerpt: Simple code to do quantile regression with Keras
tags: [Keras]
image:
  feature:
date: 2016-10-16
share: true
ads: true
---

The loss function is simple as doing the following. Which is simply the pin-ball loss function.

```python
def tilted_loss(q,y,f):
    e = (y-f)
    return K.mean(K.maximum(q*e, (q-1)*e), axis=-1)
```

When it comes to compiling the neural network, just simply do:

```python
model.compile(loss=lambda y,f: tilted_loss(0.5,y,f), optimizer='adagrad')
```

I chose 0.5 which is the median, but you can try whichever quantile that you are after. Word of caution, which applies to any quantile regression method; you may find that the quantile output might be extreme/ unexpected when you take extreme quantiles (eg. 0.001 or 0.999).

A more complete working example can be found [here](https://github.com/sachinruk/KerasQuantileModel/blob/master/Keras%20Quantile%20Model.ipynb).
