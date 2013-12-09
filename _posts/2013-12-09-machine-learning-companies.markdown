---
permalink: machine-learning-companies.html
title: Machine Learning Companies
layout: post

---

# Machine Learning Companies

I've helped build a couple companies around machine learning. It's a hard thing to do: this technology is especially difficult to productize, and therefore build a scalable business around. 

Here are some notes that describe how I think about this space now.

First, a few words on scope. I'll restrict this discussion to efforts that are addressed to "business data", broadly conceived: standard tabular and relational data, free text, transactions, logs, web behaviors, and social network posts. I'll exclude "perceptual" systems focused on vision, spoken language understanding, as well as robotics and drones. I'm also excluding companies that use ML to build their product, but for whom the business itself is in some other area - for example, I put both Prismatic and Premise Data in this category. Finally, I'll also leave aside the exciting internal ML efforts at companies like Google, Facebook, and Micrsoft.

I think the first thing to ask about a project or company is whether it intends to solve business or technical problems. Of course, in the right context, some technical problems really *are* business problems, but I still think this is a useful initial discriminator. Why? Because it really helps to get at who the potential customer might be. No business of any size wants to buy "machine learning", or has a machine learning budget. Businesses have business problems, and they want to spend money to solve those problems. This is why vendors have that tab called "solutions" at the top of their website.

# Kinds of machine learning offerings

The last five years has seen a lot of action in this area, and it's only accelerating. Here's how I break these offerings down.

* **Open source ML libraries**. Examples include scikit-learn, h2o, kiji, Mahout, Spark MLlib, graphlab. These are used by engineering-inclined data scientists and algorithmically-sophisticated developers to both perform one-off analyses and to build production data products (as one part of a larger data engineering stack). 

    These projects can either be truly non-profit enterprises (scikit), closely affiliated with - even say captive to - a single company with accompanying commercial interests (h2o and 0xdata), or seemingly somewhere in between (GraphLab). These nature of these company/project relationships is not always clear at first blush.

    Another way to differentiate these libraries is whether they are largely "stand-alone", like scikit-learn, or instead rest on top of a more complete big data analytics stack (Mahout, Cloudera ML, and h20 on hadoop; MLlib on Spark).

* **Technical and statistical computing environments**. Examples include R, SAS, SPSS, and the newcomer Julia. These are true computing environments that include a complete programming language, and which are extensible by writing code packages. Workbench interfaces are available for each of them, some of which eliminate completely elimindate the need to write code at all. They exist as both free/open source (R, Julia) and commercial (SAS, SPSS) offerings.

* **Machine Learning as a Service (MLaaS)**. Examples include BigML, wise.io, etcml, AlchemyAPI, PredictionIO, SwiftIQ, the Google Prediction API, and GraphLab's Notebook product. These offerings are distinguished by the fact that they live "in the cloud". They attempt to reduce complexity relative to ML libraries in two ways. First, they provide the same simplicity as other SaaS offerings: no need to deal with server scale out and capacity. But second, they - to varying degrees - sand the rough edges off the machine learning process provided by more traditional libraries.

   MLaaS offerings may or may not offer multiple ML techniques (logistic regression vs. SVMs), and they differ on whether the user even knows (or cares) which methods underlie their capabilities. Depending on where they fall on this spectrum, an offering may therefore reduce the level of expertise needed relative to libraries. The fundamental interface is a technical one.

* **Bayesian hierarchical modeling and probabilistic programming systems**: This is an emerging segment, immature relative to traditional machine learning, and sure to see lots of technical innovation in the coming 2-3 years. Current examples include PyMC, STAN, and Infer.net. 

   While there are no existing commercial offerings in this area, a number of startups will soon come out of stealth and others are likely to follow. One reason to be excited about these systems is that they can potentially address a number of settings where existing machine learning techniques simply do not have the expressive power to achieve adequate results with the available data.

* **Application-specific services**. Examples include PersuasionAPI and infer.com. Unlike ML libraries and web services, these offerings are highly specialized to address particular business problems, and may be targeted at specific verticals. The primary interface may still be an API - and therefore used by developers - but it solves a specific business problem (targeting marketing, lead prioritization, etc.)

# Business models

Pricing and packaging analytics and BI offerings has traditionally been driven by the fact that a few highly-trained specialists have typically done specialized work from which many benefit (i.e., a few authors and many consumers). In the past, providers like S+ and SAS addressed this imbalance by simply charging very highly for those few licenses that were needed. But this model is under massive pressure from open source offerings (R in particular, with Julia up and coming), and is falling apart. 

Many new services are trying a version of the AWS model - pricing by usage, as measured by API calls, amount of data analyzed, etc.. This has the advantage to the vendor of at least tying the pricing to the cost to provide, but 1) it holds the potential to leave money on the table, because different kinds of data can deliver vastly different amounts of value to the user, and 2) by adopting this utility pricing model, it sends a strong signal that the vendor's job is not to provide the ultimate value, but intead a basic infrastructural service.

