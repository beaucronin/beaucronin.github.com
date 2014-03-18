Events happen in the world, and they have causes. In some cases, those events are captured or measured, and therefore recorded by machines. A timestamped collection of these events comprises a log. Some log entries are deeply rooted in time - an event occurred in the world, and it was recorded - while in other cases the timestamp is more incidental, such as noting the time at which a database record was updated. 

Typically, though, the data that we feed into machine learning systems - classification, clustering, and so on - is highly processed or aggregated from the form in which it was originally captured. It is cleaned, filtered aggregated, and otherwise transformed. This is because our ML methods have very particular expectations about the overall form and the detailed content of their inputs. In most cases, they want tables, matrices, or graphs of clean, homogeneous data.

The workflow that takes us from original data to its learning-ready form is largely taken for granted at this point, but let's examine these assumptions.

In particular, every pre-processing step throws away information. We do it anyway because: 1) we think most of what it thrown away is useless, and 2) in many cases, our tools don't leave us much choice.

But what if we had learning methods that could be directed at raw event streams? I.e., methods that sought to explain the data-as-it-is-collected?

What I have in mind is a generative, stochastic process model of events, one whose higher-level structure describes the causal structure of the processes in the world that lead to events, and whose lower-level structure describes how the events themselves are emitted and authored.

If such a model existed, we could do a lot of cool things:

* Understand which events are unusual or surprising in various ways, either in isolation or as a group
* Predict which events are most likely to occur in a future time window
* Retroactively identify groups or categories of events that "go together" or co-occur, above and beyond their syntactic similarities

Two immediate questions: how would this event model be authored? and how would inference be performed to learn its specific latent variable structure from a particular observed event stream?

For authoring, I'm imagining a suitable probabailistic programming language, one well-suited to this inherently dynamic case. At a minimum, it should capture the fact that a given log can contain events from multiple sources, which may have dependencies of various kinds between them.

For inference: beats me. The data will be high-volume, so there will be challenges there. But we may be able to identify some nice simplifying assumptions once we have some good example in mind.
