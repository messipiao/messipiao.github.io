---
layout: post
title: "Hypothesis Testing"
date: 2013-11-24 10:47
comments: true
categories: Statistics
---

Hypothesis testing is another inference method comparing to point estimator. It is a statement about a population parameter. 

> The two complementaty hypotheses in a hypothesis testing problem are called the *null hypothesis* and the *alternative hypothesis*. They are denoted by *$H_0$* and *$H_1$*, respectively.

## Methods of Finding Tests

### Likelihood Ratio Tests

* The likelihood ratio test statistic for testing $$H_0:\theta \in \Theta_0$$ versus $$H_1:\theta \in \Theta_0^c$$ is 

$$\lambda(\mathbf{x}) = \frac{\sup_{\Theta_0} L(\theta \vert \mathbf{x})}{\sup_{\Theta} L(\theta \vert \mathbf{x})}$$

A likelihood ratio test (**LRT**) is any test that has a rejection region of the form $$\{\mathbf{x}:\lambda(\mathbf{x}) \le c\}$$ where c is any number satisfying $$0 \le c \le 1$$.

* If $$T(\mathbf{X})$$ is a sufficient statistic for $\theta$ and $$\lambda'(t)$$ and $$\lambda(\mathbf{x})$$ are the LRT statistics based on $T$ and $\mathbf{X}$, respectively, then $$\lambda'(T(\mathbf{X})) = \lambda(\mathbf{x})$$ for every $\mathbf{x}$ in the sample space.

<!--more-->

### Bayesian Tests

In a hypothesis testing problem, the posterior distribution may be used to calculate the probabilities that $H_0$ and $H_1$ are true. Remember, $$\pi(\theta \vert \mathbf{x})$$ is probability distribution for a random variable. Hence, the posterior probabilities $$P(\theta \in \Theta_0 \vert \mathbf{x}) = P(H_0 \text{is true} \vert \mathbf{x})$$ and $$P(\theta \in \Theta^c_0 \vert \mathbf{x}) = P(H_1 \text{is true} \vert \mathbf{x})$$ may be computed. 

One way a Bayesian hypothesis tester may choose to use the posterior distribution is to decide to accept $$H_0$$ as true if $$P(\theta \in \Theta_0 \vert \mathbf{X}) \ge P(\theta \in \Theta^c_0 \vert \mathbf{X})$$ and to reject $$H_0$$ otherwise. Another way is to reject $$H_0$$ only if $$P(\theta \in \Theta_0^c \vert \mathbf{X})$$ is greater thatn some large number, 0.99 for example.

### Union-Intersection and Intersection-Union Tests

* **Union-Intersection method**

$$H_0: \theta \in \bigcap_{\gamma \in \Gamma} \Theta_{\gamma}$$

Then the rejection region for the union-intersection test is

$$\bigcup_{\gamma \in \Gamma} \{\mathbf{x}:T_{\gamma}(\mathbf{x}) \in R_{\gamma}\}$$

* **Intersection-Union method**

$$H_0: \theta \in \bigcup_{\gamma \in \Gamma} \Theta_{\gamma}$$

Then the rejection region for the intersection-union test is

$$\bigcap_{\gamma \in \Gamma} \{\mathbf{x}:T_{\gamma}(\mathbf{x}) \in R_{\gamma}\}$$

## Methods of Evaluating Tests

### Power Function

A hypothesis test might make one of two types of errors, namely Type I Error and Type II Error. If $$\theta \in \Theta_0$$ but the hypothesis test incorrectly decides to reject $$H_0$$, then the test has made a Type I Error. If, on the other hand, $$\theta \in \Theta_0^c$$ but the test decides to accept $$H_0$$, a Type II Eroror has been made.

> The power function of a hypothesis test with rejection region R is the function of $\theta$ defined by **$$\beta(\theta) = P_{\theta}(\mathbf{X} \in R)$$**.

For a fixed sample size, it is usually impossible to make both types of error probabilities arbitrarily small. In searching for a good test, it is common to restrict consideration to tests that control the Type I Error probability at a specified level. Within this class of tests we then search for tests that have Type II Error probability that is as small as possible. The following two terms are useful when discussing tests that control Type I Error probabilities.

* For $$0 \le \alpha \le 1$$, a test with power function $$\beta(\theta)$$ is a size $\alpha$ test if $$\sup_{\theta \in \Theta_0} \beta(\theta) = \alpha$$.
* For $$0 \le \alpha \le 1$$, a test with power function $$\beta(\theta)$$ is a level $\alpha$ test if $$\sup_{\theta \in \Theta_0} \beta(\theta) \le \alpha$$.

