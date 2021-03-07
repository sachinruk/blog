---
layout: post
title: "Reversible jump MCMC"
modified:
categories: blog
excerpt: How to change dimensions of parameters in a Bayesian setting
tags: [MCMC, Bayesian, clustering]
image:
  feature:
date: 2015-10-20
share: true
ads: true
markdown: kramdown
mathjax: true
---

# Reversible jump MCMC

Reversible jump MCMC is a Bayesian algorithm to infer the number of components/ clusters from a set of data. For this illustration we shall consider a two component model at most.

## Model
The likelihoods can be represented as:
$$
\begin{align}
p(y_i|\lambda_{11},k=1)=&\lambda_{11}\exp(-\lambda_{11}y_i)\\
p(y_i|\lambda_{12},\lambda_{22},k=2,z_i)=&\prod_j (\lambda_{j2}\exp(-\lambda_{j2}y_i))^{1(z_i=j)}
\end{align}
$$

The priors on the latent variables are:

$$
\begin{align}
p(\lambda_{jk})\propto & \frac{1}{\lambda_{jk}}\qquad \lambda_{jk}\in[a,b]\\
p(z_i=1)=&\pi\\
p(\pi) = & \text{Dir}(\alpha)
p(k=j)= & 1/K
\end{align}
$$

## Jumping dimensions
We need to consider a Metropolis-Hastings (MH) step to consider going from one component to two components. The MH step in general is as follows:

$$
\begin{align}
\alpha = & \frac{p(y,\theta_2^{t+1})}{p(y,\theta_1^t)}\frac{q(\theta_1^t|\theta_2^{t+1})}{q(\theta_2^{t+1}|\theta_1^{t})}\\
A = & \text{min}\left(1,\alpha\right)
\end{align}
$$

where,

$$
\begin{align}
p(y_i,\theta_2)=& p(y|\lambda_{12},\lambda_{22},\pi)p(\lambda_{12})p(\lambda_{22})p(\pi)\\
=&\pi p(y_i|\lambda_{12})+(1-\pi) p(y_i|\lambda_{22})
\end{align}
$$

### Jumping from 1 dim to 2
In this case let the parameters $$\theta=\{\cup_j\lambda_{jk},k,\pi\}$$ . As we can let the proposal distribution be anything, we let $$q(\theta_1\to\theta_2)$$ as follows:
$$
\begin{align}
q(\lambda_{j2},\pi,k=2|k=1,\lambda_{11})=q(\lambda_{j2}|k=2,\lambda_{11})q(\pi|k=2)q(k=2|k=1)
\end{align}
$$

We let the **proposal** $$q(k=2\vert k=1)=1$$. We also have the following dimensional jump:

$$
\begin{align}
\mu_1,\mu_2\sim & U(0,1)\\
\lambda_{12}=&\lambda_{11}\frac{\mu_1}{1-\mu_1}\\
\lambda_{22}=&\lambda_{11}\frac{1-\mu_1}{\mu_1}\\
\pi=&\mu_2
\end{align} 
$$

Thus, in order to find the distribution \(q(\lambda_{j2}\vert k=2,\lambda_{11})\) we use the change of variable identity that $$q(\lambda_{j2}\vert k=2,\lambda_{11})=q(\mu_1)\vert J\vert$$ where, $$J$$ is the jacobian $$\frac{\partial(\lambda_{11},\mu_1)}{\partial(\lambda_{12},\lambda_{22})}$$. The Jacobian determinant is found to be $$\frac{\mu_1(1-\mu_1)}{2\lambda_{11}}$$ while $$q(\mu_1)=q(\mu_2)=1$$ since they are sampled from standard uniform distributions. Also \(q(\mu_2)=q(\pi\vert k=2)\).

Since we need the ratio of proposed states \( \frac{q(\theta_1^t|\theta_2^{t+1})}{q(\theta_2^{t+1}|\theta_1^{t})} \) we are also required to find \( q(\lambda_{11},k=2\vert\lambda_{2j},\pi,k=1) = q(\lambda_{11}\vert\lambda_{2j},k=2) q(k=1 \vert k=2) \). We again take \( q(k=1\vert k=2)=1 \). \(q(\lambda_{11}=\sqrt{\lambda_{12}\lambda_{22}})=1\)
 
### Jumping from 2 to 1
The MH step is conducted using the reciprocal of $\alpha$ in the equation above.

## RJMCMC Algorithm

