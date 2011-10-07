---
permalink: metropolis-sampling-made-easy.html
title: Metropolis sampling made easy
layout: post

---

# Metropolis Sampling Made Easy

## Introduction
Metropolis is a key member of a family of inference methods that collectively go by Markov chain Monte Carlo (**MCMC**).[^1]  At core, Metropolis sampling is very simple -- it can be implemented in just a few lines of code. But this basic recipe can be adapted and remixed to achieve very sophisticated and powerful probabilistic inference.

MCMC is one of general approach to sampling.[^4] In general, it can be very hard to draw random samples from complex, high-dimensional probability distributions. MCMC methods get around this by taking a random walk through the space defined by the parameters of the distribution in question. Through the miracle of **detailed balance**, they guarantee that - if run long enough - they will explore the space in proportion to its probability density.

After reading this article and playing with the accompanying code, you should:

- Be able to implement your own version of the Metropolis sampling algorithm
- Understand the key elements in the algorithm (the target and proposal distributions, the acceptance rule), and have a sense for how they can and cannot be modified to suit different applications.
- Have a seat-of-the-pants feel for the algorithm's runtime behavior and output.

## Basic Concepts

A Metropolis sampler uses a proposal distribution to move through the parameter space of a target distribution that we want to sample from. Each proposal is accepted or rejected according to the Metropolis acceptance rule.

The **target distribution** is the probability distribution from which you want to draw random samples. While Metropolis sampling can be used in many applications, it is very commonly applied in **Bayesian statistical inference**.  In this setting, the target distribution is usually the **posterior distribution** on the model parameters.  The target distribution is therefore a function of the observed data and the prior distribution on those parameters.

The **proposal distribution** is the most interesting aspect of the Metropolis sampler, because it provides the most room for creativity and insight. As long as some very general requirements on the proposal are met, the sampler will be guaranteed to explore the entire target distribution if it is run long enough. But the key phrase there is *if it is run long enough* -- a sampler with a poorly-chosen proposal scheme will take until the end of time to sample from even a simple target distribution.

The most important requirement of a Metropolis proposal distribution is that it be *symmetric* -- i.e., the probability of moving from `x` to `x*` must be the same as moving from `x*` to `x`.  Our sampler will use a normal distribution centered on the current value of `x`, which does satisfy this requirement. A generalization of the Metropolis sampling algorithm, called Metropolis-Hastings, removes this constraint at the expense of some added complexity in the acceptance rule.

The **acceptance rule**, which evaluates proposals against the target, provides the awesome power of the Metropolis algorithm. Like any good hill-climbing or optimization algorithm, it always moves uphill when it has the chance. But crucially, it also moves downhill some of the time -- with a probability that shrinks with the relative badness of the downhill move.  It turns out that this specific acceptance rule ensures that the sampled chain will, over time, maintain detailed balance.  In a nutshell, this means that the accepted samples will spend time in a given area of parameter sapce in proportion to that area's relative probability. That is, a region A1 which is twice as probable as another A2 will, with sufficient iterations, contain about twice as many samples as A2. Another way of putting it is that the histogram of samples will eventually approximate the shape of the true target distribution to whatever degree of accuracy is required.

## Implementing the sampler
A Metropolis sampler works as follows:

0. Pick a starting point in parameter space
1. Evaluate the target distribution at the current location in parameter space
2. Propose a location to jump to next, and evaluate the target distribution at that new location
3. If the new probability is greater than the current one, accept the proposal and update the current location
4. If the new probability is less than the current one, accept the proposal with probability equal to the ratio of the new probability to the old one; otherwise reject and stay put
5. Goto 1

In pythonic pseudocode, this looks like:

<script src="https://gist.github.com/1258210.js?file=gistfile1.py"></script>

