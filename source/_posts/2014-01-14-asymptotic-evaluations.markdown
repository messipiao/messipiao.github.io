---
layout: post
title: "Asymptotic Evaluations"
date: 2014-01-14 20:19
comments: true
categories: Statistics
---

All of the criteria we have considered thus far has been finite-sample criteria. In contrast, we may consider situations when the sample size becomes infinite.

## Point Estimation

The property of consistency is a quite fundamental one of asymptotic properties, which is concerned with the asymptotic accuracy of an estimator. However, we may also consider the asymptotic variance of an estimator, called efficiency.

> For an estimator $$T_n$$, if $$lim_{n \to \infty} k_n VarT_n = \tau^2 < \infty$$, where $${k_n}$$ is a sequence of constants, then $$\tau^2$$ is called the *limiting variance* or *limit of the variances*.

> For an estimator $$T_n$$, suppose that $$k_n(T_n-\tau(\theta)) \to n(0,\sigma^2)$$ in distribution. The parameter $$\sigma^2$$ is called the *asymptotic variance* or *variance of the limit distribution of $T_n$*.

It is always the case that the asymptotic variance is smaller than the limiting variance, though have the same values when calculating variances of sample means and other types of average.

> A sequence of estimators $W_n$ is asymptotically efficient for a parameter $$\tau(\theta)$$ if $$ \sqrt{n} [W_n-\tau(\theta)] \to n[0,v(\theta)]$$ in distribution and $$v(\theta)$$ achieves the **Cramer-Rao Lower Bound**.

Recall that in the above definition, 

$$v(\theta) = \dfrac{[\tau'(\theta)]^2}{E_{\theta}((\frac{\partial}{\partial \theta} \log f(X \vert \theta))^2)}$$

In general, we can consider MLEs to be consistent and asymptotically efficient. As a result, we can calculate the variance of MLEs approximately.

*Remarks: Bootstrap is another popular way to calculate standard erors.*

<!--more-->

## Robustness

Robustness and Optimality are in the two sides of a coin. For example, generally sample mean is a more accurate estimator than sample mean, while not a robust estimator sometimes (think about adding a really huge number into a sample). M-estimators is used to consider a compromise between mean and median. We are not covering this topic here.

## Hypothesis Testing

We are going to introduce 3 large-sample tests here.

### Asymptotic distribution of the LRT

> Let $$X_1,\dots,X_n$$ be a random sample from a pdf or pmf $$f(x \vert \theta)$$. Under some regularity conditions, if $$\theta \in \Theta_0$$, then the distribution of the statistic $$-2\log \lambda(\mathbf{X})$$ converges to a chi squared distribution as the sample size $$n \to \infty$$. The degrees of freedom of the limiting distribution is the difference between the number of free parameters specified by $$\theta \in \Theta_0$$ and the number of free parameters specified by $$\theta \in \Theta$$.

### Wald test

In general, a Wald test is a test based on a satistic of the form

$$ Z_n = \dfrac{W_n-\theta_0}{S_n} $$ 

where $\theta_0$ is a hypothesized value of the parameter $\theta$, $W_n$ is an estimator of $\theta$, and $$S_n$$ is a standard error for $W_n$, an estimate of the standard deviation of $W_n$. If $W_n$ is the MLE of $\theta$, then, $$1/\sqrt{I_n(W_n)}$$ is a reasonable standard error for $W_n$. Alternatively, $$1/\sqrt{\hat{I}_n(W_n)}$$, where

$$\hat{I}_n(W_n) = -\frac{\partial^2}{\partial \theta^2} \log L(\theta \vert \mathbf{X}) \mid_{\theta = W_n}$$

is the observed information number, is often used. 

### Score test

The *score statistics* is defined to be

$$ S(\theta) = \frac{\partial}{\partial \theta} \log f(\mathbf{X} \vert \theta) = \frac{\partial}{\partial \theta} \log L(\theta \vert \mathbf{X}) $$

We can obtain the result that for all $\theta$, $$E_\theta S(\theta) = 0 $$. In particular, if we are testing $$H_0: \theta=\theta_0$$ and if $H_0$ is true, then $$S(\theta_0)$$ has mean 0. Then we have

$$Var_\theta S(\theta) = I_n(\theta)$$

The test statistic for the score test is

$$Z_S = S(\theta_0)/\sqrt{I_n(\theta_0)}$$

It follows that $Z_S$ converges to a standard normal random variable.
