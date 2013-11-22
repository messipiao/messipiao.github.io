---
layout: post
title: "Random Sample"
date: 2013-11-20 15:03
comments: true
categories: Statistics
---

## Basic Concepts of Random Samples

> The random variables $$X_1,\dots,X_n$$ are called a random sample of size n from the population $$f(x)$$ if $$X_1,\dots,X_n$$ are mutually independent random variables and the marginal pdf or pmf of each $$X_i$$ is the same function $$f(x)$$. Alternatively, $$X_1,\dots,X_n$$ are called independent and identically distributed random variables with pdf or pmf $$f(x)$$. This is commonly abbreviated to iid random variables. 

The joint pdf of pmf of $$X_1,\dots,X_n$$ is given by 

$$f(x_1,\dots,x_n) = f(x_1)f(x_2)\cdots f(x_n) = \prod_{i=1}^{n}f(x_i)$$

 Two methods, sampling with and without replacement for drawing a random sample are considered here. When sampling is from a infinite population, both methods make the equation hold, as removing any sample will not change the population. However, when sampling is from a finite population, sampling with replacement still makes the equation holds while sampling without replacement not. This is because the former method will not change the population, so the random variable $$X_1,\dots,X_n$$ are independent as the process of choosing any $$X_i$$ keep the same. As for method of sampling without replacement, the probability distribution for $X_j$ depneds on the value of $$X_i$$, where $$j > i$$. For example, considering $$X_1$$ and $$X_2$$, we have

$$P(X_2 = x_1 \mid X_1=x_1) = 0  ~ \text{and} ~P(X_2=x \mid X_1=x_1) = \dfrac{1}{N-1} ~ \text{for} ~ x \ne x_1$$

It is noted that $$X_i$$ has the same marginal distribution.

$$P(X_2=x) = \sum_{i=1}^{N} P(X_2=x \mid X_1=x_i)P(X_1=x_i) = \frac{1}{N}$$

When $N$ is larger, there is not too difference between the conditional distribution of $$X_i$$ given $$ X_1, \dots,X_{i-1} $$ and the marginal distribution. We say the random variables are *nearly independent*. 

## Convergence

### Types of convergence

* **Convergence in Probability**

A sequence of random variables, $$X_1,X_2,\dots$$, converges in probability to a random variable $X$ if, for every $$\epsilon > 0$$,

$$\lim_{n \to \infty} P(\mid X_n-X \mid \ge \epsilon (\text{or} ~~ < \epsilon)) = 0 (\text{or} ~~ 1)$$

* **Convergence in almost sure**

A sequence of random variables, $$X_1,X_2,\dots$$, converges in probability to a random variable $X$ if, for every $$\epsilon > 0$$,

$$P(\lim_{n \to \infty} \mid X_n-X \mid < \epsilon ) = 1$$

The above definition is much stronger than that of convergence in probability.

* **Convergence in Distribution**

A sequence of random variables, $$X_1,X_2,\cdots$$ , converge in distribution to a random variable $X$
If

$$\lim_{n \to \infty} F_{X_n}(x) = F_X(x)$$

at all points x there $$F_X(x)$$ is continuous.

### Related Theorem or Method

* **Continuous mapping Theorem**

If $X_n$ converges in probability or almost sure or distribution to a random variable $X$, and $$g(x)$$ is a continuous function, then $$g(X_n)$$ converges in corresponding form to $$g(X)$$.

* **Slutsky's Theorem**

If $$X_n \to X$$ in distribution and $$Y_n \to a$$, a costant, in probability then

$$
\begin{align}
1. & Y_nX_n \to aX \text{in distribution} \\
2. & X_n+Y_n \to X+a \text{in distribution} \\
\end{align}
$$

* **Weak Law of Large Numbers**

If $X_n$ are i.i.d distributed with $$E\mid X_n \mid < \infty$$, $$\mu = EX_n$$,then

$$\bar{X} \to \mu \quad \text{in probability}$$

* **Strong Law of Large Numbers**

If $X_n$ are i.i.d distributed with $$E\mid X_n \mid < \infty$$, $$\mu = EX_n$$,then

$$\bar{X} \to \mu \quad \text{in almost sure}$$

* **Central Limit Theorem**

If $$X_n, n=1,2,\dots,$$ are i.i.d, and $$\mu = EX_n$$, $$\sigma^2 = var(X_n)$$, and $$0 < \sigma^2 < \infty$$, then

$$\frac{\sqrt{n}(\bar{X}-\mu)}{\sigma} \sim N(0,1)$$

* **Delta Method**

Let $Y_n$ be a sequence of random variables that satisfies $$\sqrt{n}(Y_n-\theta) \sim N(0,\sigma^2)$$
. For a given function $g$ and a specific value of $\theta$, suppose that $$g'(\theta)$$ exists and is not 0. Then

$$\sqrt{n} [g(Y_n)-g(\theta)] \sim N(0,\sigma^2[g'(\theta)]^2)$$

## Sample mean and Sample variance

The sample mean is the arithmetic average of the values in a random sample. It is usually denoted by

$$\bar{X} = \frac{1}{n}\sum_{i=1}^{n} X_i$$

The sample variance is the statistic defined by

$$S^2 = \frac{1}{n-1} \sum_{i=1}{n}(X_i-\bar{X})^2$$

Let $$X_1,\dots,X_n$$ be a random sample from a population with mean $$\mu$$ and variance $$\sigma^2 < \infty$$. Then

$$
\begin{align}
1. & E\bar{X} = \mu \\
2. & Var \bar{X} = \frac{\sigma^2}{n} \\
3. & ES^2 = \sigma^2 \\
\end{align}
$$

### Normal Case

If $X_n$ are independently and normally distributed $$N(\mu,\sigma^2)$$, then

$$
\begin{align}
1. & \bar{X}_n \sim N(\mu,\sigma^2/n) \\
2. & (n-1)S_n^2 / \sigma^2 \sim \chi_{n-1}^2 \\
3. & \bar{X}_n ~ \text{and} ~ S^2_n ~ \text{are independent} \\
\end{align}
$$

### Non-normal Case

When $X_i$ are not normal, the statistic is still commonly used because

+ Central Limit Theorem

$$\bar{X}_n \sim N(\mu,\sigma^2/n)$$

+ Law of Large Numbers

$$S_n^2 \to \sigma^2$$

+ Slusky's Theorem

$$\frac{\bar{X}_n-\mu}{S_n/\sqrt{n}} = \frac{\sigma}{S_n} \cdot \frac{\bar{X}_n-\mu}{\sigma/\sqrt{n}} \to N(0,1)$$












