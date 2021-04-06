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

In his visionary short story titled *Learning to Be Me*, Greg Egan describes the Ndoli Dual, a fictional brain implant which constantly monitors the host's neural activity in an attempt to learn how it unfolds. After several years of collecting data, the Ndoli Dual becomes powerful enough to accurately forecast the neural activity of its host, prompting many to *switch* to the Dual completely, outsourcing their entire thought process and achieving immortality. Besides describing a thought experiment which puts the Chinese room to shame in terms of vividness, Greg Egan hints at an intriguing possibility -- using a proxy for human thought as an optimization target for creating human-like artificial intelligence. An elegant formalism for *thinking humanly*, as per Russell and Norvig's taxonomy.

{: .quote }
"If the human race *was* replacing itself with clockwork automata, I was better off dead; I lacked the blind conviction to join the psychotic underground -- who, in any case, were tolerated by the authorities only so long as they remained ineffectual. On the other hand, if all my fears were unfounded -- if my sense of identity could survive the switch as easily as it had already survived such traumas as sleeping and waking, the constant death of brain cells, growth, experience, learning and forgetting -- then I would gain not only eternal life, but an end to my doubts and my alienation." -- Greg Egan

However, even if neural activity seems to be the most accurate proxy for thought, high-resolution brain-computer interfaces are a long way from being commercially viable. We need a proxy for thought which is cheap and abundant, so that our models have plenty of data to learn from. What we need is written language, the next best thing after neural activity in terms of capturing human thought processes. Infinitely expressive and highly economic, written language has been the preferred medium for capturing thoughts for millennia. Today, internet archives contain billions of them, from the most brilliant to the darkest.

{: .quote }
"You, I hope, are one of those explorers. You, I hope, found these sheets of copper and deciphered the words engraved on their surfaces. And whether or not your brain is impelled by the air that once impelled mine, through the act of reading my words, the patterns that form your thoughts become an imitation of the patterns that once formed mine. And in that way I live again, through you." -- Ted Chiang

This abundance, naturally, powered recent advances in natural language processing. That said, language models typically reflect the aggregate thought patterns of millions of people who have contributed data to the training set, whether willingly or not. However, disciplined note-taking practices such as the second brain and digital gardening enable the fine-tuning of generic language models to the specific way of thinking of an individual. By using hundreds of written notes as training data, we can configure a model to *learn to be the note-taker*, to internalize their thought patterns, to adopt their writing style and interests, to approximate their mannerisms and responses. After several months of disciplined note-taking, the aligned model becomes powerful enough to accurately extrapolate the written thoughts of its user, enabling transformative new ways of conducting knowledge work and an early glimpse into immortality.

We'll now explore the inner workings of Dual, the piece of software which learns to be its user, named so as a tribute to Greg Egan. However, before doing that, we'll consider some useful framings for better understanding what Dual is and what it is for.

## Paradigms

### Your Dual is your second brain come to life

The ideas, concepts, and insights which you include in your second brain make up your Dual's long-term memory in a manner reminiscent of the spreading activation model. Relevant pieces of knowledge are strategically remembered behind the scenes when your Dual is considering your queries, populating its working memory in a context-dependent manner. When finally engaging in a reply to your messages, the items stored in working memory are used in tandem with the previously fine-tuned language model to generate a response. The result is an expressive chatbot which seemlessly integrates disparate fragments of your knowledge into its replies.

{: .quote }
"And if one has to write anyway, it is useful to take advantage of this activity in order to create in the system of notes a competent partner of communication." -- Niklas Luhmann

### Your Dual is a virtual assistant for reasoning

Your Dual can't make changes to your notes directly, it can only read from them when interacting with you. And that's not a bug, it's a feature. Your Dual is designed to *assist* you in knowledge work, rather than to do it for you. You still have to do the hard work of creating, linking, and updating notes. Why? Not because of technical obstacles, but rather because putting in this effort is helpful. It fosters understanding and retention on a deeper level. Your Dual is there to amplify your capabilities through collaboration, not to replace you.

{: .quote }
"The best interface to my brain is a relationship. That's how merging feels like. That's how I envision it." -- George Hotz

### Your Dual is the librarian of your thoughts

Your Dual is very apt at searching for items in your knowledge base, just like a librarian knows their way around bookshelves. Ask it for notes which describe metaphors of the mind, and you'll get a list of candidates in seconds, even if part of the search results were written years ago. Ask it for entries which provide arguments supporting the feasibility of mind upload, and it will readily point you towards the (numerous) relevant items.


## Architecture

## Features

## Workflows

## Future Steps

## References