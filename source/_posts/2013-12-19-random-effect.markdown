---
layout: post
title: "Random Effect"
date: 2013-12-19 21:38
comments: true
categories: Statistics
---

Random effects models are often needed to account for unexplained heterogeneous situation.

Two commonly used distributions estimating lifetime are as follows.

### Inversed Guassian distribution

$$ X \sim IG(\mu,\lambda) $$, where $$X \in (0,\infty)$$. $$\mu$$ and $$\lambda$$ are called mean and shape parameter respectively.

1. *PDF:* $$(\frac{\lambda}{2\pi x^3})^{1/2}exp(\frac{-\lambda(x-\mu)^2}{2\mu^2 x})$$
2. *CDF:* $$\Phi(\sqrt{\frac{\lambda}{x}}(\frac{x}{\mu}-1))+exp(\frac{2\lambda}{\mu})\Phi(-\sqrt{\lambda}{x}(\frac{x}{\mu}+1))$$
3. *Expectation and Variance:* $$E(X)=\mu$$, $$V(X)=\frac{\mu^3}{\lambda}$$

### Gamma distribution

$$X \sim gamma(\alpha,\beta)$$, where $$X \in (0,\infty)$$. $$\alpha$$ and $$\beta$$ are called shape and rate parameter respectively.

1. *PDF:* $$\frac{\beta^{\alpha}x^{\alpha-1}e^{-\beta x}}{\Gamma(\alpha)}$$
2. *Gamma function:* $$\Gamma(t) = \int_{0}^{\infty} x^{t-1} e^{-x} dx$$
3. *Useful equation:* $$\frac{\Gamma(b+1)}{a^{b+1}} = \int_{0}^{\infty} t^b e^{-at}dt$$
4. *Expectation and Variance:* $$E(X)=\frac{\alpha}{\beta}$$, $$V(X)=\frac{\alpha}{\beta^2}$$

## Consider IG processes with Random Effects

Consider a Wiener process $$W(x) = \mu^{-1}x+\eta^{-1/2}B(x)$$ with the induced IG process $$Y(t) \sim IG(\mu \Lambda(t),\eta \Lambda^2(t))$$. A common practice to incorporate random effects in the Wiener process is to let the drift parameter $$\mu^{-1}$$ vary randomly across units. Assume $$\mu^{-1}$$ foolows a truncated normal distribution $$TN(w,k^{-2})$$, $$k>0$$ with PDF

$$g(\mu^{-1}) = \frac{k \phi[k(\mu^{-1}-w)]}{1-\Phi(-kw)}$$

the joint PDF of $$\mathbf{Y}_i = [Y_i(t_{i1}),Y_i(t_{i2}),\cdots,Y_i(t_{in_i})]$$ can be computed first conditioning on the random drift parameter $$\mu_i$$ and then marginalizing it

$$

\begin{align}
f(\mathbf{Y}_i) & = \int_{0}^{\infty} \prod_{j=1}^{n_i} \sqrt{\frac{\eta \lambda_{ij}^2}{2 \pi y_{ij}^3}} exp\{ \frac{-\eta(y_{ij}-\mu \lambda_{ij})^2}{2y_{ij}}\} \frac{k\phi[k(z-w)]}{1-\Phi(-kw)} dz \\
& = \frac{k}{1-\Phi(-kw)} \prod_{j=1}^{n_i} \sqrt{\frac{\eta \lambda_{ij}^2}{2\pi y_{ij}^3}} \int_{0}^{\infty} \prod_{j=1}^{n_i} exp \{\frac{-\eta (y_{ij}z-\lambda_{ij})^2}{2y_{ij}}\} \frac{1}{\sqrt{2\pi}} exp\{-\frac{k^2(z-w)^2}{2}\} dz \\
& = \frac{k}{1-\Phi(-kw)} \prod_{j=1}^{n_i} \sqrt{\frac{\eta \lambda_{ij}^2}{2\pi y_{ij}^3}} exp\{-\eta \sum_{j=1}^{n_i} \frac{\lambda_{ij}^2}{2y_{ij}}\} \int_{0}^{\infty} \frac{1}{\sqrt{2\pi}} exp \{-\frac{\eta}{2}Y_iz^2 + \eta \Lambda_iz-\frac{k^2(z-w)^2}{2}\} dz \\
& = \frac{1-\Phi(-\tilde{k}_i \tilde{w}_i)}{1-\Phi(-kw)} \frac{k}{\tilde{k}_i} \prod_{j=1}^{n_i} \sqrt{\dfrac{\eta \lambda_{ij}^2}{2\pi y_{ij}^3}} exp[\frac{\tilde{k}_i^2\tilde{w}_i^2-k^2w^2}{2}-\eta \sum_{j=1}^{n_i} \frac{\lambda_{ij}^2}{2y_{ij}}]
\end{align}

$$

where $$y_{ij} = Y_i(t_{ij})-Y_i(t_{i,j-1})$$ is the observed increment, $$\lambda_{ij} = \Lambda(t_{ij})-\Lambda(t_{i,j-1})$$, $$\tilde{k}_i = \sqrt{\eta Y_i(t_{i,n_i})+k^2}$$ and $$\tilde{w}_i = (\eta \Lambda(t_{i,n_i})+wk^2)/{\tilde{k}_i^2}$$. 