Code for a simple but complete Metropolis sampler is [here](https://github.com/beaucronin/npblog_code/blob/master/examples/metropolis.py). In the next section, we'll take a look at the output of that sampler, as plotted with some [simple matplotlib commands](https://github.com/beaucronin/npblog_code/blob/master/examples/make_metropolis_plots.py).[^3]

## Running the sampler and looking at the output
First, we'll start the sampler at (0, 0) and run it for 10 steps:

![image](img/metropolis/out_1.png)

In this picture and those that follow, each dot represents the location of the parameters at the end of each step. The dashed lines connect subsequent steps, so that you can get a sense for how the sampler is moving around in parameter space from one step to the next. Note that there are fewer dots than steps, because the location does not change on those steps where the proposal is rejected.

Now, as we add more and more steps, we see that the collection starts to approximate the target distribution:

![image](img/metropolis/out_2.png)
![image](img/metropolis/out_3.png)
![image](img/metropolis/out_4.png)
![image](img/metropolis/out_5.png)

In the following figures, I've changed the plotting so that each step is shown by a translucent dot, and the connecting lines are omitted for clarity.[^2] This kind of plot gives a more direct sense of the spatial density of the samples - higher-probabilty regions are darker - and it becomes increasingly obvious that the sampler is providing a better and better approximation of the target distribution:

![image](img/metropolis/out_6.png)
![image](img/metropolis/out_7.png)
![image](img/metropolis/out_8.png)

I've also made a [video of the sampler in action](http://www.youtube.com/watch?v=4I6TaYo9j_Y), which might give a better sense of the dynamics of the sampling process. For the first 30 seconds or so, each video frame corresponds to a single step; then, toward the end, 10 steps are added at a time. At the end of the video, several thousand steps have been plotted.

## Proposals and acceptance rates

![image](img/metropolis/metropolis_jumpsize_0.png)
![image](img/metropolis/metropolis_jumpsize_1.png)
![image](img/metropolis/metropolis_jumpsize_2.png)
![image](img/metropolis/metropolis_jumpsize_3.png)
![image](img/metropolis/metropolis_jumpsize_4.png)
![image](img/metropolis/metropolis_jumpsize_5.png)
![image](img/metropolis/metropolis_jumpsize_6.png)
![image](img/metropolis/metropolis_jumpsize_7.png)


## Next steps: generalizations and extensions

In some sense, we've only scratched the surface of Metropolis sampling, but I don't think that's the best way of looking at it.  In fact, most or all of the elements of samplers are present even in our simple example - the proposal distribution, the target distribution, and the parameters over which inference is performed. Each of these elements can become significantly more complex, but their relationship to one another, and the overall structure of the sampler, remains the same.

That said, here are a few of the ways in which samplers typically become more complex or sophisticated as our demands on them increase - as we try to solve harder and harder problems:

1. The target distribution can become much more complex. In particular, the number of parameters can increase dramatically, meaning that we need to explore a very high-dimensional space. This typically leads to…
2. The proposal distribution becoming more sophisticated. There can be different proposals for different parameters, or the proposals can incorporate more knowledge about the target distribution in order to explore it more efficiently (i.e., cover more "ground" in fewer steps while maintaining a decent acceptance ratio).
3. Choosing a good initial state can become a project unto itself. In high-dimensional situations, the "peaks" of the target distribution can be very hard to find, and using a naive starting point might require many steps to find these regions.
4. Real-world samplers often include several inference techniques in concert. Part of the art of probabilistic inference programming is learning how to use the many available tools strike the right tradeoff between implementation effort and computational efficiency, and learning to mix and match as needed. Metropolis sampling is one of these basic tools, but there are some other important ones as well.

## References and Resources

- The [original Metropolis sampling paper](http://home.gwu.edu/~stroud/classics/Metropolis53.pdf) - check out the author list!
- The code for this post can be found [here](https://github.com/beaucronin/npblog_code). Happy hacking!
- numpy, scipy, and matplotlib can be a real pain to get working on Mac OS; I've found that Chris Fonnesbeck's [scipy Superpack](http://stronginference.com/scipy-superpack/) is *the* way to get these packages installed on the mac with all the dependencies and versions taken care of. Chris is one the authors of [PyMC](http://code.google.com/p/pymc/), and his [blog](http://stronginference.com/) is a great source of sophisticated commentary on Monte Carlo sampling methods.

## Footnotes

[^1]: MCMC methods are themselves part of the larger family of "Monte Carlo" inference methods, 
      distinguished by their reliance on random exploration of a space of hypotheses.

[^2]: Protip -- The alpha channel is a very useful tool for showing the density of samples.

[^3]: See the resources section for more on installing matplotlib on the mac.

[^4]: Other basic approaches include rejection sampling, importance sampling, and sequential 
      Monte Carlo.
