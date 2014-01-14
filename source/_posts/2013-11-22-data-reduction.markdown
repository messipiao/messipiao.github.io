---
layout: post
title: "Data Reduction"
date: 2013-11-22 16:23
comments: true
categories: Statistics
---

Any statistic, T(**X**), defines a form of data reduction or data summay. 

## Sufficient Statistics

> A statistic T(**X**) is a sufficient statistic for $$\theta$$ if the conditional distribution of the samle **X** given the value of T(**X**) does not depend on $\theta$.

A sufficient statistic captures all the infromation about $\theta$.

> If $$p( \mathbf{x} \vert \theta)$$ is the joint pdf or pmf of $$\mathbf{X}$$ and $$q(t \vert \theta)$$ is the pdf or pmf of $$T(\mathbf{X})$$, then $$T(\mathbf{X})$$ is a sufficient statistic for $\theta$ if, for every x in the sample space, the ration $$p(\mathbf{x} \vert \theta)/q(T(\mathbf{x}) \vert \theta)$$ is constant as a function of $\theta$.

To use the definition, we must guess a statistic $T(\mathbf{X})$ to be sufficient, find the pmf of pdf of $T(\mathbf{X})$, and check that the ratio of pdfs or pmfs does not depend on $\theta$. **Factorization Theorem** provides us another way to find a sufficient statistic.

* Lef $$f(\mathbf{x}\vert \theta)$$ denote the joint pdf or pmf of a sample $$\mathbf{X}$$. A statistic $T(\mathbf{X})$ is a sufficient statistic for $\theta$ if and only if there exist functions $$g(t \vert \theta)$$ and $$h(\mathbf{x})$$ such that, for all sample points $\mathbf{x}$ and all parameter points $\theta$,

$$f(\mathbf{x} \vert \theta) = g(T(\mathbf{x}) \vert \theta)h(\mathbf{x})$$

It is easy to find a sufficient statistic for an exponential family of ditributions using the **Factorizaion Theorem**.

* Let $$X_1,\dots,X_n$$ be *iid* observations from a pdf or pfm $$f(x \vert \mathbf{\theta})$$ that belongs to an exponential family given by

$$f(x \vert \mathbf{\theta}) = h(x)c(\mathbf{\theta})exp(\sum_{i=1}^{k}w_i(\mathbf{\theta})t_i(x)))$$

where $$\mathbf{\theta} = (\theta_1,\dots,\theta_d)$$, $$d \le k$$. Then

$$T(\mathbf{X}) = (\sum_{j=1}^{n}t_1(X_j),\dots,\sum_{j=1}^{n}t_k(X_j)))$$

is a sufficient statistic for $$\theta$$.

<!--more-->

## Minimal Sufficient Statistics

A minimal sufficient statistic achieves the most data reduction while still retaining all the information about $\theta$.

> A sufficient statistic $$T(\mathbf{X})$$ is called a minimal sufficient statistic if, for any other sufficient statistic $$T'(\mathbf{X})$$, $$T(\mathbf{X})$$ is a function of $$T'(\mathbf{X})$$.

We have an easier way to find a minimal sufficient statistic.

* Let $$f(\mathbf{x}\vert \theta)$$ be the pmf or pdf of a sample $\mathbf{X}$. Suppose there exists a function $$T(\mathbf{x})$$ such that, for every two sample points **x** and **y**, the ratio $$f(\mathbf{x} \vert \theta)/f(\mathbf{y} \vert \theta)$$ is constant as a function of $\theta$ if and only if $$T(\mathbf{x}) = T(\mathbf{y})$$. Then $$T(\mathbf{X})$$ is a minimal sufficient statistic for $\theta$.

Note that a minimal sufficient statistic is not unique. Any **one-to-one** function of a minimal sufficient statistic is also a minimal sufficient statistic.

## Ancillary Statistics

> A stastistic $$S(\mathbf{X})$$ whose distribution does not depend on the parameter $\theta$ is called an ancillary statistic.

**Alone**, an ancillary statistic contains no information about $\theta$.

* Location family ancillary statistic: Let $$X_1,\dots,X_n$$ be *iid* observations from a location parameter family with cdf $F(x-\theta)$, $$-\infty < \theta < \infty$$. $$R = X_{(n)}-X_{(1)}$$ is an ancillary statistic.
* Scale family ancillary statistic: Let $$X_1,\dots,X_n$$ be *iid* observations from a scale parameter family with cdf $F(x/\sigma)$, $\sigma >0$. Then any statistic that depends on the sample only through the $n-1$ values $$X_1/X_n,\dots,X_{n-1}/X_n$$ is an ancillary statistic.

The knowlede of ancillary statistics alone give us no information about $\theta$, while it may increse our knowledge about $\theta$ (can be a part of a sufficient statistic). For many important situations, our intuition that a minimal sufficient statistic is independent of any ancillary statistic is correct. 

## Complete Statistics

> Let $$f(t \vert \theta)$$ be a family of pdfs or pmfs for a statistic $$T(\mathbf{X})$$. The family of probability distributions is called complete if $$E_{\theta}g(T) = 0$$ for all $\theta$ implies $$P_{\theta}(g(T)=0) = 1$$ for all $\theta$. Equivalently, $$T(\mathbf{X})$$ is called a complete statistic.

Informally, a statistic $T(\mathbf{X})$ is complete if two different parameters $\theta$ of the distribution of $\mathbf{X}$, cannot give rise to the same distribution for $T\mathbf{X}$.

We can get the complete statistics in the exponential family.

 * Let $$X_1,\dots,X_n$$ be *iid* observations from a pdf or pfm $$f(x \vert \mathbf{\theta})$$ that belongs to an exponential family given by

$$f(x \vert \mathbf{\theta}) = h(x)c(\mathbf{\theta})exp(\sum_{i=1}^{k}w_i(\mathbf{\theta})t_i(x)))$$

where $$\mathbf{\theta} = (\theta_1,\dots,\theta_d)$$, $$d \le k$$. Then

$$T(\mathbf{X}) = (\sum_{j=1}^{n}t_1(X_j),\dots,\sum_{j=1}^{n}t_k(X_j)))$$

is complete if $$\{(w_1(\theta),\dots,w_k(\theta)):\theta \in \Theta\}$$ contains an open set in $R^k$.

We use completeness to state a condition under which a minimal sufficient statistic is independent of every ancillary statistic.

* **(Basu's Theorem)** If $$T(\mathbf{X})$$ is complete and minimal sufficient statistic, then $T(\mathbf{X})$ is independent of every ancillary statistic. 

It is noted that the theorem is also true if we omit the minimality constraint, as we have

* *If a minimal sufficient statistic exists, then any complete statistic is also a minimal sufficient statistc.* 

## Applications and Special distributions

* **The Bernoulli Distribution**

$Y=\sum X_i$ is minimal sufficient and complete for $p$.

* **Poisson Distribution**

$Y = \sum X_i$ is minimal sufficient and complete for $\theta$.

* **The Uniform Distribution**

1. interval $[0,\theta]$, $X_{(n)}$ is sufficient for $\theta$;
2. interval $$[\theta,\theta+1]$$, $$(X_{(1)},X_{(n)})$$ is minimal sufficient for $\theta$.

* **Normal Distribution**

1. $$(\sum X_i,\sum X^2_i)$$ is sufficient for $$(\mu,\sigma^2)$$;
2. $$(\bar{X},S^2)$$ is sufficient for $$(\mu,\sigma^2)$$.
 
