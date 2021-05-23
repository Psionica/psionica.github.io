---
layout: default
title: MemNav
nav_order: 3
parent: Lab
description: "Expanding propositional memory through text mining."
published: True
---

# Memory Navigator
{: .no_toc }

Expanding propositional memory through text mining.
{: .fs-6 .fw-300 .text-left .mb-0 }

By Paul Bricman
{: .mt-1 }

[View Code](https://github.com/Psionica/MemNav){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [View Spec](https://github.com/Psionica/psionica.github.io/issues/4){: .btn .fs-5 .mb-4 .mb-md-0 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Text Mining

Many of us routinely use search engines to navigate the internet. They help us find information so quickly and accurately that it's hard to imagine browsing the internet without them. Their convenience even makes us perceive searchable information as less worthy of committing to memory.[^1]

Text mining is one of the core technologies behind search engines. By extracting meaning from text, search engines can easily match queries to appropriate pages. To get a sense of why language understanding is so important, imagine trying to find the details of preparing a meal in a cookbook written in a foreign language. Without text mining, search engines would similarly be limited to exact string matches, with no other means of navigating the rich body of knowledge they have at their disposal.

Due in large part to its extensive business value, text mining is a relatively mature technology. From question answering to summarization, state-of-the-art solutions are proposed every few months.[^2] What if we could leverage this traction, and repurpose text mining in order to support powerful tools for thought? In the following sections, we'll specifically explore the potential of this technology in navigating, and ultimately augmenting, human memory.

## Machine-Readable Memories

In order to create tools capable of navigating memories, we first need to record them in a machine-readable format. One popular way of transcribing memories is journaling. By creating regular entries describing their daily thoughts, ambitions, and stories, people unknowingly build a genuine knowledge base of their lives. Slowly but surely, this accumulates into a comprehensive body of knowledge which spans months, years, or even decades.[^7]

Diaries mainly consist of text. As we've seen previously, machines are already fluent in text. This means that journaling is a very good candidate for supplying our future system with memories in a machine-readable format. In order to perform text mining, simply substitute web pages for diary entries, and let the algorithms do their job.

{: .quote }
"A memex is a device in which an individual stores all his books, records, and communications, and which is mechanized so that it may be consulted with exceeding speed and flexibility. It is an enlarged intimate supplement to his memory. The lawyer has at his touch the associated opinions and decisions of his whole experience [...] The physician, puzzled by a patient's reactions, strikes the trail established in studying an earlier similar case [...] The historian, with a vast chronological account of a people [...]" -- Vannevar Bush[^10]

---

## Design

Now that we have a way of converting memories into a machine-readable format, we can start implementing the actual features of the memory navigator, or MemNav for short. Illustrative samples from my own MemNav instance are provided for each command.

The functionality of the system is encapsulated in a Python class which requires a root directory containing entries as text files. The source code builds on several open source modules, and is heavily inspired by the examples provided by their authors.[^8] [^9]

{: .code-block }
    >>> from memnav import MemNav
    >>> mn = MemNav('../MorningPages')

### Semantic Search

Internet search engines aren't constrained to the exact words in your query. If a page refers to the same thing as your query, but with a slightly different wording, then the page is still likely to show up in the search results. MemNav uses similar techniques to help users retrieve information beyond a simple *Find in text* look-up.

{: .code-block }
    >>> mn.search('embodied tools for thought')
    There was this announcement about a course on embodied critical thinking, which was at an intersection of philosophy, cognitive science, AI, and seems to be quite relevant for the tools for thought direction I chose recently. Yeah, actually I think I might apply. There's also a summer school in Iceland or something.

    >>> mn.search('text mining memories')
    However, the propositional memory miner may change that, repurposing this whole thing, making it more valuable. Really curious to see whether that will result in anything useful or whether it will be just a witty hack of repurposing SOTA NLP models.

    >>> mn.search('fMRI data processing')
    He suggested that we perform a deconvolution on the fMRI data in order to provide a better target for the model. But, what if we include the BOLD response convolution as the final step of the model and make it so that it has no learnable parameters. That's interesting because the deconvolution operation per se doesn't have a clear solution.

{: .info }
Notice how the output of the second command contains none of the exact words present in the query. Finding all slight variations by hand would have been tedious.

{: .info }
The summarization and semantic search samples might look similar. In reality, semantic search returns multiple results, one of which is included here as an illustration.

### Question Answering

When navigating the internet, you might often want a quick answer to a question, rather than a full-blown article on the subject. By systematically identifying relevant phrases in diary entries, MemNav can reliably answer questions about one's previous thoughts, ideas, and experiences.

{: .code-block }
    >>> mn.ask('Who did I spend the last day of 2020 with?')
    Bea

    >>> mn.ask('Why would k-probes be useful?')
    To reflect on things I learned that day

    >>> mn.ask('What does exosomatic mean?')
    Outside the body

### Summarization

Maybe you're not looking for an explicit detail, but you're trying to get the general *gist* of a subject. By choosing a few sentences which together convey the most information, MemNav provides users with a condensed overview of what they're interested in.

{: .code-block }
    >>> mn.summarize('attention in humans and machines')
    What if the query, key, value metaphor used in transformers to attend to things and places was used in a cognitive architecture, building a cognitive model for attention. The transformer is based on a couple forms of attention, but how does that relate to attention in humans and animals?

    >>> mn.summarize('dust theory')
    Egan is simply mindblowing. This idea of Dust Theory is deep, it's powerful. And the point is that this ever expanding computer being run in a cellular automaton would run based on dust. Based on patterns spread out across time and space. But this is not all! In the book they talk about such a representation.

    >>> mn.summarize('grading assignments')
    It's mostly the gruntwork of grading and watching and attendance and so on. Not fulfilling at all. It's still only a part time job. But the part about grading homework isn't my favorite thing ever, it is the whole idea of selling time for money again. And I'm pretty sure homework can be redesigned so that it can be more efficiently graded, even automatically.

---

## Paradigms

It might be useful to go beyond the technicalities and reflect on the very identity of this project. By taking various perspectives on it, we can get a better sense of the interplay between tools for thought and existing technical frameworks.

### Search Engines

This is the view behind the opening paragraph. MemNav can intuitively be likened to a search engine. Instead of searching the internet, it searches memories. It achieves this by using diary entries as a proxy.

If internet search engines already nudge us into neglecting searchable information, it might be important to investigate the psychological effects of using such mnemonic engines, bringing up debate on the line between voluntary usage and dependence. The fragility of human memory is actually useful in many ways. It supports all sorts of clever mental shortcuts. For example, the availability heuristic piggybacks on our forgetfulness and helps us quickly gauge the frequency of an event. By simply using the *ease* of remembering a few occurences as a proxy, it side-steps the need of actually considering *all* event instances. It turns out that many of our mental quirks are better described as double-edged swords, rather than down-right flaws.[^6] Simply making away with them might lead to unintended consequences.

Additionally, if internet search engines already grant varying degrees of exposure to items based on financial contributions, then what would happen if third-party memory systems would also follow financial incentives? Which memories would be more profitable, and therefore more likely to be remembered? Such daunting prospects further support the need for humane values being embedded in technology.

### Expert Systems

Early AI research had a strong focus on expert systems. Take the expertise of a doctor, embed it into propositional statements and inference rules, and you get a system which can give diagnostics with decent accuracy. Do the same with the expertise of a judge, and you get a system capable of giving rudimentary verdicts in court. MemNav can also be seen as an expert system. It's not an expert in medicine or law, but an expert in *you*. An expert in your thought process. You first embed your expertise in it, and then work with it.

How does it feel to outsource such highly personal knowledge to a machine? How does it feel to interact with an expert in your thought process other than yourself? Would you allow it to freely interact with others on your behalf, as a matter of convenience? Granting my significant other experimental access to my MemNav already feels peculiar. Outsourcing more mental faculties to machines and integrating more third-party components into our thinking will force us to ask such questions increasingly often.

### Exosomatic Memory

When your computer runs low on storage, you might move a few files to an external drive or to the cloud. What happens when your memory is overloaded with tasks, events, plans, ideas, and so on? You might offload that burden onto convenient task managers, calendars, planners, notebooks, and so on. Those can be collectively refered to as exosomatic memory systems (i.e. memory systems located outside the body). MemNav can also be considered an instance of such a system.

However, when you happen to expand the storage capacity of your device, say by upgrading your local storage or by purchasing cloud storage, more often than not you stop being cautious about your memory usage. A constrained memory system might force you to focus on the right things, in a way a set of storage buckets replicated across multiple server farms might not. 

Another thing to consider is the changing relation between memory acquisition and retrieval. The way we learn things strongly influences the way we remember them. For instance, knitting together a tight network of associations has been shown to foster subsequent retrieval.[^5] However, if memories are stored in a machine-readable format, then they may be subjected to a wide range of programmatic transformations. Attach definitions to terms. Break text blocks into atomic interconnected items. Form new links in the semantic network. Those possibilities might pave the way for new educational practices.

### The Mind's API

When a piece of software exposes an API, it offers an interface to third-party software as a means of programmatically interacting with it. MemNav can also be seen as an API. It offers programmatic access to your memories, enabling an entire suite of tools to integrate with it. This API is currently read-only, as it only offers indirect access to your thought process through the text artifacts. Your actual memory is separated from MemNav as a result of the one-way process of creating the artifacts. However, the artifacts being processed may get closer to their authors over time, eventually leading to authors identifying with them.

---

## Further Steps

Despite its promising performance, MemNav has several shortcomings which currently limit its potential in augmenting memory. First, it runs slow enough to feel unnatural as an extension of your memory. With a large corpus, it usually takes several solid seconds for results to be provided, depending on the task. However, clear trends in decreasing compute costs might solve this problem in the long run.

{: .quote }
"In order to function as exosomatic memory, information retrieval systems must be so good so that retrieving information is like remembering." -- Gregory Newby[^3]

Second, creating the knowledge base which underlies MemNav takes time. It requires a sustained regular commitment, and may become tedious. However, future methods will likely enable more efficient ways of recording memories. Using a speech-to-text service would easily triple the rate of transcribed words per minute. Wearable and handheld devices already bring in a multimedia dimension to the endeavor. Neural interfaces might obviate the need for words entirely.

Finally, there's a more nuanced issue. The linear structure of a diary might be a very poor representation of the non-linear structure of thought. The programmatic transformations mentioned previously may be crucial in better aligning the cognitive space with the information space.[^4] High-dimensional representations similar to the ones used by [Semantica](/docs/tools/semantica/) might be a much better fit for the task.

Despite its current flaws, MemNav manages to provide an insightful vantage point on the nature and impact of future tools for thought. The reflections it supports are as valuable as the functions it enables, as it helps us paint a picture of our desired technological path.

---

## Acknowledgments

Our work is supported by awesome sponsors:
- [Andreas Stuhlmüller](https://stuhlmueller.org/)
- [David Dohan](https://twitter.com/dmdohan)
- [Yang Wao](https://twitter.com/yangwao)

## Support Us

Our only stakeholder is humanity. Help us keep it that way.

By supporting our efforts, you're investing in transparent research and development at the frontier of thought. Not only are you helping us deliver open source tools reshaping the landscape of knowledge work, but you're also setting in motion a broader movement around cognitive augmentation as a second-order consequence.

[Become a Sponsor](https://opencollective.com/psionica){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 }

---

## Join Us

Do you want to contribute to the development of this project yourself? Join Psionica if you want to be part of an enthusiastic community of designers, researchers, and developers committed to empowering individuals around the world in fundamentally new ways. Contribute to existing projects, develop your own, or just hang around for an insightful chat.

[Become a Member](https://discord.gg/NXYZUbhMNf){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 }

---

## References

[^1]: Sparrow et al.,<br/>[Cognitive Consequences on Having Information at Our Fingertips](https://scholar.harvard.edu/files/dwegner/files/sparrow_et_al._2011.pdf)
[^2]: Papers with Code,<br/>[Language Modelling Performance over Time](https://paperswithcode.com/sota/language-modelling-on-penn-treebank-word)
[^3]: Gregory Newby,<br/>[Newby on Cognitive Space](https://www.petascale.org/presentations/302-Feb02.html)
[^4]: Gregory Newby,<br/>[Cognitive space and information space](https://onlinelibrary.wiley.com/doi/abs/10.1002/asi.1172)
[^5]: Daniel Reisberg,<br/>[Cognition: Exploring the Science of the Mind](https://openlibrary.org/books/OL16768407M/Cognition)
[^6]: Buster Benson,<br/>[Cognitive Biases](https://busterbenson.com/piles/cognitive-biases/)
[^7]: Buster Benson,<br/>[Better Than Meditation](https://medium.com/better-humans/better-than-meditation-12532d29f6cd)
[^8]: HuggingFace,<br/>[Transformers Documentation](https://huggingface.co/transformers/)
[^9]: Nils Reimers & Iryna Gurevych,<br/>[Sentence-Transformers Documentation](https://www.sbert.net/index.html)
[^10]: Vannevar Bush,<br/>[As We May Think](https://www.w3.org/History/1945/vbush/vbush6.shtml)