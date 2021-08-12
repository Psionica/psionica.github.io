---
layout: default
title: Conceptarium
nav_order: 1
parent: Tools
description: "A fluid medium for storing, relating, and surfacing thoughts."
published: True
---

# Conceptarium
{: .d-inline-block .mt-4 .no_toc }

STAGE 1
{: .label }

A fluid medium for storing, relating, and surfacing thoughts.
{: .fs-6 .fw-300 .text-left .mb-0 .mt-0 }

August 2021, by [@thoughtware.engineer](https://paulbricman.com/)
{: .mt-1 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

A conceptarium (noun. /ˈknsɛptɛriəm/, plural: conceptaria) is a fluid medium for storing, relating, and surfacing thoughts based on a new representation of knowledge. It's meant to provide a foundation for new tools for thought to build onto, a means to nurture a new tooling ecosystem for knowledge work -- a cognitive infrastructure. It embodies a philosophy of knowledge which differs in important ways from the one embodied by the knowledge graph poster children (e.g. Roam Research, Obsidian, Logseq). This document is simply a blueprint of this building block, part vignette and part wireframe, meant to give the idea a home.

## Representation

In one's conceptarium, individual thoughts, ideas, and concepts are discrete documents. A document can either be a short text or an image. There are no file names, no note titles, and no tags -- there's no book-keeping ceremony. Each document is first and foremost represented through its contents in a self-sufficient way. The meaning of a document, its very semantics, are enough to define it as a whole, without relying on additional annotations. Besides the characters in a text or the pixels in an image, each document is automatically attached three bits of metadata, which together help organize the conceptarium and support a host of new affordances: a semantic embedding, the creation timestamp, and the activation.

### Semantic Embedding

The semantic embedding of a document is a set of spatial coordinates, a finite list of numbers which indicate its location in space. Notably, this is not a physical space, and the document coordinates are not related to latitude and longitude. Rather, documents live in a *semantic space*, a space of possible meanings, with way more than three dimensions. Clever statistical models take on the task of *projecting* individual documents onto semantic space automatically, providing the actual coordinates. The semantic embedding of a document is strictly a function of its contents, with nothing else influencing its location. As dimensions of meaning are expressed as dimensions of space, documents which mean similar things are to be found close to each other in semantic space. [^2]

Semantic embeddings are a bit like cryptographic hashes. Each document gets hashed into a unique string of bytes. Hashing it again results in an identical outcome. Hashing two different documents results in two different hashes. However, replace one word with its synonym in a text file and you get a completely different cryptographic hash. In contrast, if you also compute the semantic embedding of this piece of text, it will be extremely similar to the original version, as the meaning hasn't changed much in the editing process. Similarly, if you have two documents which mean similar things, they will have similar semantic embeddings, even if they use different words. Naturally, those two concepts are used in widely different settings.

{: .border }
![](/assets/images/semanticspacetime.png)

### Timestamp

This bit of metadata is rather trivial compared to the previous one, but still important. By merely storing the creation timestamp for each document, a whole new dimension is added to the documents which can later be made use of, especially in tandem with the other ones. For instance, cutting a slice of time through a region of the semantic space might reveal the way your thinking evolved around a certain set of ideas over time. Alternatively, you might be able to locate the pioneering seedlings which grew into whole clusters of thought in their respective regions of the semantic space, the ideas which shaped your thinking most.

### Activation

If the concept of semantic embedding is mostly familiar to the machine learning crowd, the concept of activation as used here is mostly familiar to the cognitive psychology crowd. In many cognitive architectures of human memory, *activation* is a pervasive way of thinking about how memories are retrieved. In the iconic ACT-R, each memory (or chunk) has an activation, a numerical value which indicates, well, how "active" that memory is in one's mind. Memories with higher activations are more likely to be remembered. The activation of a memory is a function of several factors, mainly including: recency, frequency, and contextual relevance. Similar models of memory also form the backbone of spaced repetition algorithms in Anki and SuperMemo, where the goal is to essentially maintain memories above an activation threshold. [^3]

In one's conceptarium, each document has an activation which changes over time. Documents which have been created recently or have been retrieved frequently (as measured by the user's sustained interest in probing their region of the semantic space) have a higher activation. Just like the creation timestamp, a document's activation is mostly useful when used in tandem with other bits of metadata. For instance, I might want to retrieve documents related to the current context which I'm *specifically unlikely to remember myself*, a complementary "antimemory" system which avoids the redundancy of surfacing thoughts which I already remember myself. Alternatively, I might use the most active documents as a proxy for my current interests in downstream tools for networking.

Together, the semantic embedding, the creation timestamp, and the activation help paint a rich picture of the document's meaning and its relation to our thought process, lending itself to a whole new set of subsequent mechanics. To help conceptualize this representation, I picture it in the following way. Imagine each document as a dot in a three-dimensional space. Over time, more dots are popping up, as documents can only be added to the conceptarium, never deleted. Additionally, each dot has a color, signaling its activation. Newly created dots are bright red, due to their high activation, and they slowly turn blue as they cool down through forgetting. As a final touch, when probing the conceptarium with a query in an attempt to retrieve past documents, a heat wave is propagating outwards from the query location to nearby dots, increasing their activation due to sustained interest.

## Principles

The conceptarium embodies some specific principles about how knowledge is like and how we should work with it. Below is an attempt to articulate those explicitly, to lay bare the author's philosophy in an effort to be transparent.

### Everything is interconnected.

In a knowledge graph, each node is connected to a subset of the other notes through explicit links created by the knowledge worker. They are finite, can't overlap, and require valuable time to create. In contrast, in a conceptarium, all documents are related to each other. They live in the same space, and are just closer or farther away from each other. Additionally, the orientation of the straight line which connects any two dots is deeply informative and codes the semantic relation between the two documents. This principle is explored in much more depth in [Semantica](/tools/semantica/#match). For instance, the document pairs "man" & "woman," "king" & "queen," and "actor" & "actress" have roughly the same relative placements. However, even if we haven't developed a way to visualize, let alone understand, the semantics of high-dimensional spatial layouts, they are still present in the representation as a testament for every thought having *some* unique relation to every other one. [^1]

### Thoughts are not atomic.

In a knowledge graph, each note should be atomic, meaning that it should express one indivisible thing. Those "atoms" are then linked together to form the knowledge graph. The conceptarium, even though its documents are discrete, invites the user to narrow in on arbitrary fragments of a document, to select part of a text or part of an image as the next stop of their train of thought. After the selection is made, the conceptarium can then surface documents related to that specific aspect of the initial one, somewhat like the *Select > Right click > Search DuckDuckGo for "..."* option in browsers, but as the core linking mechanic. In this, each document can be broken down into a virtually infinite collection of fragments, which via the previous principle, can each lead down their own rabbit holes.

{: .border }
![](/assets/images/dynamiclinks.png)

### You are not your thoughts.

The term conceptarium is not just an expansive sound bite. Similar to how a herbarium is used to collect plant samples or how a terrarium is used to collect fragments of living habitat, the conceptarium is used to collect thoughts. It is nothing more than a high-tech Mason jar for those elusive pieces of language and imagery entertained by our minds moment by moment. In this, it helps the user detach themselves from their thoughts, acknowledging that individual insights are more a result of happenstance and memetic dynamics than a reflection of personal worth. Not even the most dedicated knowledge worker can control the momentary weather of their minds, but only the general climate, and the explicit decoupling of the conceptarium helps internalize this belief.

### Building blocks are common nouns.

As opposed to isolated tools, composable building blocks which have interoperability as a core principle enable a combinatorial explosion of workflows. Not only does the user have the freedom to mix and match them until obtaining the desired solution, but tool-makers can focus on designing new useful affordances to fit their workflows, rather than reinventing the knowledge graph. The conceptarium provides a self-contained knowledge store for other tools for thought to build on top of. It manages the nuts and bolts of the unique underlying representation, so that third-party apps don't have to worry about its implementation.

{: .quote }
"For example, I can program with Sublime Text, while my teammate uses vim, and we don’t need to fight to the death to pick one editor between us. There are dozens of text editors to choose from, and no lock-in from proprietary file formats. Contrast this with Google Docs: in order to live collaborate with each other, we all need to use the same editor. For someone who spends their whole working day in Google Docs, this can be a serious limitation. I personally hate doing substantial writing in Google Docs." -- Geoffrey Litt [^4] 

Another way to signal the general scope of such a building block in the making, while also taking advantage of non-commercial goals, is to name it using a common noun. In contrast to a proper noun (e.g. Roam Research), a common noun (e.g. conceptarium) does not signal a branded product or service, but rather a type of *thing* which someone can make use of. Additionally, phrasing the name using common Greek and Latin morphemes enables natural adaptations to a host of European languages. For instance, in Romanian, I would call it "conceptar" (analogous to how "ierbar" means "herbarium"). In Italian, it might be called "concettario," while it Finnish, it might be called "konseptario."

{: .border }
![](/assets/images/buildingblocks.png)

## Architecture

The conceptarium is a minimal server app. A lightweight standardized API only exposes a handful of endpoints, mostly for adding and retrieving documents. The storage of document metadata, the management of document activation, and the ranking of candidate documents based on custom criteria is all managed by the server app behind-the-scenes. It makes use of Python modules like FastAPI and sentence-transformers, but can be packaged in a self-contained Docker environment. It can be deployed from a one-click image on a cloud provider (e.g. DigitalOcean), but can also be deployed on a Raspberry Pi, as its system requirements are manageable. The lightweight API makes it trivial to integrate with services like IFTTT/Zapier (as a webhook), AutoHotKey-like utilities (as a request), browsers (as a search engine), and full-blown third-party tools (as a knowledge store).

## Glimpses

The conceptarium serves as the foundation for other tools to build on and enables a host of novel primitives. Below is a short collection of vignettes depicting the usage of those downstream tools and related mechanics.

### Copy-Recall-Paste

Alice is an architect. Before jumping into 3D modeling and technical drawing, she wants to refine her building concept in a visual canvas similar to [Muse](https://museapp.com/) or [Kosmik](https://kosmik.app/). After creating some initial sketches and adding a few pictures for atmosphere, she feels it's time to bring in concrete ideas. By selecting a sketch she has just drawn and pressing a hotkey, an assortment of related perspectives from her previous projects instantly gets pasted onto the canvas in place of the selection, straight from her conceptarium. She then wonders whether the materials used before would work in the current setting, so she screengrabs the technical annotation, presses a hotkey, and then pastes her written notes on structural properties in a nearby region of the canvas. The hotkey triggered a script which mutated the clipboard contents based on an HTTP request to her conceptarium.

{: .border }
![](/assets/images/inplacerecall.png)

### Cognitive Variance

Bob is a free learner. Besides using [Autocards](/tools/autocards) to make things easier to remember and [Dual](/tools/dual) to break down complex topics, Bob wants to make sure he doesn't spend too much time narrowing in on a single topic, but also wants to avoid wandering around too superficially. In essence, he wants to strike a healthy balance between exploration and exploitation -- he wants to have a sustainable foraging strategy across the infosphere. That's why Bob uses his conceptarium to measure the variance, the sparsity, the breadth of his thinking over time. By computing how *spread out* his thoughts are in semantic space over a period of time using his ideoscope, he can quantify how varied his thinking was. Thoughts too clustered together mean he should broaden his learning, while thoughts too spread out mean he might want to focus more. 

### Mnemonic Microcosm

Charlie is a researcher. He used to think of himself as a kinesthetic type. After having read some papers debunking this distinction, he just admits he loves nature. Every evening, Charlie takes a walk in a nearby park which he uses as his mnemonic microcosm. After using a dimensionality reduction algorithm to project his high-dimensional conceptarium onto the measly three-dimensional space of the park, he can essentially walk through his thoughts. Each physical place in the park hosts a cluster of ideas, a region of the semantic space. Each evening stroll through the high-tech memory palace is linked to a unique thought pattern which Charlie explores both for research and leisure purposes.

{: .quote }
"I finally catch sight of Maria, a few blocks ahead of me -- and right on cue, the existentialist attractor to the west firmly steers me away from the suburbs of cosmic baroque. I increase my pace, but only slightly -- it's too hot to run, but more to the point, sudden acceleration can have some peculiar side effects, bringing on unexpected philosophical swerves." -- Greg Egan [^7]

### Belief System Editor

Dan is a therapist. After a constructive series of sessions with Eve, he feels she came a long way and can now safely rely on self-administered techniques. Dan teaches her how to use the credograph, a computational aid for cognitive-behavioral therapy. For instance, if she wants to get rid of a toxic belief, she first has to enter it manually. It shows up us a node among the other related beliefs retrieved from her conceptarium, forming an intricate directed graph with red and green arcs indicating reinforcing and conflicting beliefs. To help her remove the toxic belief from her belief system, the credograph generates "lever" beliefs which aggressively contradict the target while reinforcing the others as much as possible. A memetic excision using prior beliefs as leverage.

{: .quote }
"The exact words weren't important, though; they weren't a part of the implant itself. It wouldn't be a matter of a voice in my head, reciting some badly written spiel which I could choose to ridicule or ignore; nor would it be a kind of mental legislative decree, which I could evade by means of semantic quibbling. Axiomatic implants were derived from analysis of actual neural structures in real people's brains, they weren't based on the expression of the axioms in language. The spirit, not the letter, of the law would prevail." -- Greg Egan [^8]

### Ideological Overlap

Frank and Grace are both entrepreneurs. While connecting via a video call in an attempt to expand their networks, they decide to pool together their conceptaria to quickly build context and identify common ground. After getting a sense of what active thoughts they have in common, they instantly become aware of new social affordances, new relatable ways to get across to each other. When both are ready, they slowly move towards thoughts which appear *not* to be shared. However, as they're starting from a place of shared understanding, they find it quite easy to appreciate ideas they haven't considered previously. After the call, Grace opens up her navigation system to find the best route to putting herself in the shoes of her clients, by using people across the intervening spectrum as ideological stepping stones.

{: .quote }
"When the robot finally left the Hermit to converse with the sixth clone, Orlando could see all the others watching intently; even the first clone seemed riveted, as if he was extracting some aesthetic pleasure from the five-dimensional batonwaving despite being blind to its meaning. Orlando waited, his guts knotted, as the message passed up the chain towards him. What would happen to these messengers once they'd served their purpose? Bridgers had never been isolated; everyone had been linked to a large, overlapping subset of the whole community." -- Greg Egan [^6]

## Conclusion

The conceptarium is a versatile medium for storing, relating, and surfacing thoughts. Its unique underlying representation opens the possibility of supporting an entirely new tooling ecosystem for knowledge work, briefly hinted at above. The resulting cognitive infrastructure will likely be more than the sum of its building blocks. [^5]

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

[^1]: Christopher Olah,<br/>[Deep Learning, NLP, and Representations](https://colah.github.io/posts/2014-07-NLP-RNNs-Representations/)
[^2]: Daniel Jurafsky & James Martin,<br/>[Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/6.pdf)
[^3]: Jacob Whitehill,<br/>[Understanding ACT-R – an Outsider’s Perspective](https://arxiv.org/pdf/1306.0125.pdf)
[^4]: Geoffrey Litt,<br/>[Bring Your Own Client](https://www.geoffreylitt.com/2021/03/05/bring-your-own-client.html)
[^5]: Paul Bricman,<br/>[Thoughtware](https://paulbricman.com/thoughtware)
[^6]: Greg Egan,<br/>[Diaspora](https://www.gregegan.net/DIASPORA/DIASPORA.html)
[^7]: Greg Egan,<br/>[Stable Orbits In The Space Of Lies](https://www.gregegan.net)
[^8]: Greg Egan,<br/>[Axiomatic](https://www.gregegan.net)