> A test with power function $$\beta(\theta)$$ is **unbiased** if $$\beta(\theta') \ge \beta(\theta'')$$ for every $$\theta' \in \Theta_0^c$$ and $$\theta'' \in \Theta_0$$.

### Most Powerful Tests

> Let C be a class of tests for testing $$H_0:\theta \in \Theta_0$$ versus $$H_1 : \theta \in \Theta_0^c$$. A test in class C, with power function $$\beta(\theta)$$, is a *uniformly most powerful*(**UMP**) class C test if $$\beta(\theta) \ge \beta'(\theta)$$ for every $$\theta \in \Theta^c_0$$ and every $$\beta'(\theta)$$ that is a power function of a test in class C.

If the class C is the class of all level $\alpha$ tests, then the test described above is called a **UMP level $\alpha$ test**.

**Neyman-Pearson Lemma** describes which tests are UMP level $\alpha$ tests in the situation where the null and alternative hypotheses both consist of only one probability distribution for the sample (that is, when both $$H_0$$ and $$H_1$$ are simple hypotheses).

* **Neyman-Pearson Lemma**

Consider testing $$H_0:\theta = \theta_0$$ versus $$H_1:\theta = \theta_1$$, where the pdf or pmf corresponding to $\theta_i$ is $$f(\mathbf{x} \vert \theta_i)$$, $$i=0,1$$, using a test with rejection region R that satisfies

$$\mathbf{x} \in R ~ if ~ f(\mathbf{x} \vert \theta_1) > kf(\mathbf{x} \vert \theta_0)$$

(1) and

$$\mathbf{x} \in R^c ~ if ~ f(\mathbf{x} \vert \theta_1) < kf(\mathbf{x} \vert \theta_0)$$

for some $$k \ge 0$$, and 

(2) 

$$\alpha = P_{\theta_0}(\mathbf{X} \in R)$$

Then

1. **(Sufficiency)** Any test that satisfies (1) and (2) is a **UMP level $\alpha$ test**.
2. **(Necessity)** If there exists a test satisfying (1) and (2) with $$k > 0$$, then every **UMP level $\alpha$ test** is a size $\alpha$ test (satisfies (2)) and every **UMP level $\alpha$ test** satisfies (1) except perhaps onon a set A satisfying $$P_{\theta_0}(\mathbf{X} \in A) = P_{\theta_1}(\mathbf{X} \in A) = 0$$.

Note that replace $\mathbf{x}$ by a sufficient statistic $T(\mathbf{x})$ can lead to a same conclusion(applying **Factorization Theorem**).

Hypotheses, such as $$H_0$$ and $$H_1$$ in the **Neyman-Pearson Lemma**, that specify only one possible distribution for the sample $\mathbf{X}$ are called *simple hypotheses*. In most realistic problems, the hypotheses of interest specify more than one possible distribution for the sample. Such hypotheses are called *composite hypothese*. 

* $$H:\theta \ge \theta_0$$ or $$\theta < \theta_0$$ is called *one-sided* hypotheses.
* $$H:\theta \ne \theta_0$$ is called *two-sided* hypotheses.

A large class of problems that admit **UMP level $\alpha$** tests involve one-sided hypotheses and **pdfs or pmfs** with the **monotone likelihood ratio property**.

> A family of pdfs or pmfs $$\{g(t \vert \theta):\theta \in \Theta\}$$ for a univariate random variable T with real-valued parameter $\theta$ has a *monotone likelihood ratio* (**MLR**) if, for every $$\theta_2 > \theta_1$$, $$g(t \vert \theta_2)/g(t \vert \theta_1)$$ is a monotone (nonincreasing or nondecreasing) function of t on $$\{t:g(t \vert \theta_1)>0 ~or~ g(t \vert \theta_2)>0\}$$. Note that c/0 is defined as $\infty$ if $c>0$.

* Many common families of distribution have an *MLR*. For example, the normal (known variance, unknown mean). Poisson, and binomial all have an MLR. 
* Any regular exponential family with $$g(t \vert \theta) = h(t)c(\theta) e^{w(\theta)t}$$ has an *MLR* if $$w(\theta)$$ is a nondecreasing function.

* **Karlin-Rubin Theorem**

Consider testing $$H_0:\theta \le \theta_0$$ versus $$H_1: \theta > \theta_0$$. Suppose that T is a sufficient statistic for $\theta$ and the family of pdfs or pmfs $$\{g(t \vert \theta):\theta \in \Theta\}$$ of T has an *MLR*. Then for any $$t_0$$, the test that rejects $$H_0$$ if and only if $$T > t_0$$ is a **UMP level $\alpha$ test**, where $$\alpha = P_{\theta_0}(T>t_0)$$.










