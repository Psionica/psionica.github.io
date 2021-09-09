---
layout: default
title: Ideoscope
nav_order: 0
parent: Tools
description: "An instrument for quantifying, understanding, and optimizing your thinking."
published: False
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

An ideoscope (noun. /aɪdɪɒskoʊp/, plural: ideoscopes) is an instrument for measuring your thought process through a host of novel metrics. It builds on top of the [conceptarium](/tools/conceptarium) and provides a window into your thinking in the form of an analytics dashboard full of stats and visualizations. Quantifying your thought process paves the way for a radically more intimate understanding of your thought patterns as a knowledge worker. The process of measurement, in turn, enables a host of strategies for nurturing your mind, such as A/B testing your routine for maximum generation of novel ideas (i.e. ideogenesis) or setting monthly goals for the breadth of your perspective (i.e. memetic variability).

The ideoscope is realized in a specific cultural landscape with strong influences from a number of movements. Firstly, the quantified self (QS) community advocates for the intentional measurement of various facets of yourself (e.g. sleep, productivity, well-being) as a necessary precursor for the objective optimization of the same facets. Specifically, the quantified mind project has been around since almost a decade ago, yet it focuses more on evaluating general cognitive performance through brain puzzles and abstract minigames. In contrast, the ideoscope addresses a higher level of abstraction by focusing on the totality of your specific thoughts which inhabit your mind. This nuance comes from the highly controversial field of memetics, which frames the mind as a habitat where ideas live, reproduce, and suffer mutations -- an ecology of thought.

## Architecture

As mentioned above, the ideoscope is designed as a building block which easily integrates with the conceptarium. It makes direct use of the novel representation introduced in the conceptarium, although most of the analytics involved can in theory be used with third-party data sources. The reason for this reliance on an exotic format is the richness through which it provides a mirror of the mind's ecology, unparalleled by other available alternatives (e.g. plain Markdown notes), even if still extremely far away from how the mind works.

Concretely, the ideoscope is a web app created in Python using Streamlit. It requires the URL of your conceptarium in order to extract its contents in JSON format in the background. After fetching your thoughts (as JSON), the ideoscope derives a sequence of stats and visualization designed to give you insights into your own thought process. Those metrics are grouped into three broad categories: memetics, semantics, and linguistics. Each of these provides a different angle for understanding your thinking, similar to how a blood panel involves different families of tests (e.g. hematology, biochemistry).

{: .warn }
Understanding the potential of the novel metrics introduced below requires a decent intuition around the three-part representation used by the conceptarium.

## Metrics

### Memetics

#### Ideogenesis

This metric simply refers to the rate of saving new thoughts in the conceptarium. It can support a number of different related stats and visualization (e.g. calendar views, histograms): past month, past week, past day, per month, per week, per day, by day of the week, by hour. If you're using the conceptarium as a storage medium for new ideas, then ideogenesis can indicate when (i.e. in what recent period, in what part of the day) you generated most new ideas. Correlating this with the activities you've engaged in during those times via your calendar or time tracker might help identify the most *thoughtful* ones. Chatting with interesting people and enjoying solo walks in nature appear to be major such candidates for me. 

#### Memetic Variability

Each thought saved in the conceptarium has a semantic embedding which indicates what it is about by placing it at certain coordinates in a semantic space. Memetic variability, in an analogy to genetic variability, is a measure of how *diverse* your thoughts are, how much variation there is in the ecology of your thoughts during a certain period of time. It's computed through the standard deviation (i.e. spread) of the semantic embeddings your thoughts in semantic space. If you've been constantly thinking about the same things in the same way through the past month, the memetic variability would be quite low. In contrast, if you've been thinking about more diverse things, the memetic variability would be higher. In population genetics, variability is argued to be a hard requirement for natural selection, which helps raise fitter individuals over time. Similarly, a healthy dose of memetic variability might be helpful in generating powerful ideas. In contrast, a memetic monoculture might get stuck in a local optimum of fitness.

#### Memetic Drift

Memetic drift, in an analogy to genetic drift, is a measure how fast the aggregate state of your memetic ecology (i.e. ideology) is changing over time. It's computed through the distance between the centroid (i.e. the center point located at the average coordinates) of the semantic embeddings of your thoughts from a recent period of time (e.g. past month) and the centroid of the semantic embeddings of your thoughts from a previous period (e.g. the previous month). If you've been completely changing your general focus from one month to the next, your memetic drift would be high. Conversely, if you've been rather constant in your general focus through the whole past year, your memetic drift would be quite low. The reason why this analogy is weaker is that in population genetics, genetic drift is solely the result of random chance favoring some individuals over the others. In contrast, memetic drift aims to put a numerical grip on the aggregate influences which lead to changes in the population over time, which also include versions of natural selection, mutation (i.e. random changes), and flow (i.e. migration across ecologies). That said, the term "drift" successfully captures the idea of slow aggregate changes over time, while still maintaining a loose link to genetics.

{: .info }
Interestingly enough, population genetics notes that the effect of genetic drift on large populations is way smaller than on smaller populations. Through a memetic lens, this might partially explain why large ecologies of thought which had a long time to mature are more resistant to change (e.g. elderly, whole cultures), even if obvious other factors are at play (e.g. neuroplasticity, social norms). 

#### Memetic Load

#### Population Size

### Semantics

#### Explored Volume

#### Discovery Rate

#### Low-Dimensional Projection

### Linguistics

#### Length

#### Readability

#### Factuality

#### Sentiment

#### Keywords

## Strategies