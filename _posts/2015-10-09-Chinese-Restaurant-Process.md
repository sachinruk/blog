---
layout: post
title: "Chinese Restuarant Process"
modified:
categories: blog
excerpt: Generative Process of the Chinese Restaurant Process (CRP).
tags: [Bayesian, Clustering, Dirichlet Process]
image:
  feature:
date: 2015-10-09
share: true
ads: true
---
In this instance we generate the parameters $$\theta_k$$ from $$\mathcal{N}(\mathbf{0},3\mathbf{I})$$. The data is generated from $$\mathcal{N}(\theta_k,0.1\mathbf{I})$$. Where $$k$$ is the table. Table allocation is the main part of the CRP which is determined by:
$$\begin{align}
k=\begin{cases}
\text{new table } & \text{with prob = } \frac{\alpha}{\alpha+n-1}\\
\text{table k } & \text{with prob = } \frac{n_k}{\alpha+n-1}
\end{cases}
\end{align}
$$
where $$n_k$$ is the number of customers at table $$k$$.

The associated ipython notebook is [located here](https://github.com/sachinruk/sachinruk.github.io/blob/master/_posts/Stats%20Blog/CRP.ipynb).


