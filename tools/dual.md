---
layout: default
title: Dual
nav_order: 1
parent: Tools
description: "Amplifying knowledge work through user-defined assistants."
published: True
image: /assets/images/dual-thumbnail.png
---

# Dual
{: .d-inline-block .mt-4 .no_toc }

STAGE 3
{: .label }

Amplifying knowledge work through user-defined assistants.
{: .fs-6 .fw-300 .text-left .mb-0 .mt-0 }

By @benjamin, [@thoughtware.engineer](https://paulbricman.com/)
{: .mt-1 }

[Watch Demo](https://youtu.be/58-Ue2mDy0k?t=3236){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [View Code](https://github.com/Psionica/Dual){: .btn .fs-5 .mb-4 .mb-md-0 .mr-2 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

In his visionary short story titled "Learning to Be Me," Greg Egan describes the Ndoli Dual, a fictional brain implant which constantly monitors the host's neural activity in an attempt to learn how it unfolds.[^1] After several years of collecting data, the Ndoli Dual becomes powerful enough to accurately forecast the neural activity of its host, prompting many to *switch* to it completely, outsourcing their entire thought process and achieving immortality. Besides describing a thought experiment which puts the Chinese room to shame in terms of vividness, Egan hints at an intriguing possibility -- using a proxy for human thought as an optimization target for creating human-like artificial intelligence. An elegant formalism for *thinking humanly*, as per Russell and Norvig's taxonomy.[^2]

{: .quote }
"If the human race *was* replacing itself with clockwork automata, I was better off dead; I lacked the blind conviction to join the psychotic underground -- who, in any case, were tolerated by the authorities only so long as they remained ineffectual. On the other hand, if all my fears were unfounded -- if my sense of identity could survive the switch as easily as it had already survived such traumas as sleeping and waking, the constant death of brain cells, growth, experience, learning and forgetting -- then I would gain not only eternal life, but an end to my doubts and my alienation." -- Greg Egan[^1]

However, even if neural activity seems to be the most accurate proxy for thought, accessible high-resolution neuroimaging techniques are a long way from being commercially viable. In order to implement Egan's envisioned device, we need a proxy for thought which is cheap and abundant, so that our models have plenty of data to learn from. What we need is written language, the next best thing after neural activity in terms of capturing human thought processes. Infinitely expressive and highly economic, written language has been the preferred medium for capturing thoughts for centuries. Today, internet archives contain billions of them, from the most brilliant to the darkest.

{: .quote }
"You, I hope, are one of those explorers. You, I hope, found these sheets of copper and deciphered the words engraved on their surfaces. And whether or not your brain is impelled by the air that once impelled mine, through the act of reading my words, the patterns that form your thoughts become an imitation of the patterns that once formed mine. And in that way I live again, through you." -- Ted Chiang[^3]

This abundance, naturally, powered recent advances in natural language processing. That said, current language models typically reflect the aggregate thought patterns of millions of people who have contributed data to the training set, whether willingly or not. However, disciplined note-taking practices such as the Zettelkasten and digital gardening enable the fine-tuning of generic language models to one's specific way of thinking.[^15] By using hundreds of written notes as training data, we can configure a model to *learn to be the note-taker*, to internalize their thought patterns, to adopt their writing style and interests, to approximate their mannerisms and responses. After several months of disciplined note-taking, the aligned model becomes powerful enough to accurately extrapolate the written thoughts of its user, enabling transformative new ways of conducting knowledge work and an early glimpse into immortality.

We'll now explore the inner workings of Dual, the piece of software which learns to be its user, named so as a tribute to Egan. However, before doing that, we'll consider some useful framings for better understanding what your Dual is and what it isn't.

---

## Paradigms

### Your Dual is a skilled virtual assistant for knowledge work
{: .no_toc }

While conversing with your Dual, you can ask it to help you with things. You might want to find notes related to a certain topic, brainstorm research questions, or get your hands on a summary of an article. What your Dual can do for you is entirely determined by its set of skills, also refered to as its skillset. Skills are simply Markdown files which specify the desired behavior of your virtual assistant *in natural language*.[^16] Generally, you can teach it new skills by merely describing them in plain English (or in other languages, for that matter). Following this learning phase, your Dual not only adopts your way of thinking, but can also use its skills to best follow your commands before producing responses as chat messages.

{: .quote }
"The best interface to my brain is a relationship. That's how merging feels like. That's how I envision it." -- George Hotz[^6]

### Your Dual is your second brain come to life
{: .no_toc }

The ideas, concepts, and insights which you include in your second brain make up your Dual's long-term memory. When using skills based on this memory system, relevant pieces of knowledge are strategically remembered behind the scenes in a context-dependent manner. More often than not, those memories are used to provide an explicit context for the previously fine-tuned language model when producing an original response. The end result of using this cognitive architecture is an expressive chatbot which seamlessly integrates disparate fragments of your knowledge with your style of writing.

{: .quote }
"And if one has to write anyway, it is useful to take advantage of this activity in order to create in the system of notes a competent partner of communication." -- Niklas Luhmann[^5]

---

## Structure

As mentioned before, your Dual has at its core a fine-tuned language model. Currently, it's using GPT-2, a language model which has been open sourced in late 2019 and can run on average consumer hardware.[^17] However, in the upcoming months, Dual will advance to GPT-Neo, an open source replica of GPT-3 created by [EleutherAI](https://www.eleuther.ai/) which outperforms GPT-3 on many benchmarks.[^18] We're very pleased that different open collectives can build on each other's work so easily thanks to the open source ecosystem. For users who want to opt-out of running the language model on their machine for free, we'll provide a wrapper around OpenAI's hosted [offering](https://beta.openai.com/pricing).

Another essential component of Dual is the skill interpreter. It orchestrates the use of skills at a high-level, and is responsible for the following: determining when to use what skill, keeping track of skills which use other skills, understanding your commands, and so on. It's conceptually similar to a traditional interpreter of programming languages, such as the Python or Javascript ones, but it's designed to interpret natural language expressed in plain text and then act on it. In this, Dual is also an important step in developing a new programming paradigm, one based on humane representations such as natural language or 3D scapes, as opposed to clunky symbolic syntax.[^19] [^20]

Interacting with Dual is done through a familiar chat interface. Dual is reading your messages and then typing out responses using its skills. The chat has full support for Markdown formatting, meaning that if your Dual eventually sends you a list, a table, or even an image, they all get rendered in the chat as responses. While the current implementation is packaged as an [Obsidian](https://obsidian.md/) plugin, Dual will integrate with other tools in the future (e.g. [Roam Research](https://roamresearch.com/)). Mobile speech interfaces around Dual are also on the table.[^21]

As teaching Dual to recreate itself from scratch is somewhat beyond the capabilities of current language models, Dual itself is implemented using several programming languages. Managing the language model was initially done using [Python](https://huggingface.co/transformers/), but we're experimenting with [Rust](https://github.com/guillaume-be/rust-bert) and [Javascript](https://www.tensorflow.org/js) for better cross-platform support. The skill interpreter and the interface are both written in Typescript, playing nicely with an Electron app like Obsidian.

---

## Skills

This section provides a brief tour of the types of skills your Dual can currently acquire. This isn't designed to serve as an in-depth tutorial, just as a quick glance at the skills you can teach Dual using Markdown. Skills and examples of using them are provided together in the actual screenshots below, with the skill files on the left and the chat conversations on the right. Keep in mind that only *rendered* Markdown is shown, for simplicity. 

For starters, let's say you're a researcher in academia and want to teach your (virtual) assistant how to come up with research questions on different subjects. To best explain this task, you might choose to provide a few examples of what you consider to be good research questions. This is what happens in the first few lines of the file listed below (have a look!). However, remember that you want to teach it how to come up with suggestions on *new* subjects. To describe this task, you might use the placeholder `*subject*` and ask it to complete the pattern with a new sentence. Placeholders are automatically filled in when the skill is used for following commands.

{: .border }
![](/assets/images/dual_formulate_research_questions.png)

After teaching your Dual this skill (by simply creating the skill file), it will automatically figure out when and how to use it, as can be seen in the chat. Actually, the `Write a paragraph...` part is just another command you can issue to your Dual yourself in the chat! It's skills building on each other all the way down.

The next example is similar. Provide some examples, a placeholder or two, ask it to complete the pattern, and you just taught it a new skill. You can use any placeholders you wish  (e.g. `*person*`, `*language*`, `*property*`) and provide as many of them as you like. Dual knows how to fill them in automatically, provided you actually specify them in your commands.

{: .border }
![](/assets/images/dual_find_related_concepts.png)

However, providing examples might not always be the best way of teaching a skill. For instance, let's say you'd like your Dual to know how to answer open-ended questions using knowledge from your notes. In only a few lines of text, you can specify that exact behavior without even providing examples. Placeholders get filled in as usual, notes related to the topic are being retrieved, and the pattern gets completed. You can teach it skills which build on any number of other skills.

{: .border }
![](/assets/images/dual_answer_open_questions.png)

The following skill is also learned in a *zero-shot* fashion, meaning that no examples are provided, as opposed to the first two skills which were acquired in a *few-shot* way. If you got what those terms refer to, you have a pretty good chance of understanding the main innovation introduced by the GPT-3 paper, which is applied here to other language models.[^13] Actually, Dual can also be seen as simply a framework for prompt engineering plus some handy features for enabling a conversational interface.

The skill below is all about prompting the user to reflect on certain topics described in their notes. You might have also noticed `#0` being used several times in those examples. That's indeed probably the least natural part of the otherwise pretty casual "syntax" used here. `#0` is simply shorthand for "everything before this block," while using `#1` would refer to the result of the first block, and so on. This design choice was inspired by an exploration of approaches to capability amplification created by [Ought](https://ought.org/), another non-profit operating in this space.[^14]

{: .border }
![](/assets/images/dual_formulate_questions.png)

You can teach your Dual skills using plain natural language. However, if you want to prescribe a more programmatic task, such as computing the result of a mathematical expression or fetching data from an endpoint, you can also throw in some snippets of code by simply using existing Markdown code blocks. Because those blocks are interpreted differently, Markdown files become analogous to [Jupyter](https://jupyter.org/) or [Observable](https://observablehq.com/@freedmand/sounds) notebooks. 

Back to the skill below. This one relies on some Javascript to get information about a certain entity from [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page), a machine-friendly Wikipedia spin-off which advocates for linked open data. Even in the occasional case when you resort to writing code, you're still free to use placeholders (e.g. `*entity*` and `*property*` below), making it possible to mix highly deterministic code with fuzzy command parsing. The dawn of versatile user-defined assistants which can integrate with any number of [IFTTT](https://ifttt.com/home) services?

{: .border }
![](/assets/images/dual_ask_wikipedia.png)

This section merely provides an overview of how your Dual acquires skills. You could teach it to come up with metaphors, summarize short documents, suggest writing prompts, and what not. All in a local-first, user-defined, and open source way. You can have a look at [this awesome list](https://www.buildgpt3.com/) for inspiration on framing all sorts of tasks as text generation, from writing code based on a natural language description to formulating arguments and counter-arguments. More resources on teaching Dual such skills will follow once it will graduate from an alpha version. 

---

## Further Steps

What we've made is only the beginning. Here are other ideas to take the project, given further investment of time and other resources.

### Streamlining installation
Making it simple to get Dual running would help get users onboard, especially in the Obsidian environment. Ideally, a one-click install would make it accessible for non-technical users as well.
{: .no-toc }

### Documentation
Documenting the Markdown-like language for defining skills and the API for interacting with the server component would make it easy for users to get started and tweak it to their own needs.
{: .no-toc }

### Standalone version
Developing Dual for Obsidian is a great first step, with many users gaining a deeper access to their notes. By creating a standalone client, with access from the commandline or other clients, Dual can be a consistent tool for thinking outside of the Obsidian ecosystem. 
{: .no-toc }

### Skills hub
Users are able to share Dual skills among themselves by essentially transferring the relevant Markdown files. A hub or market for such files would make it easier for users to teach their Duals new skills.
{: .no-toc }

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

[^1]: Greg Egan,<br/>[Learning to Be Me](http://www.gregegan.net/BIBLIOGRAPHY/Bibliography.html#p12)
[^2]: Stuart Russell & Peter Norvig,<br/>[AI: A Modern Approach](http://aima.cs.berkeley.edu/contents.html)
[^3]: Ted Chiang,<br/>[Exhalation](https://www.goodreads.com/book/show/41160292-exhalation)
[^4]: John Anderson,<br/>[A spreading activation theory of memory](http://act-r.psy.cmu.edu/?post_type=publications&p=13730)
[^5]: Niklas Luhmann,<br/>[Communicating with Slip Boxes](https://luhmann.surge.sh/communicating-with-slip-boxes)
[^6]: George Hotz & Lex Fridman,<br/>[Lex Podcast #31](https://youtu.be/iwcYp-XT7UI?t=6812)
[^8]: Andy Matuschak & Michael Nielsen,<br/>[How can we develop transformative tools for thought?](https://numinous.productions/ttft/)
[^9]: Greg Egan,<br/>[Closer](https://www.gregegan.net/MISC/CLOSER/Closer.html)
[^10]: Andy Matuschak,<br/>[Prefer explicit associations to inferred associations](https://notes.andymatuschak.org/Prefer_explicit_associations_to_inferred_associations)
[^11]: Andy Matuschak,<br/>[Writing forces sharper understanding](https://notes.andymatuschak.org/Writing_forces_sharper_understanding)
[^12]: Ben Balter,<br/>[Why everything should have a URL](https://ben.balter.com/2015/11/12/why-urls/)
[^13]: OpenAI,<br/>[Language Models are Few-Shot Learners](https://arxiv.org/pdf/2005.14165.pdf)
[^14]: Ought,<br/>[A taxonomy of approaches to capability amplification](https://ought.org/research/factored-cognition/taxonomy#pointers)
[^15]: David Clear,<br/>[Zettelkasten](https://writingcooperative.com/zettelkasten-how-one-german-scholar-was-so-freakishly-productive-997e4e0ca125)
[^16]: Matt Cone,<br/>[The Markdown Guide](https://www.markdownguide.org/getting-started/)
[^17]: OpenAI,<br/>[Language Models are Unsupervised Multitask Learners](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)
[^18]: EleutherAI,<br/>[GPT-Neo](https://github.com/EleutherAI/gpt-neo)
[^19]: Bret Victor,<br/>[The Humane Representation of Thought](https://vimeo.com/115154289)
[^20]: Vi Hart & Evelyn Eastmond,<br/>[Explorations into Embodied Knowledge and AR/VR](https://youtu.be/FLENZ_si7N8?t=1947)
[^21]: Michael Hansen,<br/>[voice2json](https://voice2json.org/)