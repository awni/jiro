---
layout: post
title: "Squared error."
date: 2017-01-10
categories: [practice]
tags: [loss functions]
difficulty: 2
---

### Problem ###

One of the most commonly used algorithms in machine learning is linear
regression.  The loss function used in linear regression is the squared error
given by
\begin{align}
\mathcal{L}(X,y) = \frac{1}{2} ||X^T \theta - y||^2 = \frac{1}{2} \sum\_{i=1}^n (\theta^T x\_i - y\_i)^2.
\end{align}
where $$n$$ is the number of examples, $$x_i$$ are the columns of the matrix
$$X$$ and $$y_i$$ are the elements of the vector $$y$$.

Assume the targets are generated via a linear transformation of the inputs and
some zero-mean Gaussian noise. In other words
\begin{align}
y\_i = \theta^T x\_i + \epsilon\_i
\end{align}
where $$\epsilon_i \sim \mathcal{N}(0, \sigma^2)$$.

Show that maximizing the [likelihood] of the parameters $$\theta$$ is equivalent
to minimizing the squared error above.

### Solution ###
<a id='answer-toggle' href="#" onclick="toggleDiv()">show</a>

<div id="answer-block"  style="display:none;" markdown="1">
First note that $$\epsilon_i = y_i - \theta^T x_i$$. This says that the
difference between the ground truth $$y_i$$ and the prediction $$\theta^T x_i$$
follows a zero-mean Gaussian distribution. Alternatively $$y_i \sim
\mathcal{N}(\theta^T x_i, \sigma^2)$$.

The likelihood of the parameters is thus given by
\begin{align}
P\_{\theta}(y | X) &= \prod\_{i=1}^n \mathcal{N}(y\_i;  \theta^T x\_i, \sigma^2) \\\
&= \prod\_{i=1}^n \frac{1}{\sqrt{2\pi}\sigma} \exp\left( -\frac{(y\_i - \theta^T x\_i)^2}{2\sigma^2} \right)
\end{align}

Rather than maximizing the likelihood, we can minimize the negative
log-likelihood. Recall $$\log$$ is monotonic and increasing thus does not
change the value of $$\theta$$ which optimizes the function. Thus we have

\begin{align}
-\log P\_{\theta}(y | X) &= - \sum\_{i=1}^n \log \frac{1}{\sqrt{2\pi}\sigma} \exp\left( -\frac{(y\_i - \theta^T x\_i)^2}{2\sigma^2} \right) \\\
&= - n \log \frac{1}{\sqrt{2\pi}\sigma} - \sum\_{i=1}^n \left( -\frac{(y\_i - \theta^T x\_i)^2}{2\sigma^2} \right) \\\
&= - n \log \frac{1}{\sqrt{2\pi}\sigma} + \frac{1}{2\sigma^2} \sum\_{i=1}^n (y\_i - \theta^T x\_i)^2 \\\
&=  a + \frac{b}{2} \sum\_{i=1}^n (y\_i - \theta^T x\_i)^2
\end{align}
where $$a = - n \log \frac{1}{\sqrt{2\pi}\sigma}$$ and $$b = \frac{1}{\sigma^2}$$.

The constants $$a$$ and $$b$$ also do not effect the value of $$\theta$$ which
optimizes the function, thus we are left with the equivalent problem of
minimizing
\begin{align}
\frac{1}{2} \sum\_{i=1}^n (y\_i - \theta^T x\_i)^2
\end{align}
which is precisely the squared error objective function.
</div>

[likelihood]: https://en.wikipedia.org/wiki/Likelihood_function

