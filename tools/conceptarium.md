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

## Building Blocks

As opposed to isolated tools, composable building blocks which have interoperability as a core principle enable a combinatorial explosion of workflows. Not only does the user have the freedom to mix and match them until obtaining the desired solution, but tool-makers can focus on designing new useful affordances to fit their workflows, rather than reinventing the knowledge graph. This is especially true when considering the coupling of data with client apps used to interact with it.

{: .quote }
"For example, I can program with Sublime Text, while my teammate uses vim, and we don’t need to fight to the death to pick one editor between us. There are dozens of text editors to choose from, and no lock-in from proprietary file formats. Contrast this with Google Docs: in order to live collaborate with each other, we all need to use the same editor. For someone who spends their whole working day in Google Docs, this can be a serious limitation. I personally hate doing substantial writing in Google Docs." -- Geoffrey Litt

{: .border }
![](/assets/images/buildingblocks.png)

## Semantic Spacetime

The conceptarium has at its core a semantic spacetime, a new representation of knowledge that differs from the popular knowledge graph in important ways. This new medium builds on the idea of semantic space, a term familiar to the machine learning community, but grossly underrated outside of it. Instead of being represented as nodes in a graph, knowledge fragments are represented as points in a space. Each document, each note, each picture, is uniquely projected onto semantic space automatically, using (rather opaque) statistical models. The core property of the semantic space is that documents which are close in meaning are located close to each other in semantic space. Conceptual differences correspond to geometric distances. It turns out that this alternative representation enables an entire new host of mechanics.

### Content-Based Addressing

As the process of embedding a document in semantic space already places it *somewhere*, there's no need to engage in the ceremony of placing it in a folder, tagging it, or even name it. The document is representing itself through its very contents in a self-sufficient way -- there's no immediate need for book-keeping. Documents are retrieved through semantic search, the process of looking for them in a certain region of the semantic space. This is usually done by embedding a new document, a *query*, and looking for documents which are close to it in semantic space (and therefore related in meaning). The same technique is at play when using an online search engine.

{: .border }
![](/assets/images/semanticspacetime.png)

## Mechanics

### Dynamic Links

In a knowledge graph, documents are connected through explicit links created by the knowledge worker. There are a finite number of them, they can't overlap, and they take time to create. In contrast, in a conceptarium, there are no explicit links at all, yet everything is interconnected. The standard way of moving from one document to another is by making an arbitrary selection (be it text or an image), which is then treated as a query for semantic search, leading the user to documents related to that particular selection. Therefore, there are virtually infinite rabbit holes to explore from each document. What's more, those dynamic links created on the fly might lead to different results over time, due to new more relevant documents being created in the meantime. The soft, implicit links adapt themselves to your growing knowledge base.   

{: .border }
![](/assets/images/dynamiclinks.png)

### Contextual Antimemory

### In-Place Recall

{: .border }
![](/assets/images/inplacerecall.png)

## Principles

### Everything is interconnected.

### Thoughts are not atomic.

### You are not your thoughts.

## Glimpses

## Conclusion