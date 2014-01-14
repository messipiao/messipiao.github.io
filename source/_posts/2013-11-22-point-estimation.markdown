---
layout: post
title: "Point Estimation"
date: 2013-11-22 19:31
comments: true
categories: Statistics
---

When sampling is from a population described by a pdf or pmf $$f(x \vert \theta)$$, knowledge of $\theta$ yields knowledge of the entire population. Hence, it is natural to seek a method of finding a good estimator of the point $\theta$, that is, a good point estimator. Note that an estimator is a function of the sample while an estimate is the realized value of an estimator (that is, a number) that is obtained when a sample is actually taken.

## Methods of Finding Estimators

### Method of Moments

Let $$X_1,\dots,X_n$$ be a sample from a population with pdf or pmf $$f(x \vert \theta_1,\dots,\theta_k)$$. Method of moments estimators are found by equating the first k sample moments to the corresponding k population moments.

$$m_k = \frac{1}{n} \sum_{i=1}^{n}X_i^k = \mu'_k = EX^k$$

### Maximum Likelihood Estimators

The likelihood function is defined by

$$L(\mathbf{\theta} \vert \mathbf{x}) = L(\theta_1,\dots,\theta_k \vert x_1,\dots,x_n) = \prod_{i=1}^{n} f(x_i \vert \theta_1,\dots,\theta_k)$$

Basicly, we can solve the first derivative of *log likelihood function* to get the MLEs. If the likelihood function cannot be maximized analytically, it may be possible to use a computer and maximize the likelihood function numerically.

MLE has the following properties.

* **(Invariance property of MLEs)** 

If $\hat{\theta}$ is the MLE of $\theta$, then for any function $f(\theta)$, the MLE of $f(\theta)$ is $f(\hat{\theta})$.

* **(Asymptotic Normality)** 

Under appropriate regularity conditions,

$$\sqrt{I_n(\theta_0)} (\hat{\theta}_n-\theta_0) \sim N(0,1)$$

In addition

$$\sqrt{I_n(\hat{\theta}_n)} (\hat{\theta}_n-\theta_0) \sim N(0,1)$$

where $I(\theta)$ is called the information number or *Fisher information* of the sample.

$$ I(\theta) = E[(\frac{\partial}{\partial \theta} \log f(X;\theta))^2] = -E[\frac{\partial^2}{\partial \theta^2} \log f(X;\theta)]$$

Fisher information has following properties.

$$
\begin{align}
1. & I_{X,Y}(\theta) = I_X(\theta)+I_Y(\theta)\\
2. & I_n(\theta) = n I(\theta) \\
\end{align}
$$


### The EM Algorithm

The EM algorithm is used to find **MLEs**, which is guaranteed to converge to the MLE. It is particularly suited to "missing data" problems, as the very fact that there are missing data can sometimes make calculations cumbersome.

If $$\mathbf{Y} = (Y_1,\dots,Y_N)$$ are the incomplete data, and $$\mathbf{X} = (X_1,\dots,X_m)$$ are the augmented data (missing data), making $$(\mathbf{Y},\mathbf{X})$$ the complete data. The densities $g(\cdot \vert \theta)$ of $\mathbf{Y}$ and $f(\cdot \vert \theta)$ of $\mathbf{Y},\mathbf{X}$ have the relationship

$$g(\mathbf{y} \vert \theta) = \int f(\mathbf{y},\mathbf{x} \vert \theta) dx$$

If we turn these into the likelihoods, $$L(\theta \vert \mathbf{y}) = g(\mathbf{y} \vert \theta)$$ is the incomplete-data likelihood and $$L(\theta \vert \mathbf{y},\mathbf{x}) = f(\mathbf{y},\mathbf{x} \vert \theta)$$ is the complete-data likelihood.i

Define

$$k(\mathbf{x} \vert \theta,\mathbf{y}) = \frac{f(\mathbf{y},\mathbf{x} \vert \theta)}{g(\mathbf{y} \vert \theta)} = \frac{L(\theta \vert \mathbf{y},\mathbf{x})}{L(\theta \vert \mathbf{y})}$$

Then we have

$$\log L(\theta \vert \mathbf{y}) = \log L(\theta \vert \mathbf{y},\mathbf{x}) - \log k(\mathbf{x} \vert \theta,\mathbf{y})$$

