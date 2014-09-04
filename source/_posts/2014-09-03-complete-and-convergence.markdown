---
layout: post
title: "Complete and Convergence"
date: 2014-09-03 16:55
comments: true
categories: Analysis
---

This post will talk about [complete](http://en.wikipedia.org/wiki/Complete_metric_space) and convergence, including [uniform convergence](http://en.wikipedia.org/wiki/Uniform_convergence) and [poitwise convergence](http://en.wikipedia.org/wiki/Pointwise_convergence). These two concepts are very important in mathimatical analysis.

## Complete

> In mathimatics, a Cauchy sequence is a sequence whose elements become arbitrary close to each other as the sequence progresses. The definition of Cauchy sequence can regard to real numbers and a metric space. A metric space $M$ is called complete if every Cauchy sequence in $M$ converges in $M$. 

One main shortcoming of Riemann integration is that all $L_p$ space except for $$L_ \infty$$ fail to complete. 

## Convergence

We first given two definitions of convergence, i.e., pointwise convergence and uniform convergence.

> Define a sequence of functions $$\{f_t; t\in T\}$$ on the set $$E \subset X$$ over the base $$B$$. Introduce the quantity $$\Delta_t(x) = \mid f(x)-f_t(x) \mid $$ and $$\Delta_t = \sup_{x\in E} \Delta_t(x)$$. Then

$$(f_t \to f \;on \;E) := \forall x \in E, (\Delta_t(x) \to 0 \; over \; B),$$

$$(f_t \Rightarrow f \; on \;E) := (\Delta_t \to 0 \;over \;B).$$

Obviously, the uniform convergence is stronger than the pointwise convergence. Also, the uniform convergence plays an very important role to the passage to limit with regard to continuity, integration and differentiation. 

### Continuity and passage to the limit

> Let $$\{ f_t; t \in T\}$$ be a family of functions $$f_t: X \to C$$ depending on the parameter $t$; let $$B$$ be a base in $$T$$. If $$f_t \Rightarrow f$$ on $$X$$ over the base $$B$$ and the function $$f_t$$ are continuos at $$x_0 \in X$$, then the function $$f:X \to C$$ is also continuos at that point.

This theorem can result in a useful proposition, named Dini's theorem, to prove the uniform convergence.

> If a sequence of continuos functions on a compact set converges monotonically to a continuous function, then the convergence is uniform. 

<!--more-->

### Integration and passage to the limit

> Let $$\{ f_t; t \in T\}$$ be a family of functions $$f_t: X \to C$$ defined on a closed interval $$a \le x \le b$$ and depending on the parameter $$t \in T$$, and let $B$ be a base in $T$. If the functions of the family are integrable on $$[a,b]$$ and $$f_t \Rightarrow f$$ on $$[a,b]$$ over the base $$B$$, then the limit function $$f:[a,b] \to C$$is also integrable on $$[a,b]$$ and 

$$\int_a^b f(x) dx = \lim_{B} \int_a^b f_t(x) dx.$$

A useful corollary following by is

> If the series $$\sum_{n=1}^\infty f_n(x)$$ consisting of integrable functions on a closed interval $$[a,b] \subset R$$ converges uniformly on that closed interval, then its sum is also integrable on $$[a,b]$$ and 

$$\int_a^b (\sum_{n=1}^{\infty} f_n(x))dx = \sum_{n=1}^{\infty} \int_a^b f_n(x) dx.$$


### Differentiation and passage to the limit

The condition of interchanging between differentiation and limit is more strict. In general, if the original function converges uniformly, the limit function need not be differentiable; even if it is differentiable, the derivative of the limit function need not be equal to the limit of derivatives.

> Let $$\{ f_t; t \in T\}$$ be a family of functions $$f_t: X \to C$$ defined on a convex bounded set $X$ (in $R$, $C$, or any normed space) and depending on the parameter $$t \in T$$; let $B$ be a base in $T$. If the functions of the family is differentiable on $X$, and the family of derivatives $$\{f'_t; t\in T\}$$ converges uniformly on $X$ to function $\psi:X\to C$, and the original family $$\{f_t;t\in T\}$$ converges at even on point $$x_0 \in X$$, then it converges uniformly on the entire set $X$ to a differentiable function $$f:X\to C$$, and $$f '=\psi$$.  

A corollary following by is

> If the series $$\sum_{n=1}^\infty f_n(x)$$ of functions $$f_t: X \to C$$ that are differentiable  on a convex bounded set $X$ (in $R$, $C$, or any normed space)  converges at even on point $$x \in X$$ and the series $$\sum_{n=1}^\infty f'_n(x)$$ converges uniformly on $X$, then $$\sum_{n=1}^\infty f_n(x)$$ $$\sum_{n=1}^\infty f_n(x)$$ also  converges uniformly on $X$, its sum is differentiable on $X$ and 

$$(\sum_{n=1}^\infty f_n(x))'=  \sum_{n=1}^\infty f'_n(x).$$ 
