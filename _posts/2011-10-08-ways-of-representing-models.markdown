---
title: Different ways of representing generative models
permalink: representing-generative-models
layout: post
published: True

---
# Ways of Representing Generative Models

Generative models can be represented in several ways, each with its own strengths and weaknessed. This post will show four different ways to denote a simple model, the **Beta-Bernoulli**. Informally, this model describes a situation in which there are N flips of a coin, where that coin need not be "fair" but can have any probability between 0 and 1 of coming up heads on each flip. Note that the weight of the coin does not change from one flip to the next, and each flip is independent of all the others (i.e., the chance of heads on a given flip is not affected by how the previous flips turned out).

## Prose

- Set the parameters of the Beta distribution, `alpha` and `beta`, both to 1.0
- Draw a weight `p` as a random sample the [Beta](http://mathworld.wolfram.com/BetaDistribution.html) distribution with these paramters
- For each of `N` observations, index by `i`:
  - Perform a [Bernoulli](http://mathworld.wolfram.com/BernoulliDistribution.html) trial with probability `p` to produce the observation `x_i`

In many situations, a semi-formal prose description of the model serves well.  It can provide some intuition for the structure of the model, and with care these specifications can be used even more models of considerable complexity. Of course, we cannot read off the formal or structural properties of the model without extra work, sometimes considerable. For this reason, prose descriptions are best paired with another representation.

## Distributions

    alpha = 1.0
    beta  = 1.0
    p     ~ Beta(alpha, beta)
    x_i   ~ Bernoulli(p)

This form is close to how statisticians represent models.  It emphasizes the probability distributions that are used, and the values that parameterize each one. When models become more complex, however, it becomes increasingly difficult to keep track of the relationships. Also, because the overall structure of the model is hidden, this notation doesn't provide much help in formulating inference strategies.

## Directed Graphical Model

![image](img/Beta_Bernoulli_DGM.png)

This representation emphasizes the dependencies between the variables in the model, but it elides the nature of the relationship between them.  Looks at the graphical model, we do not even know that `p` is produced from a Beta distribution, or the the `x_i` are produce by Bernoulli draws. On the other hand, we can read off the fact that the `x_i` are **conditionally independent** of `alpha` and `beta`, once `p` has been chosen. These kinds of (in)dependency relationships can be helpful when we are implementing inference for a particular model.

Graphical models are popular in the machine learning community, and [for good reason](http://www.cs.ubc.ca/~murphyk/Bayes/bnintro.html). While they have considerable expressive power, though, they run into trouble with highly nested or cross-cutting models, as well as in models where the number of variables is not fixed at the outset.

## Program

{% highlight python %}

  alpha = 1.0
  beta = 1.0
  N = 10
  p = betarnd(alpha, beta)
  x = []
  for i in range(N):
    x.append(bernrnd(p))

{% endhighlight %}

Writing a generative model as a program is clearly the most expressive option, and it is increasingly viewed as the method of choice when the complexity or number of latent variables in the model is learned from the data. There is no universally agreed-upon syntax, however, and it may take longer to read and understand a model expressed in this form compared to the more constrained representations shown above.

As a side note, an active and growing research community is developing [probabilistic programming languages](http://probabilistic-programming.org/) and associated runtime environments; the goal of these systems is to automatically perform inference on the latent variables in models specified in programs like this one. While work on these languages is rapid and promising, at the time of this writing their performance in most domains is not competitive to the more traditional means of writing inference programs.