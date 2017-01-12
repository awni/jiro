---
layout: post
title: "Logistic regression."
date: 2017-01-11
categories: [practice]
tags: [loss functions]
difficulty: 1
---

### Problem ###

The loss function for a single example label pair $$(x, y)$$ in logistic
regression can be written as
\begin{align}
\mathcal{L}(\theta) = y\log \sigma(\theta^Tx) + (1 - y) \log (1-\sigma(\theta^Tx))
\end{align}
where $$x \in \mathbb{R}^n$$ and $$y \in \{0,1\}$$ and $$\sigma(\cdot)$$ is the
sigmoid function.

Show that the gradient with respect to the parameters $$\theta$$ is given by
\begin{align}
\nabla\_\theta \mathcal{L}(\theta) = (y - \sigma(x)) x.
\end{align}

### Solution ###
<a id='answer-toggle' href="#" onclick="toggleDiv()">show</a>

<div id="answer-block"  style="display:none;" markdown="1">
<!---
First let $$z = \theta^T x$$ and take the derivative
$$\frac{d}{dz}\mathcal{L}(\theta)$$. This gives

\begin{align}
\frac{d}{dz} \mathcal{L}(\theta) &= \frac{y}{\sigma(z)}\frac{d}{dz}\sigma(z) - \frac{(1 - y)}{(1-\sigma(z))} \frac{d}{dz}\sigma(z) \\\
&= \frac{y}{\sigma(z)}\sigma(z)(1-\sigma(z)) - \frac{(1-y)}{(1-\sigma(z))} \sigma(z) (1-\sigma(z)) \\\
&= y(1-\sigma(z)) - (1-y)\sigma(z) \\\
&= y - \sigma(z) \\\
\end{align}

We used the identity $$\frac{d}{dz}\sigma(z) = \sigma(z)(1-\sigma(z))$$ from an
earlier [problem]. Now to compute the derivative w.r.t $$\theta$$ we just apply
the chain rule
\begin{align}
\nabla\_\theta \mathcal{L}(\theta) &= \frac{d}{dz}  \mathcal{L}(\theta) \nabla\_\theta (\theta^Tx) \\\
&= (y - \sigma(z)) x
\end{align}
-->
</div>

[problem]: {% post_url 2017-01-06-warm-up %} 
