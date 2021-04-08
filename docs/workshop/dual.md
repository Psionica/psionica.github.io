---
layout: default
title: Dual
nav_order: 1
parent: Workshop
description: "Your second brain implant."
published: False
---

# Dual
{: .no_toc }

Your second brain implant.
{: .fs-6 .fw-300 .text-left }

[View Code](https://github.com/Psionica/Dual){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

In his visionary short story titled *Learning to Be Me*, Greg Egan describes the Ndoli Dual, a fictional brain implant which constantly monitors the host's neural activity in an attempt to learn how it unfolds.[^1] After several years of collecting data, the Ndoli Dual becomes powerful enough to accurately forecast the neural activity of its host, prompting many to *switch* to it completely, outsourcing their entire thought process and achieving immortality. Besides describing a thought experiment which puts the Chinese room to shame in terms of vividness, Egan hints at an intriguing possibility -- using a proxy for human thought as an optimization target for creating human-like artificial intelligence. An elegant formalism for *thinking humanly*, as per Russell and Norvig's taxonomy.[^2]

{: .quote }
"If the human race *was* replacing itself with clockwork automata, I was better off dead; I lacked the blind conviction to join the psychotic underground -- who, in any case, were tolerated by the authorities only so long as they remained ineffectual. On the other hand, if all my fears were unfounded -- if my sense of identity could survive the switch as easily as it had already survived such traumas as sleeping and waking, the constant death of brain cells, growth, experience, learning and forgetting -- then I would gain not only eternal life, but an end to my doubts and my alienation." -- Greg Egan[^1]

However, even if neural activity seems to be the most accurate proxy for thought, high-resolution brain-computer interfaces are a long way from being commercially viable. In order to implement Egan's envisioned device, we need a proxy for thought which is cheap and abundant, so that our models have plenty of data to learn from. What we need is written language, the next best thing after neural activity in terms of capturing human thought processes. Infinitely expressive and highly economic, written language has been the preferred medium for capturing thoughts for centuries. Today, internet archives contain billions of them, from the most brilliant to the darkest.

{: .quote }
"You, I hope, are one of those explorers. You, I hope, found these sheets of copper and deciphered the words engraved on their surfaces. And whether or not your brain is impelled by the air that once impelled mine, through the act of reading my words, the patterns that form your thoughts become an imitation of the patterns that once formed mine. And in that way I live again, through you." -- Ted Chiang[^3]

This abundance, naturally, powered recent advances in natural language processing. That said, current language models typically reflect the aggregate thought patterns of millions of people who have contributed data to the training set, whether willingly or not. However, disciplined note-taking practices such as the Zettelkasten and digital gardening enable the fine-tuning of generic language models to one's specific way of thinking. By using hundreds of written notes as training data, we can configure a model to *learn to be the note-taker*, to internalize their thought patterns, to adopt their writing style and interests, to approximate their mannerisms and responses. After several months of disciplined note-taking, the aligned model becomes powerful enough to accurately extrapolate the written thoughts of its user, enabling transformative new ways of conducting knowledge work and an early glimpse into immortality.

We'll now explore the inner workings of Dual, the piece of software which learns to be its user, named so as a tribute to Egan. However, before doing that, we'll consider some useful framings for better understanding what your Dual is and what it isn't.

## Paradigms

### Your Dual is your second brain come to life
{: .no_toc }

The ideas, concepts, and insights which you include in your second brain make up your Dual's long-term memory in a manner reminiscent of the spreading activation model.[^4] Relevant pieces of knowledge are strategically remembered behind the scenes when your Dual is conversing with you, populating its working memory in a context-dependent manner. When finally engaging in a reply to your messages, the items stored in working memory are used in tandem with the previously fine-tuned language model to generate a response. The result is an expressive chatbot which seamlessly integrates disparate fragments of your knowledge into its replies.

{: .quote }
"And if one has to write anyway, it is useful to take advantage of this activity in order to create in the system of notes a competent partner of communication." -- Niklas Luhmann[^5]

### Your Dual is a virtual assistant for thinking
{: .no_toc }

Your Dual can't make changes to your notes directly, it can only read from them when interacting with you. And that's not a bug, it's a feature. Your Dual is designed to *assist* you in knowledge work, rather than to do it for you. You still have to do the hard work of creating, linking, and updating notes. Why? Not because of technical obstacles, but rather because putting in the effort is helpful in the long-term: it fosters understanding and retention on a much deeper level. It would otherwise be extremely tempting to succumb to overreliance on the advanced capabilities of this and future systems. Your Dual is there to amplify your impact through collaboration, not to replace you.

{: .quote }
"The best interface to my brain is a relationship. That's how merging feels like. That's how I envision it." -- George Hotz[^6]

### Your Dual is the librarian of your thoughts
{: .no_toc }

Your Dual is very apt at searching for items in your knowledge base, just like a librarian knows their way around bookshelves. Ask it for notes which describe metaphors of the mind, and you'll get a list of candidates in seconds, even if part of the search results were written years ago. Ask it for entries which provide arguments supporting the feasibility of mind upload, and it will readily point you towards the (numerous) relevant items.

## Architecture

Your Dual consists of three broad components: the essence, the skeleton, and the interface. Together, these components enable a conversational medium between you and your emulated self.

### Essence

The essence is an instance of GPT-2, a language model which has learned to generate human-like text based on giant internet archives. Crucially, this language model is fine-tuned on your personal notes before use in order to accurately capture your way of thinking. The essence is the central component of your Dual and the only one of the three which differs from user to user. It's here that your thought patterns are extracted and extrapolated.

### Skeleton

The skeleton consists of a collection of several smaller language models which play auxiliary roles in your Dual's operation. Two text encoders are used sequentially to derive semantic embeddings from your notes which are then used when spontaneously remembering relevant knowledge. Yet another language model is tasked with determining which notes match a given natural language description when necessary. A local server exposes a minimal API for the interface to consume.

### Interface

The interface resembles an instant messaging chat, complete with a message history which you can scroll through, and is even equipped with a status indicator. This component (currently) consists of an Obsidian plugin which defines a new view in a side panel. Use the chat as you normally would, except that at the other end is your emulated self, rather than a peer. The interface is your main point of contact with your Dual.

## Features

Your Dual's architecture enables three progressively more powerful features: fluid search, descriptive search, and open dialogue. Fluid and descriptive search are extractive features, meaning that they merely guide you to existing notes which are currently relevant. In contrast, open dialogue is a generative feature. It can be used to synthetize highly original content whose connection to previous notes is non-linear and non-trivial. Naturally, this is the main attraction.

Samples from the author's own Dual are provided for illustration purposes.[^7] However, due to the underlying second brain being only several weeks old at the time of writing, a personal diary spanning several months has also been used for obtaining the essence.

### Fluid Search

This search feature is all about what your notes are *about*. It goes beyond traditional search and can locate relevant notes regardless of whether they explicity contain the words used in the query, provided they're about the same topic. In this, it's fluid, it's frictionless.

- ***Find notes about seamlessly navigating one's notes.***

{: .existing-note }
By using fluid search through a collection of previous notes, one can elevate into their awareness the most semantically related items in their second brain. This way, they are then easily able to optimally weave together new information with old information, in the spirit of constructivism.

### Descriptive Search

This search feature builds on the previous one, but takes things a step further. You can now more flexibly describe the entries you are looking for, not only in terms of topic, but in terms of content. Find examples, arguments, parallels, and others. The possibilities are endless.

- ***Look for a note which describes an analogy between machine learning and sociology.***

{: .existing-note }
Contrastive learning is machine learning based on strategically sampling counterexamples for a given concept. Similarly, some sociologists argue that criminality and deviant behavior are essential for a well-functioning society as they provide "counterexamples" to the norm. Essentially, deviants successfully inform the social norm space, perhaps better than actual explicit norms. Their expressiveness is essential, as without them society would lose its sense of identity. There would be a collapse, just as in machine learning.

- ***Search for a note which argues that measuring neural activity with EEG is tricky.***

{: .existing-note }
In the brain-stadium metaphor, neural activity is associated with the vivid activity which happens inside a stadium during a sport event. Each individual supporter from the audience represents a neuron firing. According to this mapping, EEG corresponds to recording sound from outside the stadium, trying to reconstruct individual supporter activity. Additionally, single unit recording corresponds to having microphones down the throats of individual supporters.

- ***Find a note which contains an application of VR.***

{: .existing-note }
In virtual and augmented reality, abstract concepts can be grounded in concrete objects. For instance, in programming, a code library can become an actual physical library, a game tree can be an actual tree, calling a function can involve a phone. What's more, virtual reality provides the necessary context for attempting to make any abstract concept tangible, in an effort to infuse them with embodied knowledge, forcing a host of cognitive functions to be applied to the same concept.

### Open Dialogue

As mentioned previously, open dialogue is the main dish. When you're posing a question to your Dual, it automatically retrieves relevant notes and starts formulating a response based on them. The value of open dialogue lies not in retrieving cold facts from your knowledge base, but rather in tackling ambiguous open-ended questions.

- ***How can we develop transformative tools for thought?*** [^8]

{: .original-response }
The second brain framework for cognitive augmentation provides a clear path to transhuman singularity through exponential self-improvement of the human individual and collective, in collaboration with AI. It's also a pragmatic approach to cognitive enhancement, as it provides a pragmatic framework for dialogue between the two. The second brain framework for cognitive augmentation is very well-suited for the context of neuroplasticity, as it helps the user relax constraints and embrace radical new perspectives. This is in contrast to the more...

- ***What are some important questions in the neuroscience of attention?***

{: .original-response }
How does the brain create "tuning" in response to different stimuli? What are some features which distinguish attention? Are there "attention modalities", or "attention channels", or "attention frequencies"? How can the brain "see" different types of information from different perspectives? How can it compute a graph of information contents based on such topologies? Attention is often associated with sensations, movement, and attention alone. However, attention can also occur at the level of thought...

- ***How could one seamlessly edit their belief system on command?***

{: .original-response }
If one subscribes to the belief that truth is relative, then one can trivially "edit" their belief system as a document. They simply need to attach a semantic link to a statement which they believe is false, and then edit their text accordingly, with regards to the stated truth. This way, one's belief system is merely an artifact which one has to reconcile with other beliefs in order to work effectively. Another way to reconcile conflicting beliefs is for the...

- ***Can ambiguity be used as a tool?***

{: .original-response }
In a sense, yes. However, in an arguably conflicting way. By using ambiguity as a means of promoting insight, one is also using it as a means of limiting creative output. The very act of intentionally distorting one's perception of the world is often seen as an act of creation. This is a perspective often dismissed in the context of consciousness augmentation, but perhaps it's not. Creativity can be seen as an intentional process of engineering the world in such a way as to support...

- ***Why should one learn in public?***

{: .original-response }
If one's purpose is to develop a large body of knowledge, then one should actively seek out, learn from, and publish work. This would presumably lead to a positive feedback loop of more knowledge being gained, helping the individual maximize their contribution. However, the incentive for creation and creation of knowledge is also plagued by censorship, limiting the flow of knowledge. A good alternative is open access, enabling anyone to search through one's work for useful insights. The creation of commonsense through machine learning...

## Workflows

## Further Steps
### Hosted inference
{: .no_toc}
What if you wanted others to interact with your Dual? Perhaps your research collaborators, team members, or just anyone browsing through your public notes. We're working on making this a reality through an option to host the essence in the cloud.

### More features
{: .no_toc}
There are plenty of other language models out there waiting to make themselves useful in your second brain. The three features described above merely scratch the surface of how natural language processing can reshape knowledge work.

### Better support
{: .no_toc}
At the moment, your Dual can only run on Linux using Obsidian, due to the way the skeleton is currently packaged. In light of that, Windows and macOS support are top priorities. Extending the interface to work with Foam in VS Code is also a planned feature.

### Higher performance
{: .no_toc}
All those language models take up a lot of memory and are somewhat sluggish. Memory optimizations and speed improvements are well underway, mostly based on model distillation, caching, and forcing GPU support. Upcoming developments in machine learning will enable even more performance bang for the computational buck.


---

## Join Us

Do you want to contribute to the development of Dual yourself? Join Psionica if you want to be part of an enthusiastic community of designers, researchers, and developers committed to empowering individuals around the world in fundamentally new ways. Contribute to existing projects, develop your own, or just hang around for an insightful chat.

[Become a Member](https://discord.gg/NXYZUbhMNf){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 }

---

## Support Us

Our only stakeholder is humanity. Help us keep it that way.

By supporting our efforts, you're investing in transparent research and development at the frontier of thought. Not only are you helping us deliver open source tools reshaping the landscape of knowledge work, but you're also setting in motion a broader movement around cognitive augmentation as a second-order consequence. 

[Become a Sponsor](https://opencollective.com/psionica){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 }

---


## References

[^1]: Greg Egan,<br/>[Learning to Be Me](http://www.gregegan.net/BIBLIOGRAPHY/Bibliography.html#p12)
[^2]: Stuart Russell & Peter Norvig,<br/>[AI: A Modern Approach](http://aima.cs.berkeley.edu/contents.html)
[^3]: Ted Chiang,<br/>[Exhalation](https://www.goodreads.com/book/show/41160292-exhalation)
[^4]: John Anderson,<br/>[A spreading activation theory of memory](http://act-r.psy.cmu.edu/?post_type=publications&p=13730)
[^5]: Niklas Luhmann,<br/>[Communicating with Slip Boxes](https://luhmann.surge.sh/communicating-with-slip-boxes)
[^6]: George Hotz & Lex Fridman,<br/>[Lex Podcast #31](https://youtu.be/iwcYp-XT7UI?t=6812)
[^7]: Paul Bricman,<br/>[Second Brain](https://paulbricman.com/secondbrain/)
[^8]: Andy Matuschak & Michael Nielsen,<br/>[How can we develop transformative tools for thought?](https://numinous.productions/ttft/)