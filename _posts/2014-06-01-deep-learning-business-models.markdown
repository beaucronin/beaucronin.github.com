---
permalink: deep-learning-business-models.html
title: Deep Learning Business Models
layout: post

---

The DeepMind acquisition was the starting gun for a deep learning startup goldrush. Most of the new companies are driven by the assumption that there is a big opportunity in bringing deep learning “to the masses” - i.e., all of the companies and startups that could benefit from the technology, but don’t have the in-house expertise that Google, Facebook, Yahoo, and Microsoft do. 

I think they key issues are as follows:

1. Deep learning requires very large training sets, and these shouldn't be shipped around a lot.

2. No one knows which applications deep learning will dominate: maybe just the ones it's already doing well, maybe a few additional ones, maybe a large number. This has a big effect on business model, and there is real uncertainty here.

3. Lots of experience is required in getting deep learning to work well on a given application; the people who can do it well are those who have been at it for a while, and they tend to come from a handful of places. This will change, but the rate of diffusion of expertise is unknown and will also have an impact on business options.

Here is a brief tour of the different models; I know of companies in each category, but I won’t name names since some of them are unannounced.

- **Sell hardware**. With the death of single-core speed improvements, startups in a number of areas are exploring alternative (i.e., non-von Neumann) computing architectures; deep learning is no exception. 

	The real competition here is GPUs, which benefit from the same economies of scale that have kept mainstream architectures dominant for so long, and which are emerging as the consensus compute platform for scaled deep learning. Deep learning-optimized chips may well have performance advantages at the margins, but they’ll be much more expensive and harder to deploy for quite some time; it’s really tough to beat the cost and convenience of dialing up AWS GPU instances.

	Of course, a startup with new chip technology could use it in-house to execute on one of the other business models below, but it’s unusual for a founding team with that level of hardware chops to follow those paths - the instinct will be to just sell the chips they’ve created (or, more accurately, the IP behind those chips).

	A team that succeeds in developing a successful architecture would be a natural acquisition target for on of the big deep learning players.
	
- **Open source plus services**, a la Redhat or Cloudera. Offer deep learning software for free, and charge for training and consulting. This is made more enticing by the fact that Torch7, widely used at the big deep learning companies, is open source; why not make it more accessible? I see a couple challenges here.

	First, are there sufficiently many applications and workloads for deep learning to support this approach? My hunch is no - that deep learning as currently conceived will prove dominant in a few areas. What happens when another approach is better - say, random forests? I.e., why build a company committed to just this ML method?

	Second, it’s not enough to just put a high-quality open source implementation in developers’ hands. Deep learning requires a ton of tuning and tweaking, and getting good results is as much art as science. This expertise gap might be closed with professional services, but then the challenge shifts to scaling that operation.

- **Hosted API, “Deep Learning as a Service”**. This is an API-driven operation: customers upload their data, train a deep learning model, and then send queries. This model has the advantage that a lot of usability, tuning and scale-out problems can be solved once-and-for-all for customers. Customers would be charged for usage, either directly or by tiers.

	One major concern is that deep learning training sets are very large, and the resulting data gravity will be a challenge. I.e., the shape of the data flows make this a hard sell.

	Another concern, a more general one, is that it’s very hard to price discriminate in order to capture the value provided. If one customer is is financial services and another in consumer web, you’d like to charge the money folks more without pricing the others out, but this is hard to make work.

- **Individual deep learning services**. In this case, the startup gathers data and trains a deep learning model itself, and then offers queries as a service. For example, the company might offer image tagging as a service: the user provides an image, and is given labels that describe it. 

	The obvious challenge here is that deep learning is by definition only being applied to the problems that it is known to solve well, and there are no natural barriers to entry - so it’s likely that these capabilities will tend towards free. These features will quickly become table stakes.

There’s lots more to say, but this is one of those cases where I’ll never get this out if I don’t post it as-is.

Tell me what you think on [twitter](http://twitter.com/beaucronin).