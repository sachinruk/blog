---
layout: post
title: "von Mises-Fisher Distribution"
modified:
categories: blog
excerpt: von Mises-Fisher Distribution, mean and covariance.
tags: [Expectation, Covariance, Exponential Distributions]
image:
  feature:
date: 2015-08-10
share: true
ads: true
---

The von Mises Fisher Distribution is a multivariate distribution on a hyper sphere. I have decided to share the expectation and covariance of the vMF distribution. The Wikipedia page doesn't give much info of this distribution.

## Expectation of vMF distribution

Let \\(C\\) be the normalising constant.

$$
\int_{||\mathbf{x}||_2=1}\exp(\kappa\mathbf{\mu}^T\mathbf{x})\,d\mathbf{x} = \frac{(2\pi)^{d/2-1} I_{d/2-1}(\kappa)}{\kappa^{d/2-1}}=C 
$$

Let \\(\mathbf{y}=\kappa\mathbf{\mu}\\). Therefore \\(\kappa=\sqrt{\mathbf{y}^T\mathbf{y}}\\).

$$ \begin{align}
\frac{d\kappa}{d\mathbf{y}}=\frac{1}{2}\frac{\mathbf{y}}{\sqrt{\mathbf{y}^T\mathbf{y}}}=\frac{\kappa\mathbf{\mu}}{\kappa}=\mathbf{\mu}
\end{align} 
$$

$$
\begin{align}
\int \mathbf{x} \exp(\mathbf{y}^T \mathbf{x}) d\mathbf{x} =& \frac{d}{d\mathbf{y}} \int \exp(\mathbf{y}^T \mathbf{x}) d\mathbf{x}\\
=& \frac{d\kappa}{d\mathbf{y}} \frac{d}{d\kappa} \int \exp(\mathbf{y}^T \mathbf{x}) d\mathbf{x} \\
=& \mathbf{\mu} \frac{d}{d\kappa} \frac{(2\pi)^{d/2-1} I_{d/2-1}(\kappa)}{\kappa^{d/2-1}} \\
=& \mathbf{\mu} \left(\frac{I'_{d/2-1}(\kappa)}{I_{d/2-1}(\kappa)} - \frac{d/2-1}{\kappa}\right) \frac{(2\pi)^{d/2-1} I_{d/2-1}(\kappa)}{\kappa^{d/2-1}}\\
 E(\mathbf{x}) =& \frac{\int \mathbf{x} \exp(\mathbf{y}^T \mathbf{x}) d\mathbf{x}}{\int \exp(\mathbf{y}^T \mathbf{x}) d\mathbf{x}} = \mathbf{\mu} \left(\frac{I'_{d/2-1}(\kappa)}{I_{d/2-1}(\kappa)} - \frac{d/2-1}{\kappa}\right)\\
E(\mathbf{x}) =& \frac{I_{d/2}(\kappa)}{I_{d/2-1}(\kappa)}\mathbf{\mu}
\end{align}
$$

This is an interesting result because its saying that the mean of a von Mises-Fisher distribution is NOT \\(\mathbf{\mu}\\). It is infact multiplied a constant $$ \frac{I_{d/2}(\kappa)}{I_{d/2-1}(\kappa)} $$ which is between \\((0,1)\\). If you think about a uniformly distributed vMF this makes sense (\\(\kappa\to 0\\)). If we average all those vectors pointing in different directions it averages very close to 0. This whole 'averaging' of unit vectors is what makes the expected value not equal \\(\mathbf{\mu}\\) but a vector pointing in the same direction but smaller in length.

##Covariance of von Mises-Fisher Distribution

Using the same differential approach we can find $$E(\mathbf{xx}^T)$$ and hence the covariance by using the identity $$cov(\mathbf{x},\mathbf{x})=E(\mathbf{xx}^T)-E(\mathbf{x})E(\mathbf{x})^T$$. Hence the covariance is,

$$
\begin{align}
\frac{h(\kappa)}{\kappa}\mathbf{I}+\left(1-2\frac{\nu+1}{\kappa}h(\kappa)-h(\kappa)^2\right)\mathbf{\mu}\mathbf{\mu}^T
\end{align}
$$

where $$h(\kappa)=\frac{I_{\nu+1}(\kappa)}{I_{\nu}(\kappa)}$$ and $$\nu=d/2-1$$.
