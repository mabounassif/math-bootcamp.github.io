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
there we will bring everything together by applying those notions in topics
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

$$
\begin{align}
    \text{Sum rule: } & \boxed{\frac{d}{dx}(u + v) = \frac{du}{dx}+ \frac{dv}{dx}} \\\\
    \text{Product rule: } & \boxed{\frac{d}{dx}(uv) = \frac{du}{dx}v+ u\frac{dv}{dx}} \\\\
    \text{Chain rule: } & \boxed{\frac{d}{dx}(u \circ v) = \frac{du}{dv} \frac{dv}{dx}}
\end{align}
$$
