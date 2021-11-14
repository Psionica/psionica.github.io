---
layout: default
title: Ideoscope
nav_order: 0
parent: Tools
description: "An instrument for quantifying, understanding, and optimizing your thinking."
published: True
redirect_to: https://paulbricman.com/thoughtware/ideoscope
---

# Ideoscope
{: .d-inline-block .mt-4 .no_toc }

STAGE 1
{: .label }

An instrument for quantifying, understanding, and optimizing your thinking.
{: .fs-6 .fw-300 .text-left .mb-0 .mt-0 }

By [@thoughtware.engineer](https://paulbricman.com/)
{: .mt-1 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

An ideoscope (noun. /aɪdɪɒskoʊp/, plural: ideoscopes) is an instrument for measuring your thought process through a host of novel metrics. It builds on top of the [conceptarium](/tools/conceptarium) and provides a window into your thinking in the form of an analytics dashboard full of stats and visualizations. Quantifying your thought process paves the way for a more intimate understanding of your thought patterns as a knowledge worker. The process of measurement, in turn, enables a host of strategies for nurturing your mind, such as A/B testing your routine for maximum generation of novel ideas (i.e. ideogenesis) or setting monthly goals for the breadth of your perspective (i.e. memetic variability).

The ideoscope is realized in a specific cultural landscape, with influences from a number of movements. Firstly, the quantified self community advocates for the intentional measurement of various facets of your life (e.g. sleep, productivity, well-being) as a necessary precursor for the effective optimization of those areas.[^2] Particularly relevant here is the quantified mind project, which has been around since almost a decade ago, yet it focuses more on evaluating general cognitive performance through brain puzzles and abstract minigames.[^3] In contrast, the ideoscope addresses a higher level of abstraction by focusing on the set of specific thoughts which inhabit your mind. This perspective comes from the highly controversial field of memetics, which frames the mind as a habitat where ideas live, reproduce, and mutate -- an ecology of thought.

## Architecture

As already mentioned, the ideoscope is designed as a building block which easily integrates with the [conceptarium](/tools/conceptarium). It makes direct use of the novel representation introduced by the other tool, although most of the analytics involved can in theory be used with third-party data sources. The reliance on an exotic format is justified by the richness through which it provides a mirror of the mind's ecology, unparalleled by other available alternatives (e.g. plain Markdown notes), even if still extremely far from how the mind works.

Concretely, the ideoscope is a web app written in Python using Streamlit.[^6] For starters, it needs the URL of your [conceptarium](/tools/conceptarium) in order to extract its contents in the background. After fetching your thoughts as JSON, the ideoscope derives a sequence of stats and visualization designed to give you insights into your own thought process.

{: .warn }
Understanding the potential of the novel metrics introduced below requires a decent understanding of the [three-part representation](http://localhost:4000/tools/conceptarium/#representation) used by the conceptarium.

## Metrics

The metrics incorporated in the ideoscope are grouped into three broad categories: memetics, semantics, and linguistics. Each of these provides a different angle for analyzing your thinking, similar to how a blood panel involves different families of tests (e.g. hematology, biochemistry).

### Memetics

As hinted at before, the memetic perspective consists in looking at your mind as a population of memes (i.e. ideas, thoughts, concepts) which evolves over time, facing various obstacles and opportunities along the way.[^7]

#### Ideogenesis

This metric simply refers to the rate of new thoughts being saved in the [conceptarium](/tools/conceptarium). It supports a number of different related stats and visualizations (e.g. calendar views, histograms): past month, past week, past day, per month, per week, per day, by day of the week, by hour. If you're using the [conceptarium](/tools/conceptarium) as a storage medium for new ideas, then ideogenesis can indicate when (i.e. in what recent period, in what part of the day) you generate most new ideas. Correlating this with activities you've engaged in during those times (e.g. via your calendar or time tracker) might help identify the most *thoughtful* practices. Chatting with interesting people and enjoying solo walks in nature appear to be major such candidates for me.

#### Memetic Variability

Each thought saved in the [conceptarium](/tools/conceptarium) has a semantic embedding which indicates what it is about by placing it at certain coordinates in semantic space. Memetic variability, in an analogy to genetic variability, is then a measure of how *diverse* your thoughts are, how much variation there is in the ecology of your thought during a certain period of time.[^1] It's computed through the standard deviation (i.e. spread) of your thoughts across semantic space. If you've been constantly thinking about the same things in the same way through the past month, the memetic variability would be quite low. In contrast, if you've been thinking about more diverse things, the memetic variability would be higher. In population genetics, variability is argued to be a hard requirement for natural selection, which helps increase fitness over time. Similarly, a healthy dose of memetic variability might be helpful in generating powerful ideas, while a memetic monoculture might get stuck in a local optimum of fitness. Think of memetic variability as biodiversity for ideas.

#### Memetic Drift

Memetic drift, in an analogy to genetic drift, is a measure of how fast the aggregate state of your memetic ecology (i.e. ideology) is changing over time. It's computed through the distance between the centroid (i.e. the center point located at the average coordinates) of the semantic embeddings of your thoughts from a recent period of time (e.g. past month) and the centroid of the semantic embeddings of your thoughts from a previous period (e.g. the previous month). If you've been completely changing your general focus from one month to the next, your memetic drift would be high. Conversely, if you've been rather constant in your general focus through the whole past year, your memetic drift would be quite low.

{: .info }
Interestingly enough, population genetics notes that the effect of genetic drift on large populations is way smaller than on small populations.[^1] Through a memetic lens, this might partially explain why large ecologies of thought which had a long time to mature are more resistant to change (e.g. elderly, whole cultures), even if obvious other factors are at play (e.g. neuroplasticity, social norms).

#### Memetic Fitness

If the previous metrics aimed to characterize the entire population of your memetic ecology, memetic fitness is a characteristic of an individual -- one idea. We're identifying the fitness of an idea here with its activation in the [conceptarium](/tools/conceptarium). The more captivating, consequential, and generally interesting ideas are the most active ones, the ones you've kept thinking about most. Besides getting some summary stats like min, max, mean, median, or mode, it's possible to peek into the aggregate fitness landscape of the population through visualizations like histograms and boxplots. These metrics might be able to diagnose segregation, inbreeding, elitism, and other pitfalls faced by evolving populations. 

#### Memetic Load

Memetic load, in an analogy to genetic load, is a measure of the presence of unfavorable memetic material in your ecology of mind.[^1] It's expressed as a function of the maximum fitness found in the population and the average fitness of the population as a whole. Concretely, if you've invested time in thinking about things you're not thinking about now at all, then the memetic load would be high. Alternatively, if all saved thoughts are relatively active, then the memetic load is quite low.

{: .border }
![](/assets/images/ideoscope1.png)

#### Effective Population Size

Just like in population genetics, the population size of your memetic ecology is simply the number of individuals (i.e. ideas) which inhabit it. However, some further criteria might turn it into a more useful metric than simply an indicator of how many thoughts you ever saved to the [conceptarium](/tools/conceptarium). For instance, thoughts might be considered active members of the ecology only if their activation is above a certain threshold.

#### Memetic Carrying Capacity

Memetic carrying capacity, in an analogy to the notion of carrying capacity used in environmental science, is the maximum population size which can be sustained by your mind as a habitat for ideas.[^4] Cognitive resources have long been argued to be limited across various dimensions, the combination of which might only be able to support a certain quantity of thought. This might be helpful for budgeting your available cognitive resources according to predefined objectives. The memetic carrying capacity can be gauged by looking back in time and estimating the maximum population size based on the largest populations recorded in the past.

### Semantics

In contrast to the memetic lens which frames all of thought as evolution, the semantics perspective employed here disregards any Darwinian nuance and narrows in on the semantic embeddings alone.

{: .warn }
The semantic space accessible by embedding thoughts using a machine learning model is "shaped" so as to only account for the human thought seen in the training data, and little else. The resources of expressivity are completely devoted to representing human ideas contained in text, due to the optimization pressures involved in training. Therefore, when talking about the volume of semantic space, it's useful to keep in mind that we're only referring to the breadth of human thought, rather than the breadth of all possible thought (e.g. artificial, animal, posthuman etc.). Still, this measure might be informative, and currently, all we have at our disposal.

#### Explored Volume

The semantic embeddings of thoughts are expressed as points in semantic space. Therefore, the finite set of one's thoughts occupies exactly zero percent of the entire volume of the semantic space. However, if one promoted those zero-dimensional points to tiny three-dimensional spheres indicating rough semantic neighborhoods, then it becomes possible to talk about the total volume of the semantic space which has been "touched" by your thoughts, the size of the semantic territory which you've explored via your ideas. Conversely, this enables a measure of your ideological terra incognita, how much thought there is which you haven't personally experienced. All this seems highly esoteric, but the ideoscope shows you a concrete number, an actual percentage indicating how far you've thought, and how much there's left.

#### Discovery Rate

This change in perspective from points to tiny spheres popping up all around semantic space enables yet another new metric. The discovery rate is a measure of how much new semantic territory you've discovered in a set period of time (e.g. last month), the rate of change of the explored volume. This might make for an interesting target indicator based on values of exploration and conquest.

#### Low-Dimensional Projection

All previous metrics, even if quite informative, are simply stats or, at best, time series. Low-dimensional projection is a completely different way of thinking about thoughts in high-dimensional semantic spaces by reducing their dimensionality and actually *seeing* them (e.g. on a 2D plane). Even if this visualization technique doesn't focus on deriving specific insights from your thought process, looking at ideas popping up across jagged semantic trajectories (i.e. trains of thought), might ultimately prove informative as well. Note that projecting high-dimensional points on a 2D plane inevitably means cutting down on the expressivity of the original spatial layouts.

### Linguistics

If all previous metrics applied to thoughts expressed both through written language and visual imagery as stored in the [conceptarium](/tools/conceptarium), the following explore opportunities for gaining insights from langauge in particular.

#### Conciseness

Probably the most trivial metric of those provided by the ideoscope, conciseness is simply an indicator of how long your written thoughts are, based on a word count. Capturing the essence of ideas effectively can easily be a target to aim for.

#### Readability

Just a bit less trivial than the previous metric, readability is a measure of how clear and easy to understand your language is. See it as a proxy for success in using ELI5 or the Feynman technique. Common readability scores often express their results in terms of the rough level of education required to read a text, based on factors like the length of the individual words you're using.

{: .border }
![](/assets/images/ideoscope2.png)

#### Objectivity

By using rather traditional text mining techniques, objectivity can be roughly gauged based on the nature of words used.[^5] Words typically associated with expressing personal takes drive objectivity down, while dry impersonal phrases nudge it upwards. A rationalist might aim for achieving high objectivity, while someone interested in getting in touch with their subjective intuition might aim for achieving low objectivity. Additionally, thoughts can be tested against a set of predefined fallacies via language models, and the results reported. 

#### Sentiment

Using very similar techniques to the previous metric, the sentiment of your written thoughts can tracked on a simplistic one-dimensional scale from 0 (i.e. negative sentiment) to 1 (i.e. positive sentiment). Think of it as an estimate of how many stars an online review has based on its text contents, but normalized between 0 and 1. In explorations of the [conceptarium](/tools/conceptarium) as a therapeutic tool, a safe space for honest thoughts, the average sentiment over various periods of time might provide useful insights and even a tangible target for well-being interventions.

#### Interests

Being the only window into your [conceptarium](/tools/conceptarium) which shows you the actual contents of your thoughts, this is a visualization of how your interests evolved based on the frequency of certain keywords over time. Thoughts are bucketed by certain time intervals (e.g. by week) on a timeline, and the most frequent noun phrases you used in each period are reported. This can be an effective way of getting a sense of how your interests (i.e. the things you've been thinking about) changed through the years.

## Strategies

Taking in the range of stats and visualizations which are part of the ideoscope's dashboard can be an exciting activity in itself, but the real value of this computer-aided introspection practice lies in how it informs your thinking habits. Below are a few general strategies or practices which you might use to make the most out of the deeper understanding of your thought process. 

### Ideological Audit

You might decide on occasionally performing an audit of your thinking. This could consist in a weekly time slot dedicated to glancing over your ideological metrics and course-correcting your routine in order to reach your target goals. This might mean anything from expressing ideas with more clarity (i.e. readability, conciseness, objectivity) to being on track with your discovery rate of thought based on your average lifespan. The practice of regularly running diagnostics on your thinking might prove a powerful new way of avoiding failure modes on a cognitive level.

### Ideogenesis A/B Testing

Do you come up with more new ideas at home or in nature? When reflecting on your own or when chatting with peers? How does ideogenesis interact with your sleep and diet? Tracking rates of generating new ideas can lead the way to maximizing them via intentional tweaks to your routine.

### Temperature Schedule

In optimization theory, search algorithms like simulated annealing and genetic algorithms aim to explore more in the beginning and then less and less of the search space as time goes on. Similarly, you might aim to act as a generalist in your youth and gently switch to a specialist as you grow up. Metrics like memetic variability and drift can help you keep your ideological journey on track through best practices derived from theory and empirical data.

## Conclusion

The ideoscope is a digital instrument which enables a new dimension of understanding your thought process. Through novel metrics which take advantage of the [conceptarium's](/tools/conceptarium) architecture, knowledge workers can get a numerical grip on the ecology of their mind, and start cultivating it rationally. 

---

## Acknowledgements

Our work is supported by awesome people: [Adam Wiggins](https://opencollective.com/adam-wiggins), [Alex Iwaniuk](https://opencollective.com/alex-hubert-iwaniuk), [Andreas Stuhlmüller](https://stuhlmueller.org/), [Bruno Winck](https://opencollective.com/bruno-winck), [Chris Boette](https://opencollective.com/chris-boette), [David Dohan](https://opencollective.com/david-d), [Flancia](https://opencollective.com/flancia), [I Do Recall, Inc.](https://opencollective.com/i-do-recall-inc), [Nick Milo](https://opencollective.com/nickmilo), [Maggie Appleton](https://opencollective.com/maggie-appleton), [Serj Hunt](https://opencollective.com/serjhunt_ark), [Yang Wao](https://opencollective.com/yangwao).

## Support Us

Our only stakeholder is humanity. Help us keep it that way.

By supporting our efforts, you're investing in transparent research and development at the frontier of thought. Not only are you helping us deliver open source tools reshaping the landscape of knowledge work, but you're also setting in motion a broader movement around cognitive augmentation as a second-order consequence.

[Become a supporter](https://opencollective.com/psionica){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 }

---

## Join Us

Do you want to contribute to the development of this project yourself? Join Psionica if you want to be part of an enthusiastic community of designers, researchers, and developers committed to empowering individuals around the world in fundamentally new ways. Contribute to existing projects, develop your own, or just hang around for an insightful chat.

[Become a member](https://discord.gg/NXYZUbhMNf){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 }

---

## References

[^1]: John Gillespie,<br/>[Population Genetics: A Concise Guide](https://b-ok.xyz/book/461097/8c9c1c)
[^2]: Reddit,<br/>[Quantified Self](https://www.reddit.com/r/QuantifiedSelf/top/?t=all)
[^3]: Quantified Mind,<br/>[What We Test](http://www.quantified-mind.com/)
[^4]: National Geographic,<br/>[Carrying Capacity](https://www.nationalgeographic.org/topics/resource-library-carrying-capacity/)
[^5]: TextBlob,<br/>[Quickstart](https://textblob.readthedocs.io/en/dev/quickstart.html#sentiment-analysis)
[^6]: Streamlit,<br/>[Home Page](https://streamlit.io/)
[^7]: Paul Bricman,<br/>[Ideoponics](paulbricman.com/reflections/ideoponics)