replace the right side with its expectation under $k(\mathbf{x} \vert \theta',\mathbf{y})$, we have

$$\log L(\theta \vert \mathbf{y}) = E[\log L(\theta \vert \mathbf{y},\mathbf{x}) \vert \theta',\mathbf{y}] - E[\log k(\mathbf{x} \vert \theta,\mathbf{y}) \vert \theta',\mathbf{y}]$$

Now we start the algorithm: From an initial value $$\theta^{(0)}$$ we create a sequence $$\theta^{(r)}$$ according to

$$\theta^{(r+1)} = \max_{\theta} E[\log L(\theta \vert \mathbf{y},\mathbf{x}) \vert \theta^{(r)},\mathbf{y}] $$

### Bayes Estimators

In Bayes approach $\theta$ is considered to be a quantity whose variation can be described by a probability distribution (called the prior distribution). This is a subjective distribution, based on the experimenter's belief, and is formulated before the data are seen (hence the name prior distribution). A sample is then taken from a population indexed by $\theta$ and the prior distribution is updated with this sample information. The updated prior is called the posterior distribution. 

If we denote the prior distribution by $\pi(\theta)$ and the sampling distribution by $$f(x \vert \theta)$$, then the posterior distribution, the conditional distribution of $\theta$ given the sample, $$\mathbf{x}$$, 

$$\pi(\theta \vert \mathbf{x}) = f(\mathbf{x} \vert \theta) \pi(\theta)/m(\mathbf{x})$$

where $m(\mathbf{x})$ is the marginal distribution of $\mathbf{X}$, that is,

$$m(\mathbf{x}) = \int f(\mathbf{x} \vert \theta) \pi(\theta) d \theta$$

## Methods of Evaluating Estimators

### Mean Squared Error

> The mean square error (MSE) of an estimator W of a parameter $\theta$ is the function of $\theta$ defined by $E_{\theta}(W-\theta)^2$.

Define

$$Bias_{\theta}W = E_{\theta}W-\theta$$

Then

$$E_{\theta}(W-\theta)^2 = Var_{\theta}W+(E_{\theta}W-\theta)^2 = Var_{\theta}W+(Bias_{\theta}W)^2$$

### Best Unbiased Estimators

> An estimator W' is a *best unbiased estimator of $\tau(\theta)$* if it satisfies $$E_{\theta}W' = \tau(\theta)$$ for all $\theta$ and, for any other estimator W with $$E_{\theta}W = \tau(\theta)$$, we have $$Var_{\theta}W' \le Var_{\theta}W$$ for all $\theta$. W' is also called a *uniform minimum variance unbiased estimator* (**UMVUE**) of $\tau(\theta)$.
 
* **Cramer-Rao Inequality**

Let $$X_1,\dots,X_n$$ be a sample with pdf $f(x \vert \theta)$, and let $$W(\mathbf{X}) = W(X_1,\dots,X_n)$$ be *any estimator satisfying*

$$\frac{d}{d\theta} E_{\theta}W(\mathbf{X}) = \int \frac{\partial}{\partial \theta}[W(\mathbf{x})f(x \vert \theta)] dx$$

and

$$Var_{\theta}W(\mathbf{X}) < \infty$$

Then

$$Var_{\theta}(W(\mathbf{X})) \ge \frac{(\frac{d}{d\theta}E_{\theta}W(\mathbf{X}))^2}{E_{\theta}[(\frac{\partial}{\partial \theta} \log f(\mathbf{X} \vert \theta))^2]} = \frac{(\frac{d}{d\theta}E_{\theta}W(\mathbf{X}))^2}{I_n(\theta)}$$

when $$X_1,\dots,X_n$$ are *iid*, based on the property of *Fisher Information*, we have

$$Var_{\theta}(W(\mathbf{X})) \ge \frac{(\frac{d}{d\theta}E_{\theta}W(\mathbf{X}))^2}{nE_{\theta}[(\frac{\partial}{\partial \theta} \log f(X \vert \theta))^2]} = \frac{(\frac{d}{d\theta}E_{\theta}W(\mathbf{X}))^2}{nI(\theta)}$$

We need to verify whether the **Cramer-Rao Lower Bound** is attainable.

* Let $$X_1,\dots,X_n$$ be *iid* $f(x \vert \theta)$, which satisfies the conditions of the *Cramer-Rao Theorem*. Let $$L(\theta \vert \mathbf{x}) = \prod_{i=1}^{n} f(x_i \vert \theta)$$ denote the likelihood function. If $$
W(\mathbf{X})=W(X_1,\dots,X_n) $$ is any unbiased estimator of $\tau(\theta)$, then $W(\mathbf{X})$ attains the Cramer-Rao Lower Bound if and only if 

$$a(\theta)[W(\mathbf{x})-\tau(\theta)] = \frac{\partial}{\partial \theta}\log L(\theta \vert \mathbf{x})$$

for some function $a(\theta)$.

Two theorems are used to find the **UMVUE**.

* **Rao-Blackwell Theorem** 

Let W be any unbiased estimator of $\tau(\theta)$, and let T be a sufficient statistic for $\theta$. Then $E(W \vert T)$ is a UMVUE.

* **Lehmann Scheffe Theorem**

Suppose there exists a sufficient and complete statistic T for $\theta$. If there exisits unbiased estimator of $\tau(\theta)$, then the UMVUE takes the form of h(T), where h is a Borel function.

It is also noted that UMVUE is **unique**.














