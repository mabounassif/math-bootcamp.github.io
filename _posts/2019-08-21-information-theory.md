---
layout:     post
title:      Information Theory
date:       2019-07-23 12:22:18
summary:    Quick introduction to Information Theory.
categories: machinelearning basics
---

> As Jenny walks into a room, someone yells out "145!" and then the whole room
> starts laughting.
> Perplexed, Jenny tried to make sense of what just happened, she picked up a
> pamphlet from the front table and took the first available seat she could
> find. Moments
> later another person yells "256!" and again the whole room erupts into
> laughter, including Jenny.

---
Generative Adversarial Networks (GANs), were first introduced by Ian Goodfellow
back in 2014. Estimating the mutual information as part of an adversarial game
between competing deep neural networks is at the cornerstone of GANs. In this
post, we will give a short introduction of the fundamentals of Information
Theory in order to help with the understanding. We will introduce information,
shannon-entropy, cross-entropy, relative entropy and mutual information. From
there we will bring everything together by applying those notions in topics
related to machine learning.


<a href="https://colab.research.google.com/drive/1pD4Lnr1Gs8S3KiUT86D1zZzpWlHOBWRQ" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>


## Calculating Gradients, Analytically

> ``In a [recent article](https://dl.acm.org/citation.cfm?id=364791) R. Wengert suggested a technique for machine evaluation of the partial derivatives of a function given in analytical form [that] appears very attractive from the programming viewpoint and permits the treatment of large systems of differential equations which might not otherwise be undertaken.''
>
> --Richard E. Bellman (1964) [^5]

Numerical approaches tell us the approximate sensitivity of a function with respect to its inputs at a single point. Symbolic differentiation gives us a closed-form expression for the derivative at any point in its input.

In calculus, we are taught many rules for symbolic differentiation. These rules are convenient identities to remember, but almost all differential calculus can be recovered from three simple rules for scalar differentiation:

$$
\begin{align}
    \text{Sum rule: } & \boxed{\frac{d}{dx}(u + v) = \frac{du}{dx}+ \frac{dv}{dx}} \\\\
    \text{Product rule: } & \boxed{\frac{d}{dx}(uv) = \frac{du}{dx}v+ u\frac{dv}{dx}} \\\\
    \text{Chain rule: } & \boxed{\frac{d}{dx}(u \circ v) = \frac{du}{dv} \frac{dv}{dx}}
\end{align}
$$

The same notion which appears in the differential calculi can be applied in many different contexts from [regular expressions](http://maveric.uwaterloo.ca/reports/1964_JACM_Brzozowski.pdf) to [λ-calculus](https://www.sciencedirect.com/science/article/pii/S030439750300392X) to [linear logic](https://arxiv.org/abs/1805.11813). In machine learning, we are chiefly interested in calculating derivatives for vector fields or some mechanical representation thereof. As long as a number system admits the standard arithmetic notation (addition, multiplication and their inverses), it is possible to symbolically derive an expression which, when evaluated at a point, will equate to the finite difference approximation.

We make the following two claims:

1. Symbolic differentiation can be performed mechanically by replacing the expressions on the left hand side with their right hand side equivalents. This process often requires less computation than the numerical method [described above](#calculating-gradients-numerically).
2. The same rules can be applied to functions whose inputs and outputs are vectors, with exactly the same algebraic semantics. Using matrix notation requires far less computation than elementwise scalar differentiation.

Firstly, let us examine the first claim. A naïve implementation of the finite difference method requires at least two evaluations each time we wish to compute the derivative at a certain input. While algebraic rewriting can help to reduce the computation, but we are still left with the $$\lim_{h\rightarrow 0}$$. It is often more efficient to derive a closed form analytical solution for the derivative at every input.

Secondly, partial differentiation of vector functions is a specific case of higher dimensional derivatives that are often more convenient to represent as a matrix, or _Jacobian_, which is defined as follows: 

$$
\mathcal{J}_{\mathbf{f}} = 
\begin{bmatrix}
    \dfrac{\partial \mathbf{f}}{\partial x_1} & \cdots & \dfrac{\partial \mathbf{f}}{\partial x_m}
\end{bmatrix} =
\begin{bmatrix}
    \dfrac{\partial f_1}{\partial x_1} & \cdots & \dfrac{\partial f_1}{\partial x_m}\\
    \vdots & \ddots & \vdots\\
    \dfrac{\partial f_n}{\partial x_1} & \cdots & \dfrac{\partial f_n}{\partial x_m} 
\end{bmatrix} =
\begin{bmatrix}
    \nabla f_1 \\
    \vdots \\
    \nabla f_m
\end{bmatrix}
$$

The matrix representation often requires far less memory and computation than a naïve implementation which iteratively computes derivatives for each element of a vector function.

TODO: give an example

