---
layout: post
title: "Basics of Martingales"
date: 2013-11-18 16:16
comments: true
categories: Probability
---

Here martingale, a type of stochastic process, whose definition formalizes the concept of a fair game, is considered. 

### Martingales
A stochastic process ${Z_n,n \ge 1}$ is said to be a martingale process if 
$$ 
E[|Z_n|] < \infty \quad \text{for all n}
$$
and

$$ E[Z_{n+1} \mid Z_1,Z_2,\dots,Z_n] = Z_n. $$

Taking expectations of both sides gives

$$E[Z_{n+1}]=E[Z_n]$$

When 

$$ E[Z_{n+1} \mid Z_1,Z_2,\dots,Z_n]>Z_n $$ 

it is a sub-martingale and when 

$$ E[Z_{n+1} \mid Z_1,Z_2,\dots,Z_n]<Z_n $$ 

it is a super-martingale.

* Let $$X,Y_1,Y_2,\dots$$ be arbitary random variables such that 
$$ E[|X|] < \infty $$, 
and let

$$Z_n = E[X \mid Y_1,\dots,Y_n]$$

It then follows that $${Z_n,n \ge 1}$$ is a martingale, which is called a **Doob type martingale**.

* The parial sums of independent random variables having mean 0 is a martingale. The simplest example:

$$ Z_n = \sum_{i=1}^n {X_i - E[X_i \mid X_1,\dots,X_{i-1}]}$$

* Note that when compute the conditional expectation of $Z_{n+1}$, we often use more informative random variables instead $$Z_1, \dots, Z_n$$. 
Actually, we can prove this results. Let $$Z = g(Y)$$ then

$$E(X \mid Z) = E(E(X \mid Z,Y) \mid Z) = E(E(X \mid Y) \mid Z) = E(X\mid Y)$$

## Stopping Times

### Definition

The positive interger-value, possibly infinite, random variable $N$ is said to be a random time for the process $${Z_n,n \ge 1}$$ if the event {N=n} is determined by the randon variables $$Z_1,\dots,Z_n$$. That is, knowing $Z_1,\dots,Z_n$ tells us whether or not $$N=n$$. If $$P(N < \infty)$$, then the random time $N$ is said to be a **stopping time**.

### The Martingale Stopping Theorem

If either:


1. $$Z_{n \land N}$$ is bounde, or;
2. $$N$$ is bounded, or;
3. $$E[N] < \infty$$, and there is an $$M<\infty$$ such that

$$E[\mid Z_{n+1}-Z_n \mid \mid Z_1,\dots,Z_n] < M$$

then 

$$E[Z_N] = E[Z_1]$$

NOTE that boundedness is important. Take $X_0=0$ and

$$X_n = \xi_1+\xi_2+\cdots+\xi_n$$

where $\xi_i$ are independent identically distributed random variables taking the value $$\pm \dfrac{1}{2}$$. Let $$T = inf\{n:X_n=1\}$$. Then T is a stopping time, $$P[T<\infty] = 1$$, but T is not bounded. $$X_T=1$$ with probability 1 and trivially $$E[X_T]=1 \neq 0$$.

This theorem can be applied to prove the **Wald's Equation** and analyze cards and gambling problems, which will be summarized in my future posts. 

## Azuma's Inequality

Let $$Z_n, n \ge 1$$ be a martingale with mean $$\mu = E[Z_n]$$. Let $Z_0 = \mu$ and suppose that for nonegative constants $$\alpha_i,\beta_i,i\ge 1$$,

$$-\alpha_i \le Z_i-Z_{i-1} \le \beta_i$$

Then for any $$n \ge 0, a > 0$$:

$$
\begin{align}
1. & P\{Z_n-\mu \ge a\} \le exp\{-2a^2/\sum{(\alpha_i+\beta_i)^2}\} \\
2. & P\{Z_n-\mu \le -a\} \le exp\{-2a^2/\sum{(\alpha_i+\beta_i)^2}\} \\
\end{align}
$$

## The Martingale Convergence Theorem

If $$\{Z_n,n \ge 1\}$$ is a martingale such that for some $$M< \infty$$

$$E[\mid Z_n \mid] \le M, \text{for all n}$$

then, with probability 1, $$\lim_{n \rightarrow \infty} Z_n$$ exists and is finite.



