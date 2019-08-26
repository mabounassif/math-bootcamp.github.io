---
layout:     post
title:      Information Theory
date:       2019-07-23 12:22:18
summary:    Quick introduction to Information Theory.
categories: machinelearning basics
---

> As Jenny walks into a room, someone yells out "145!" and then the whole room
> starts laughting.
> Perplexed, Jenny tries to make sense of what just happened, she picks up a
> pamphlet from the front table and takes the first available seat she could
> find. Moments
> later another person yells "256!" and again the whole room erupts into
> laughter, including Jenny.

---
Generative Adversarial Networks (GANs), were first introduced by Ian Goodfellow
back in 2014. Estimating the mutual information as part of an adversarial game
between competing deep neural networks is at the cornerstone of GANs. In this
post, we will give a short introduction on the fundamentals of Information
Theory in order to help with the understanding. We will introduce information,
shannon-entropy, cross-entropy, relative entropy and mutual information. From
there we will bring everything together by applying these notions in topics
related to machine learning.


<a href="https://colab.research.google.com/drive/1--MtLnkUsyCwkdeVITCEmDxig_EywYbC" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

## Information

> ``Information is the resolution of uncertainty.''
>
> -- Claude Shannon

In 1948, Claude E. Shannon published his famous "A Mathematical Theory of
Communication" paper, which is considered by many academics as the foundational work of
Information Theory. The mathematician lays down simply the problem he is trying
to solve: the fundamental problem of communication. He defines it as the challenge of
reproducing at one point either exactly or approximately a message selected at
another point. A typical obstacle during WW2 while transmitting vital messages
to allies accross the atlantic ocean.

Formally, "information" is thought of as a set of possible messages, where the
goal is to send these messages over a noisy channel, and then to have the
receiver reconstruct the message with low probability error, in spite of the
channel noise.

## Entropy

Randomness is quite an abstract concept yet it manifests itself all around us
 all the time. For instance, it appears when we ask questions like: what are the
 chances that a brisk of air rolls a pen off the
table? How likely can a career in acting be succesful? 

All of these scenarios are different, yet we can somehow discribe them in the same framework of
"randomness". In order words, whatever "randomness" is, let's put it under a glass
dome and observe it. We will quickly notice that each dome  has universal subtleties that can make it unique and
different. We can also operate on them, we can compare
them, we can measure them etc...

Let us give the glass dome a more technical term and define it as
a random variable. Hence, entropy allows us to quantify the uncertainty of
a random variable. The higher the entropy the more "random" is the random
variable.


Formally, entropy \\(H(X)\\) of a discrete random variable \\(X\\) is:

\begin{equation}
  H(X) = - \sum_{x \in \varkappa}{p(x)\log{p(x)}}
\end{equation}

where \\(\varkappa\\) is the set containing all possible values of the random variable \\(X\\) 
and \\(p\\) is the probability density function of \\(X\\).
The log is to the base 2 and entropy is expressed in bits. We can rewrite the above as:

\begin{equation}
  H(X) = E_{p} \log{\frac{1}{p(X)}}
\end{equation}
