---
layout: default
title: Conceptarium
nav_order: 1
parent: Tools
description: "A fluid medium for storing, relating, and surfacing thoughts."
published: False
---

# Conceptarium
{: .d-inline-block .mt-4 .no_toc }

STAGE 1
{: .label }

A fluid medium for storing, relating, and surfacing thoughts.
{: .fs-6 .fw-300 .text-left .mb-0 .mt-0 }

By [@thoughtware.engineer](https://paulbricman.com/)
{: .mt-1 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

A conceptarium (noun. /ˈknsɛptɛriəm/, plural: conceptaria) is a fluid medium for storing, relating, and surfacing thoughts based on a new representation of knowledge. It's meant to provide a foundation for other tools for thought to build onto, a means to nurture a new tooling ecosystem for knowledge work. It embodies a philosophy of knowledge which differs in important ways from the one embodied by the knowledge graph poster children (e.g. Roam Research, Obsidian, Logseq). This document is simply a blueprint of this building block, part vignette and part wireframe, meant to give the idea a home.

## Representation

In one's conceptarium, individual thoughts, ideas, and concepts are discrete documents. A document can either be a short text or an image. There are no file names, no note titles, and no tags -- there's no book-keeping ceremony. Each document is first and foremost represented through its contents in a self-sufficient way. The meaning of the document, its very semantics, are enough to define the document as a whole, without relying on supplemental annotations. Besides the characters of a text or the pixels of an image, each document is automatically attached three bits of metadata, which help organize the conceptarium and offer the user new affordances: a semantic embedding, the creation timestamp, and the activation.

### Semantic Embedding

The semantic embedding of a document is a set of spatial coordinates, a finite list of numbers which indicate its location in space. Notably, this is not a physical space, and the document coordinates are not related to latitude and longitude. Rather, documents live in a *semantic space*, a space of possible meanings, with way more than three dimensions. Clever statistical models take on the task of *projecting* individual documents onto semantic space automatically, providing actual coordinates. The semantic embedding of a document is strictly a function of its contents, with nothing else influencing its location. As dimensions of meaning are expressed as dimensions of space, documents which mean similar things are to be found close to each other in semantic space.

Semantic embeddings are a bit like cryptographic hashes. Each document gets hashed into a unique string of bytes. Hashing it again results in an identical outcome. Hashing two different documents results in two different hashes. However, replace one word with its synonym in a text file and you get a completely different cryptographic hash. In contrast, if you compute the semantic embedding of this text file, it will be extremely similar to the original version, as the meaning hasn't change much in the editing process. Similarly, if you have two documents which mean similar things, they will have similar semantic embeddings. Naturally, those two tools are used for widely different purposes.

{: .border }
![](/assets/images/semanticspacetime.png)

### Timestamp

This bit of metadata is rather trivial compared to the previous one, but still important. By merely storing the creation timestamp for each document, a whole new dimension is added to the documents which can later be made use of, especially in tandem with the other ones. For instance, cutting a slice of time through a region of the semantic space might reveal the way your thinking evolved around a certain set of ideas. Alternatively, you might be able to locate the pioneering seedlings which grew into whole clusters of thought in their respective regions of the semantic space.

### Activation

If the concept of semantic embedding is mostly familiar to the machine learning crowd, the concept of activation as used here is mostly familiar to the cognitive psychology crowd. In many cognitive architectures of human memory, *activation* is a pervasive way of thinking about how memories are retrieved. In the iconic ACT-R, each memory (or chunk) has an activation, a numeric value which indicates, well, how "active" that memory is in one's mind. Memories with higher activations are more likely to be remembered. The activation of a memory is a function of several factors, mainly including: recency, frequency, and contextual relevance. Similar models of memory also form the backbone of spaced repetition algorithms in Anki and SuperMemo, where the goal is to essentially maintain memories above an activation threshold.

In one's conceptarium, each document has an activation which changes over time. Documents which have been created recently or have been retrieved frequently (as measured by the user's sustained interest in probing their region of the semantic space) have a higher activation. Just like the creation timestamp, a document's activation is mostly useful when used in tandem with other bits of metadata. For instance, I might want to retrieve documents related to a context which I'm *specifically unlikely to remember myself*, a complementary "antimemory" which avoids the redundancy of surfacing thoughts which I already remember myself. Alternatively, I might use the most active documents as a proxy for my current interests in downstream tools for networking.

Together, the semantic embedding, the creation timestamp, and the activation help paint a rich picture of the document's meanings and its relation to our thought process, lending itself to a whole new set of subsequent mechanics. To help conceptualize this composite representation of documents, I eventually developed the following image. Imagine each document as a dot in a three-dimensional space. Over time, more dots are popping up, as documents can only be added to the conceptarium, never deleted. Additionally, each dot has a color, signaling its activation. Newly created dots are bright red, due to their high activation, and they slowly turn blue as they cool down. As a final touch, when probing the conceptarium with a query in an attempt to retrieve past documents, a wave is propagating outwards from the query location to nearby dots, increasing their activation due to sustained interest.

## Principles

The conceptarium embodies some specific principles about how knowledge is like and how we should work with it. Below is an attempt to articulate those explicitly, to lay bare the creator's philosophy in an effort to be transparent.

### Everything is interconnected.

In a knowledge graph, each node is connected to a subset of the other notes through explicit links created by the knowledge worker. They are finite, can't overlap, and require valuable time to create. In contrast, in a conceptarium, all documented are related to each other. They live in the same space, and are just closer or farther away from each other. Additionally, the orientation of the straight line which connects two dots is deeply informative and codes the semantic relation between the two documents. This principle is explored in much more depth in [Semantica](/tools/semantica/#match). However, even if we haven't developed a way to visualize, let alone understand, the semantics of high-dimensional spatial layouts, they are still present in the representation as a testament for every thought having *some* unique relation to every other one.

### Thoughts are not atomic.

In a knowledge graph, each note should be atomic, meaning that it should express one thing and one thing only. Those "atoms" are then linked together to form the knowledge graph. The conceptarium, even though its documents are discrete, invites the user to narrow in on arbitrary fragments of a document, to select part of a text or part of an image as the next stop of their train of thought. After the selection is made, the conceptarium can then resurface documents related to that specific aspect of the initial one, somewhat like the *Select > Right click > Search DuckDuckGo for "..."* option in browsers, but as the core linking mechanic. In this, each document can be broken down into a virtually infinite collection of fragments, which via the previous principle, can each lead down their rabbit holes.

{: .border }
![](/assets/images/dynamiclinks.png)

### You are not your thoughts.

The term conceptarium is not just an expansive sound bite. Similar to how a herbarium is used to collect plant samples or how a terrarium is used to collect fragments of living habitat, the conceptarium is used to collect thoughts. It is nothing more than a high-tech Mason jar for those elusive pieces of language and imagery entertained by our minds moment by moment. In this, it helps the user detach themselves from their thoughts, acknowledging that individual insights are more a result of happenstance and memetic dynamics than a reflection of personal worth. Not even the most dedicated knowledge worker can control the momentary weather of their minds, but only the general climate, and the explicit decoupling of the conceptarium helps internalize this belief.

## Implementation

### Architecture

### Building Blocks

As opposed to isolated tools, composable building blocks which have interoperability as a core principle enable a combinatorial explosion of workflows. Not only does the user have the freedom to mix and match them until obtaining the desired solution, but tool-makers can focus on designing new useful affordances to fit their workflows, rather than reinventing the knowledge graph. This is especially true when considering the coupling of data with client apps used to interact with it.

{: .quote }
"For example, I can program with Sublime Text, while my teammate uses vim, and we don’t need to fight to the death to pick one editor between us. There are dozens of text editors to choose from, and no lock-in from proprietary file formats. Contrast this with Google Docs: in order to live collaborate with each other, we all need to use the same editor. For someone who spends their whole working day in Google Docs, this can be a serious limitation. I personally hate doing substantial writing in Google Docs." -- Geoffrey Litt

The conceptarium provides a self-contain knowledge store for other tools for thought to build onto. Additionally, it manages the nuts and bolts of the unique underlying representation, so that third-party apps don't have to worry about its implementation.

{: .border }
![](/assets/images/buildingblocks.png)

## Glimpses

### In-Place Recall

{: .border }
![](/assets/images/inplacerecall.png)

### Mnemonic Microcosm

### Ideological Kinetics

### Belief System IDE

## Conclusion