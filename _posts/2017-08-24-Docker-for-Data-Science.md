---
layout: post
title: "Docker for Data Science"
modified:
categories: blog
excerpt: Simplifying the Installation Process.
tags: [Data Science, Docker]
image:
  feature:
date: 2017-08-24
share: true
ads: true
---
# Docker for Data Science

Docker is a tool that simplifies the installation process for software engineers. Coming from a statistics background I used to care very little about how to install software and would occasionally spend a few days trying to resolve system configuration issues. Enter the god-send Docker almighty.

Think of Docker as a light virtual machine (I apologise to the Docker gurus for using that term). Its **underlying philosophy is that if it works on my machine it will work on yours**.

## What's in it for Data Scientists
1. Time: The amount of time that you save on not installing packages in itself makes this framework worth it.
2. **Reproducible Research**: I think of Docker as akin to setting the seed in a report. This makes sure that the analysis that you are generating will run on any other analysts machine.

## How Does it Work?
Docker employs the concept of (reusable) layers. So whatever line that you write inside the `Dockerfile` is considered a layer. For example you would usually start with:
```Dockerfile
FROM ubuntu
RUN apt-get install python3
```
This Dockerfile would install `python3` (as a layer) on top of the `Ubuntu` layer.

What you essentially do is for each project you write all the `apt-get install`, `pip install` etc. commands into your Dockerfile instead of executing it locally.

I recommend reading the tutorial on https://docs.docker.com/get-started/ to get started on Docker. The **learning curve is minimal** (2 days work at most) and the gains are enormous.

## Dockerhub
Lastly Dockerhub deserves a special mention. Personally Dockerhub is what makes Docker truly powerful. It's what github is to git, a open platform to share your Docker images.

My Docker image for Machine Learning and data science is availale here: https://hub.docker.com/r/sachinruk/ml_class/