In short, everything that can be meaningfully metered is being used by someone as a pricing unit: consulting and support hours, API calls made, data amounts cranked, software licenses, and server cores.

# The Machine Learning Value Chain

Many startups that think of themselves as providing machine learning products and solutions are, naturally, focused quite heavily on the model-building and querying phases of the overall process. But it's important to note that these phases are just a fraction of the overall value chain that stretches from the collection of raw data to the ultimate solution of a business problem. Let's take a quick tour of this chain to see what is at risk of being ignored.

1. **Integration with existing data storage & analytics systems**. ML tools do not exist in a vacuum. Many big companies have already made huge investments in hadoop, data warehouses, and other analytic database offerings.

    Big, legacy vendors like SAS have been working on this for years and have a number of integration partners. My sense is that lack of a good story here is a major impediment to startup offerings looking to make enterprise sales.

2. **Joining and rationalizing disparate datasets and sources** - often referred to as data integration, data fusion, or master data management. This is especially challenging (and valuable) when no deterministic shared key is available - i.e., no straightforward join is possible.

    This has traditionally been an area dominated by traditional, heavyweight enterprise solutions. Interestingly, at least two startups (Paxata and Trifacta) are going after this phase - both using various ML methods themselves to attack problems usually addressed by manual or rules-based approaches.

3. **Data preprocessing and transformation**. Data at rest is rarely ready for analysis by machine learning techniques, which often require some pretty specific and significant data-massaging steps to be performed. Sometimes this step is referred to as feature engineering - all of the work that is required to transform the data as it is found into an input dataset that is likely lead to a high-quality model. The specifics steps needed are highly dependent on the particular methods which will be employed.

   There is value waiting to be captured in (semi-)automated feature engineering; this is an interesting area to watch for innovation.

4. **Model-building and evaluation**. This is typically viewed as the core job of machine learning offerings, and as such it already receives considerable attention from the new crop of ML companies.

5. **Model deployment**. Once a model is built, it must be moved from the devlopment environment - often housed on a data scientist's workstation - to production infrastructure. With many existing setups, the production technology stack is very different from that used to developer and evaluate models. The PMML standard was developed in part to address exactly this mismatch - to enable models to be declaratively specified and thereby ported from one environment to another.

6. **Discovery, Prediction, Prescription, Recommendation**. This is the phase at which real business value can be unlocked, whether by discovering an insight that informs decision-making; providing a predicted view of upcoming events; suggesting content, tasks, or people; or directly prompting action. 

    Key to maximizing this value is that the output or payload be delivered in the right context - not delivered in the abstract, but tightly integrated into the interface or business process involved. In contrast, many ML offerings in effect throw their scores or answers or recommendations over the wall, leaving it up to the customer to get those results in front of the right people at the right time. This is exactly where a vertical focus can be so impactful.

When businesses talk about wanting to pay for solutions to their problems (rather than products per se), what they mean is that they want to address many links at once. So, offerings that address the whole enchilada are multiplicatively, not just additively, more valuable than products which address just one or two pieces. The fact is, most potential customers simply aren't in a position to buy several partial solutions and string them together into a comlete system - it's not how their purchasing works, and they don't have the expertise anyway. And the ones that *do* have this expertise on hand can be problematic customers in other ways; for one thing, they probably have sophisticated data teams that want to use open source tools to build things in-house.

# Takeaways

Here are some working conclusions I've drawn after spending a few years in this space. 

* There's a bit of confusion on the part of highly technical data scientists and algorithmic engineers about what is the value of these new, black-boxed services. I think this is because *if* such services are going to have a viable user base, it's going to have to be found beyond these sophisticated users; for the time being, they're going to continue to gravitate toward libraries and computing platforms that provide more (perceived) flexibility and configurability. So if you're going to black-box the methods, you'd better be going after a fundamentally different user base: web developers, business users, SQL jockeys, something.

* The kind of people who found ML startups are quick to identify (and fixate on) abstractions and generality. They'll see lots of similarities between different modeling domains (predicting customer attrition vs. prioritizing sales leads), and while they'll recognize that there are differences, the similarities will seem more intriguing. Intriguing enough to ignore the fact that everything else about 

* Any MLaaS company will need to reckon with Amazon's likely and imminent entry - just providing the basic capability, however conventient, elastic, and powerful, will no longer be enough.

* Raw ML capability is not a thing that anyone wants to buy. Business folks - including the people with the budget to spend - want to buy solutions to business problems; machine learning is, at most, a tactic to employ along the way. And developers, whether data scientists/engineers or algorithmic folks, don't see why ML is something they should pay for - especially when there are so many seemingly high quality open libraries and frameworks out there.
