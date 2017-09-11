---
layout: post
title: "Expected errors in linear regression"
date: 2017-07-29
categories: [practice]
tags: [generalization]
difficulty: 2
---

### Problem ###

We have a training set of $$N$$ examples $$(x_i, y_i)$$ and test set of $$M$$
examples $$(\tilde{x}_i, \tilde{y}_i)$$ both sampled randomly from the same
distribution. Let $$\beta$$ be the parameters which minimize the sum of squared
errors on the training set.

Prove that 

\begin{align}
\mathbb{E} \left[ \frac{1}{N} \sum\_{i=1}^N (\beta^T x\_i - y\_i)^2 \right] \le 
\mathbb{E} \left[ \frac{1}{M} \sum\_{i=1}^M (\beta^T \tilde{x}\_i - \tilde{y}\_i)^2 \right]
\end{align}

where the expectations are taken over the training and test samples.

### Solution ###
<a id='answer-toggle' href="#" onclick="toggleDiv()">show</a>

<div id="answer-block" style="display:none;" markdown="1">

The expectation for a given test example $$\mathbb{E} [ (\beta^T \tilde{x} -
\tilde{y})^2 ]$$ is constant thus the expectation over the test set does not
depend on $$M$$. Without loss of generality we can set $$M = N$$.

Now let $$\tilde{B}$$ be the parameters which minimize the sum of squared errors on the test set. Since the test set comes from the same distribution as the training set we have
\begin{align}
\mathbb{E} \left[ \frac{1}{N} \sum\_{i=1}^N (\beta^T x\_i - y\_i)^2 \right] =
\mathbb{E} \left[ \frac{1}{M} \sum\_{i=1}^M (\tilde{\beta}^T \tilde{x}\_i - \tilde{y}\_i)^2 \right].
\end{align}

Since $$\tilde{\beta}$$ is the minimizer of the sum of squared errors on the test set, we must have 
\begin{align}
\mathbb{E} \left[ \frac{1}{N} \sum\_{i=1}^N (\tilde{\beta}^T \tilde{x}\_i - \tilde{y}\_i)^2 \right] \le 
\mathbb{E} \left[ \frac{1}{M} \sum\_{i=1}^M (\beta^T \tilde{x}\_i - \tilde{y}\_i)^2 \right]
\end{align}

which proves the claim.

</div>

<span class="post-credit">
Credit: This is exercise 2.9 in [Elements of Statistical Learning](http://web.stanford.edu/~hastie/ElemStatLearn/).
</span>
