---
permalink: machine-learning-companies.html
title: Machine Learning Companies
layout: post

---

# Machine Learning Companies

I've helped build two machine learning companies in the last few years. It's hard to do: ML is temperamental technology, and while it's pretty straightforward for talented data scientists and engineers to execute one-off projects, the methods themselves are difficult to productize. For this and other reasons, it's tough to build a scalable business around machine learning itself.

But this hasn't stopped a lot more people from trying recently, so I thought I'd write up some notes to describe how I think about this space now.

First, though: What do I mean by an "ML company"? Roughly, it's a company whose core product offering provides value by learning from data, with the eventual goal of discovering valuable patterns, predicting something interesting about the future, recommending or prioritizing people or content, or guiding actions.

I'll restrict this discussion to efforts that are addressed to "business data", broadly conceived: standard tabular and relational data, free text, commercial transactions, location, logs, web behaviors, social network posts, and even some sensor readings. I *will* discuss non-commercial offerings such as open-source ML frameworks, because many startups in this space are effectively competing against these kinds of free projects.

I'll exclude "perceptual" systems focused on vision, spoken language understanding, as well as robotics and drones. I'm also excluding companies that use ML to build their product, but for whom the business itself is in some other area - as illustration, I would put both [Prismatic](http://getprismatic.com/) and [Premise Data](http://www.premise.com/) in this category. Finally, I'll also leave aside the exciting internal ML efforts at companies like Google, Facebook, and Microsoft.

I think the first thing to ask about a project or company is whether its offerings address business or technical problems. Of course, in the right context, some technical problems really *are* business problems, but I still think this is a useful initial discriminator. Why? Because it really helps to get at who the potential customer might be. No business of any size wants to buy "machine learning", or has a machine learning budget. Companies conceive of their problems in business terms, and they want to spend money to solve those problems. This is why vendors have that tab called "solutions" at the top of their website, even though they're really selling products.

## Kinds of machine learning offerings

The last five years has seen a lot of action in this area, and it's only accelerating. 

Here's how I break these offerings down.

* **Open source ML libraries**. Examples include [scikit-learn](http://scikit-learn.org/stable/), [h2o](http://0xdata.com/h2o-2/), [kiji](http://www.kiji.org/), [Mahout](http://mahout.apache.org/), [Spark MLlib](http://spark.incubator.apache.org/docs/latest/mllib-guide.html), [vowpal wabbit](https://github.com/JohnLangford/vowpal_wabbit/wiki), and [graphlab](http://graphlab.org/). These are used by engineering-inclined data scientists and algorithmically-sophisticated developers to both perform one-off analyses and to build production data products (as one part of a larger data engineering stack).

    These projects can either be truly non-profit enterprises (scikit-learn), closely affiliated with - even say captive to - a single company with accompanying commercial interests (h2o and [0xdata](http://0xdata.com/)), or seemingly somewhere in between ([GraphLab](http://graphlab.com/)). These nature of these company/project relationships is not always clear at first blush.

    Another way to differentiate these libraries is whether they are largely "stand-alone", like scikit-learn, or instead rest on top of a more complete big data analytics stack (Mahout, Cloudera ML, and h20 on hadoop; MLlib on Spark).

* **Technical and statistical computing environments**. Examples include R, SAS, SPSS, and the newcomer Julia. These are true computing environments that include a complete programming language, and which are extensible by writing code packages. Graphical workbenches are available for each of them, and some of these interfaces eliminate  the need to write code at all. These systems exist as both free/open source (R, Julia) and commercial (SAS, SPSS) offerings.

* **Machine Learning as a Service (MLaaS)**. Examples include [BigML](https://bigml.com/), [wise.io](http://about.wise.io/), [etcml](http://www.etcml.com/), [AlchemyAPI](http://www.alchemyapi.com/), [PredictionIO](http://prediction.io/), [SwiftIQ](http://www.swiftiq.com/), the [Google Prediction API](https://developers.google.com/prediction/), and [GraphLab Notebook](https://beta.graphlab.com/). These offerings are distinguished by the fact that they live "in the cloud". They attempt to reduce complexity relative to ML libraries in two ways. First, they provide the basic value proposition as other SaaS offerings: namely, no need to deal with server scale out infrastructure administration. But second, to varying degrees they sand the rough edges off the machine learning workflow provided by traditional libraries and frameworks.

    MLaaS offerings may or may not offer multiple ML techniques (say, logistic regression vs. random forests), and they differ on whether the user even knows (or cares) which methods underlie their capabilities. Depending on where they fall on this "black-box" spectrum, an offering may therefore reduce the level of expertise needed relative to libraries, which typically do not provide this kind of encapsulation. But the fundamental interface to these services is still a technical one - an API that must be integrated into another application or business process in order to realize business value.

* **Bayesian hierarchical modeling and probabilistic programming systems**: This is an emerging segment, immature relative to traditional machine learning, and sure to see lots of technical innovation in the coming 2-3 years. Current examples include [PyMC](http://pymc-devs.github.io/pymc/), [STAN](http://mc-stan.org/), and [Infer.net](http://research.microsoft.com/en-us/um/cambridge/projects/infernet/). 

   While there are no existing commercial offerings in this area (though see [BayesHive](http://bayeshive.com/) for the first public attempt that I know of), a number of startups will soon come out of stealth - and others are sure to follow. One reason to be excited about these systems is that they can potentially address a number of settings where existing machine learning techniques simply do not have the expressive power to achieve adequate results with the available data.

* **Application-specific services**. Examples include [PersuasionAPI](http://www.persuasionapi.com/) and [infer.com](https://www.infer.com/). Unlike the general ML libraries and web services discussed above, these offerings are highly specialized to address particular business problems, and may be targeted at specific verticals. The primary interface may still be an API - and therefore used by developers - but it solves a specific business problem (targeting marketing, lead prioritization, etc.)

## Business models

The pricing and packaging of analytics and BI offerings has traditionally been driven by the fact that a few highly-trained, specialist users have typically executed the work from which many benefit (i.e., a few authors and many consumers). In the past, providers like S+ and SAS addressed this imbalance by charging very highly for those few licenses that were needed. But this model is under massive pressure from open source offerings (R in particular, with Julia up and coming), as well as self-serve BI tools (not covered here), and is in the process of falling apart completely. 

As an alternative, many of these new offerings are trying a version of the AWS model: pricing by usage, as measured by API calls, amount of data analyzed, etc. This has the advantage to the vendor of at least tying the pricing to the cost to provide the service, but at significant strategic cost. First, this utility model leaves money on the table, because different kinds of data and different domains represent vastly different amounts of value to the user. Second, adopting this pricing model sends a strong signal that the vendor's job is not to deliver the business value, but instead to provide a basic infrastructural service (i.e., plumbing).

In short, everything that can be meaningfully metered is being used by someone as a pricing unit: consulting and support hours, API calls made, data amounts cranked, software licenses, and server cores. My sense is that the business models in this space need at least as much innovation and experimentation as the products and technology.

## The Machine Learning Value Chain

![image](img/MLValueChain.001.png)

Many startups that think of themselves as providing machine learning products and solutions are, naturally, focused quite heavily on the model-building and querying phases of the overall process. But it's important to note that these phases are just a fraction of the overall value chain that stretches from the collection of raw data to the ultimate solution of a business problem. 

Let's take a quick tour of this chain to see what is at risk of being ignored.

1. **Integration with existing data storage & analytics systems**. ML tools do not exist in a vacuum. Many big companies have already made huge investments in hadoop, data warehouses, and other analytic database offerings.

    Big, legacy vendors like SAS have been working on this for years and have a number of integration partners. My sense is that lack of a good story here is a major impediment to startup offerings looking to make enterprise sales.
    
    In fact, one thing I've noticed is that many startup offerings are oddly, even pathologically, disconnected from the larger data ecosystem, to the point where uploaded csv files are often the de facto data exchange solution. I get where this comes from - for a small team whose core expertise lies in algorithmic development as opposed to data infrastructure, this represents the path of least resistance. But this definitely puts significant constraints on how the resulting products can be priced and sold, and it also ignores the reality of [data gravity](http://blog.mccrory.me/2010/12/07/data-gravity-in-the-clouds/).

2. **Joining and rationalizing disparate datasets and sources** - often referred to as data integration, data fusion, or master data management. This is especially challenging (and valuable) when no deterministic shared key is available - i.e., no straightforward join is possible.

    This has traditionally been an area dominated by traditional, heavyweight enterprise solutions. Interestingly, at least two startups ([Paxata](http://paxata.com/) and [Trifacta](http://www.trifacta.com/)) are going after this phase - both using various ML methods themselves to attack problems usually addressed by manual or rules-based approaches.

3. **Data preprocessing, transformation, and feature engineering**. Data at rest is rarely ready for analysis by machine learning techniques, which often require some pretty specific and significant data-massaging steps to be performed. Sometimes this step is referred to as feature engineering - all of the work that is required to transform the data as it is found into an input dataset that is likely lead to a high-quality model. The specifics steps needed are highly dependent on the particular methods which will be employed.

   There is value waiting to be captured in (semi-)automated feature engineering; this is an interesting area to watch for innovation.

4. **Model-building and evaluation**. This is typically viewed as the core job of machine learning offerings, and as such it already receives considerable attention from the new crop of ML companies.

5. **Model deployment**. Once a model is built, it must be moved from the devlopment environment - often sitting on a data scientist's workstation - to production infrastructure. With many existing setups, the production technology stack is very different from that used to developer and evaluate models. The PMML standard was developed in part to address exactly this mismatch - to enable models to be declaratively specified and thereby ported from one environment to another.

6. **Discovery, Prediction, Prescription, Recommendation**. This is the phase at which real business value can be unlocked, whether by discovering an insight that informs decision-making; providing a predicted view of upcoming events; suggesting content, tasks, or people; or directly prompting action. 

    Key to maximizing this value is that the output or payload be delivered in the right context - not just delivered in the abstract, but tightly integrated into the user interface or business process involved. In contrast, many ML offerings in effect throw their scores/answers/recommendations over the wall, leaving it up to the customer to put those results in front of the right people at the right time. This is exactly where a vertical focus can be so impactful, because it is at this stage that the abstract similarities between problem domains give way to the messy particularities.

When businesses talk about wanting to pay for solutions to their problems (rather than products per se), what they mean is that they want to address many links in this chain at once. So, offerings that address the whole enchilada are multiplicatively, not just additively, more valuable than products which address just one or two pieces. The fact is, most potential customers simply aren't in a position to buy several partial solutions and string them together into a complete system - it's not how their purchasing process works, and they don't have the expertise anyway. 

And the potential customers that *do* have this kind of algorithmic expertise on hand can be problematic customers in other ways. For one thing, they probably have sophisticated data teams that want to use open source tools to build things in-house, rather than some new-fangled and unreliable service over which they have no control.

## Takeaways

Here are some working conclusions I've drawn after spending a few years in this space. 

1. [There's a bit of confusion](https://twitter.com/johnmyleswhite/status/409377138836398080) on the part of highly technical data scientists and algorithmic engineers about what is the value of the new crop of machine learning services. What do they really get from machine learning "in the cloud" that they can't obtain more easily and reliably from the many libraries and frameworks available? 

    For this reason, I think these services must look beyond these most sophisticated folks to find their user base: web developers, business users, SQL jockeys, something.

2. The kind of people who found ML startups are quick to identify (and fixate on) abstractions and generality - in short, all the ways in which different ML use cases are all the same. Through the right lens, predicting customer attrition, prioritizing sales leads, and predicting employee success can seem really similar - and these similarities will seem really intriguing (we don't have to choose! we can address all these use cases with one product!). This is dangerous, because it does not take into account the top of the value chain.

3. Any MLaaS company will need to reckon with Amazon's likely and imminent entry - just providing the basic capabilities, however convenient, elastic, and powerful, will no longer be enough.

4. Raw ML capability is not a thing that anyone wants to buy. Business folks - including the people with the budget to spend - want to buy solutions to business problems; machine learning is, at most, a tactic to employ along the way. And developers, whether data scientists/engineers or algorithmic folks, don't see why ML is something they should pay for - especially when there are so many seemingly high quality open libraries and frameworks out there.

Let me know what you think; you can find me on twitter [@beaucronin](https://twitter.com/beaucronin).
