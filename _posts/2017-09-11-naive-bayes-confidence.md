---
layout: post
title: "Over Confidence in Naive Bayes"
date: 2017-09-10
categories: [practice]
tags: [naive bayes - generative models - classification]
difficulty: 2
---

### Problem ###

One problem with the Naive Bayes classifier is that the confidence of the model
in its predictions can change even when no new information has been gained. 

Let $$p(x_i \mid y)$$ for $$i = 1, \ldots, m$$ and $$p(y)$$ be the probability
distributions defining a Naive Bayes model. There are $$m$$ features and $$y$$
can take on $$n$$ possible classes. Assume the the prior over labels $$p(y)$$
is uniform.

Show that if every feature is repeated exactly once, the model becomes more
confident in its predicted output class for an arbitrary example.

### Solution ###
<a id='answer-toggle' href="#" onclick="toggleDiv()">show</a>

<div id="answer-block" style="display:none;" markdown="1">

Let $$j$$ be the index of the class label that the Naive Bayes model predicts
for a given example. In this case

\begin{align}
\prod\_{i=1}^m p(x_i \mid y = j)p(y=j) > \prod\_{i=1}^m p(x_i \mid y = k)p(y=k) \quad \text{for} \quad k \ne j.
\end{align}
Since the prior is uniform we have
\begin{align}
\texttt{(1)} \quad \prod\_{i=1}^m p(x_i \mid y = j) > \prod\_{i=1}^m p(x_i \mid y = k) \quad \text{for} \quad k \ne j.
\end{align}

Now consider probability given to the same label $$j$$ by the model with every
output feature repeated:

\begin{align}
&\frac{\prod\_{i=1}^m p(x_i \mid y = j)^2 p(y=j)}{\sum\_{k=1}^n \prod\_{i=1}^m p(x_i \mid y = k)^2 p(y=k)} \\\
&= \frac{\prod\_{i=1}^m p(x_i \mid y = j)^2 }{\sum\_{k=1}^n \prod\_{i=1}^m p(x_i \mid y = k)^2} \\\
&\ge \frac{\prod\_{i=1}^m p(x_i \mid y = j)^2 }{\sum\_{k=1}^n \prod\_{i=1}^m p(x_i \mid y = k)p(x_i \mid y = j)} \\\
&\ge \frac{\prod\_{i=1}^m p(x_i \mid y = j) }{\sum\_{k=1}^n \prod\_{i=1}^m p(x_i \mid y = k)}
&\end{align}

This shows that the probability for the prediction $$y=j$$ given by the new
model is greater or equal to the probability given by the old model. The first
step is using the fact that $$p(y)$$ is uniform. The second step is using the
inequality `(1)` from above.
</div>

<span class="post-credit">
This fact was pointed out to me in Section 2.2.3 of [An Introduction to
Conditional Random
Fields](http://homepages.inf.ed.ac.uk/csutton/publications/crftut-fnt.pdf).
</span>
