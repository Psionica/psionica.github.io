---
layout: default
title: Autocards
nav_order: 1
parent: Lab
description: "Accelerating learning through machine-generated flashcards."
published: True
---

# Autocards
{: .no_toc }

Accelerating learning through machine-generated flashcards.
{: .fs-6 .fw-300 .text-left .mb-0 }

By Paul Bricman
{: .mt-1 }

[View Code](https://github.com/Psionica/Autocards){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [Open Demo](https://colab.research.google.com/drive/1Z6D8ncYiavbrc72-Hc84M3qFVgWnQnNx?usp=sharing){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [View Spec](https://github.com/Psionica/psionica.github.io/issues/6){: .btn .fs-5 .mb-4 .mb-md-0 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Empowering Creators

Not all educational resources are created equal. Imagine you're trying to grasp the essence of quaternions, a somewhat esoteric mathematical construct. One way to go about it might be to painstakingly read through an old textbook chapter on the topic, full of intimidating terminology and verbose notation.[^1] You might end up giving it a few solid reads, as building mental models from scratch is quite tedious. Now, picture yourself experimenting with an interactive animation on the same topic. You can now freely manipulate quaternions from the comfort of your desk while getting instant feedback across several parallel representations. Meanwhile, you're being guided through the material in an accessible way, while systematically internalizing core concepts.[^2]

A broad range of methods have been developed through the years to guide the creation of engaging, insightful, and memorable educational resources. However, guidelines only go so far, and developers started building concrete tools to help creators in their process. For instance, one project aims to help authors make their online articles more memorable by easily embedding a custom spaced repetition system into the actual web page.[^3] Flashcards are knitted together with text and figures, making them an integral part of the article. This tool essentially turns otherwise static online essays into engaging and memorable artifacts. Yet other tools help creators bring abstract concepts to life through programmatically-generated videos and interactive animations. [^4] [^5]

## Empowering Audiences

However, few creators possess the skill, interest, and know-how required to create such cognitively ergonomic content. There is indeed a growing collection of pixel-perfect explorable explanations and engaging learning experiences, but they pale in comparison to the rate at which mediocre static content is being published.[^6] It's difficult enough for creators of educational resources to convey knowledge accurately and accessibly in the first place, and even more so with the additional hurdle introduced by complex creator-side tools.

What if instead of focusing on building tools for creators, we focused on building tools for *audiences* to systematically get the best out of existing content? Building the shovels and pickaxes required to mine for educational gems, rather than investing in the alchemy of crafting the gems themselves. Think about how a committed student can easily turn a static lecture into flashcards, mind-maps, or sketchnotes in order to get the best out of the material. Could learner-side tools and practices radically extend beyond that with the help of technologies like AI? What if we could automatically turn the mountains of resources available in unfriendly formats into something more memorable, humane, and ergonomic? We'll attempt to answer this exact question with a working prototype.

---

## Design

The most prevalent format employed by educational resources today is written text. Articles, essays, books, textbooks, and papers are all variations on the same tried and trusted way of conveying knowledge -- writing. It only makes sense to focus our efforts on this particularly pervasive medium. Fortunately, text is also quite a machine-friendly format, as we've seen with [MemNav](/docs/tools/memnav). To explore the potential of AI in learner-side tools, we'll attempt to use natural language processing to make text-based resources more brain-friendly.

One especially popular way of making static text more cognitively ergonomic is to turn it into flashcards. Using flashcards for spaced repetition is standard practice for committed students across a wide range of disciplines, as it results in long-term information retention. It turns out that machines are surprisingly good at automatically creating flashcards from text-based content which is rich in information. By combining methods of question generation with methods of question answering, several language models can be configured to work in parallel, forming a system capable of generating flashcards based on arbitrary text. The task of answer-aware question generation, or what we'll call flashcard generation, is based on the following steps being performed automatically by the system:

1. Extract tentative answers for subsequently-generated questions. Those can be specific terms, entities, or short phrases which are likely to make good answers (e.g. "the junction rule").
2. Based on the previously-extracted answers and the original text, try to generate related questions, as if playing Jeopardy (e.g. "What is another name for Kirchhoff’s current law?").
3. Close the loop by checking whether the previously-generated questions actually match the previously-extracted answers using question answering.

Equipped with this approach, we can start building Autocards, a flashcard generator based on existing open source tools. This time, we're forking an excellent pipeline designed specifically for question generation.[^7] By encapsulating its functionality in a Python class capable of consuming various types of text (i.e. plain text, text files, PDF's) we're laying the groundwork for a large number of possible workflows.

{: .code-block }
```
>>> from autocards import Autocards
>>> a = Autocards()
>>> a.consume_text('King Philip’s ultimate goal was to conquer Persia.')
```

The resulting Python object can then be used to export flashcards derived from text as a CSV file which can later be imported in a wide range of spaced repetition apps. It provides a few handy options, such as adding a prefix to the front side of the flashcard and switching the questions up with the answers for a Jeopardy-style experience.[^22]

{: .code-block }
```
>>> a.export('history.csv', prefix='HELLENISTIC AGE:', jeopardy=False)
```

---

## Samples

To get a sense of the pipeline's performance, several samples from various disciplines are listed below. Each excerpt is followed by a set of automatically generated flashcards, pairs of questions and answers which have suffered no human modification whatsoever.

### Physics
{: .no_toc }

{: .quote .mt-4 }
"Kirchhoff’s junction rule says that the total current into a junction equals the total current out of the junction. This is a statement of conservation of charge. It is also sometimes called Kirchhoff’s first law, Kirchhoff’s current law, the junction rule, or the node rule. Junctions can’t store current, and current can’t just disappear into thin air because charge is conserved. Therefore, the total amount of current flowing through the circuit must be constant."

{: .text-left }
| Question | Answer |
|-|-|
| What does Kirchhoff's junction rule say? | the total current into a junction equals the total current out of the junction |
| What is Kirchhoff's junction rule a statement of? | conservation of charge |
| What is another name for Kirchhoff's current law? | the junction rule |
| Why can't current disappear into thin air? | charge is conserved |
| The total amount of current flowing through a circuit must be what? | constant |

### History
{: .no_toc }

{: .quote .mt-4 }
"King Philip’s ultimate goal was to conquer Persia and help himself to the empire’s land and riches. This was not to be; King Philip was assassinated by his bodyguard Pausanias in 336 B.C. at his daughter’s wedding, before he could enjoy the spoils of his victories. His son Alexander, known to history as "Alexander The Great," jumped at the chance to take over his father’s imperial project. The new Macedonian king led his troops across the Hellespont into Asia. (When he got there, he plunged an enormous sarissa into the ground and declared the land “spear won.”) From there, Alexander and his armies kept moving."

{: .text-left }
| Question | Answer |
|-|-|
| What was King Philip's ultimate goal? | conquer Persia |
| Who was King Philip's bodyguard? | Pausanias |
| Where was King Philip assassinated? | his daughter’s wedding |
| Who was King Philip's son? | Alexander |
| Alexander led his troops across the Hellespont into what continent? | Asia |
| What did Alexander plunge into the ground when he got to Asia? | sarissa |

### Biology
{: .no_toc }

{: .quote .mt-4 }
"DNA sequencing is a collection of scientific methods for determining the sequence of the nucleotide bases in a molecule of DNA. All living organisms have DNA (deoxyribonucleic acid) in each of their cells. Each cell in an organism contains the genetic code for the entire organism. The process of DNA sequencing transforms the DNA from a given organism into a format that can be used by researchers for the basic study of biologic processes, medical research, and in forensics."

{: .text-left }
| Question | Answer |
|-|-|
| What is a collection of scientific methods for determining the sequence of the nucleotide bases in a molecule of DNA? | DNA sequencing |
| What does DNA stand for? | deoxyribonucleic acid |
| What does each cell in an organism contain the genetic code for? | the entire organism |
| What is the use of DNA sequencing? | basic study of biologic processes, medical research, and in forensics |

### Architecture
{: .no_toc }

{: .quote .mt-4 }
"The Villa Savoye at Poissy, designed by Le Corbusier in 1929, represents the culmination of a decade during which the architect worked to articulate the essence of modern architecture. Throughout the 1920s, via his writings and designs, Le Corbusier (formerly Charles-Edouard Jeanneret) considered the nature of modern life and architecture’s role in the new machine age. His famous dictum, that “The house should be a machine for living in,” is perfectly realized within the forms, layout, materials, and siting of the Villa Savoye."

{: .text-left }
| Question | Answer |
|-|-|
| In what year was the Villa Savoye at Poissy designed? | 1929 |
| What was Le Corbusier's previous name? | Charles-Edouard Jeanneret |
| What was Le Corbusier's famous dictum? | The house should be a machine for living in |

### AI
{: .no_toc }

{: .quote .mt-4 }
"Generative adversarial networks consist of two networks, the generator and the discriminator, which compete against each other. The generator is trained to produce fake data, and the discriminator is trained to distinguish the generator’s fake data from real examples. If the generator produces fake data that the discriminator can easily recognize as implausible, such as an image that is clearly not a face, the generator is penalized. Over time, the generator learns to generate more plausible examples."

{: .text-left }
| Question | Answer |
|-|-|
| Who is trained to distinguish the generator's fake data from real examples? | the discriminator |
| What is the generator trained to produce? | fake data |
| What is an example of a implausible data that a discriminator can easily recognize? | an image that is clearly not a face |
| What does the generator learn to generate over time? | more plausible examples |

---

## Workflows

Individual samples are exciting, but it might be equally valuable to think through ways of integrating this experimental system into real workflows. A series of vignettes are provided below, each capturing the concrete routine of a hypothetical learner. This specific way of portraying otherwise exotic tools for thought was inspired by a seminal report on human augmentation.[^8]

### The Scholar

Alice is a researcher in machine learning. The rate of new breakthroughs in the field these days is astonishing, and makes it difficult for even the most committed scholars to keep up with the pace of progress.[^9] This is not the case for Alice, though. As part of her morning routine, she launches Zotero, her open source reference manager, in order to have a look at a research paper she saved last week.[^10] While trying to get a high-level view of the paper, she starts highlighting relevant text directly in the PDF file using her document viewer. After a couple of passes through the paper, she triggers the automatic extraction of highlighted text from the PDF using Zotfile, her PDF management tool.[^12] Several days later, she copies all her annotations from that week and pastes them in a console running Autocards. After using it to generate batched flashcards, she polishes the CSV file and imports it in Anki, her open source spaced repetition system.[^13]

{: .info }
One of the few estimates I found on how much time an experienced researcher spends on creating flashcards based on a paper is listed below. From early hands-on experience with Autocards, this can reliably be brought down to around 5 minutes, *after* first reading it.

{: .quote }
"I typically spend 10 to 60 minutes Ankifying a paper, with the duration depending on my judgment of the value I'm getting from the paper." -- Michael Nielsen[^21]

### The Bookworm

Bob is an avid reader. He's aiming for reaching the 50 books per year mark, while still remembering the important bits later on.[^14] As part of his evening routine, he turns on his reMarkable tablet, a maker-friendly e-reader, and opens a non-fiction book.[^15] As he gets immersed in it, he highlights all sorts of insights, nuggets, and gems which resonate with him. After finishing the book several days later, he runs it through Biff, a tiny utility for extracting highlights made on the reMarkable tablet.[^16] He then pipes the extracted annotations through Autocards, polishes some of the flashcards in the CSV, and imports the file in Anki. He's pretty sure he might have managed to implement the same workflow using the more popular Kindle e-reader, but he happens to be a big fan of the maker culture.[^17]

### The Student

Charlie is a motivated student. He almost likes experimenting with study techniques more than actual studying, but he tries to strike a healthy balance regarding that. Throughout the day, he takes part in several lectures, some of which are online. During those, he tries to take concise notes which clearly capture important aspects of the material, while retaining the big-picture view. In order not to get caught up in making his notes look exceedingly aesthetic, he resorts to simply typing them out in Markdown, a light-weight markup language, using VS Code, an open source text editor.[^18] [^19] After the lecture, he goes through a [k-probing](/docs/tools/k-probes) session in order to better weave together what he just learned with his previous knowledge. While he's busy reflecting on the material, Autocards is starting up and working through the notes, ultimately generating several dozen flashcards listed in a CSV, which Charlie polishes and imports in Anki.

{: .warn }
It's tempting to quickly jump to rote memorization before actually understanding the material, and even more so with automated flashcard generation. Autocards is best used in tandem with techniques which foster understanding, such as the Feynman Technique or Knowledge Probes, as exemplified by Charlie.

---

## Future Steps

One of the main areas of improvement going forward is the quality of the questions generated by the system. They often come across as clunky and overly verbose, which might prove inconvenient for many. Fortunately, recent years have seen a steady rise in the performance of language models, which might soon become able to generate more natural questions.[^20] In the meantime, fine-tuning larger models on the task might help, as the current implementation is limited to the T5-small and T5-base models.

Another clear area of improvement is a more user-friendly interface which would wrap around the core functionality. Unfortunately, the natural language processing component would translate to higher requirements for a client-side device, especially in terms of RAM and GPU. It might seem anticlimactic to heat up a GPU only to get a dozen lines of text in return, yet this is the price you currently have to pay for this sort of processing. Paid access to a hosted server might do, but it would be great to somehow make this powerful tool accessible.

Additionally, the range of possible inputs which could be fed into Autocards might be extended. Various operating modes might instruct the system to, say, automatically extract the abstract, introduction, and discussion sections from a research paper for later use in flashcard generation. It could be adapted to consume a web article based on its URL by scraping the content and using it as input, perhaps after first piping it through an extractive summarization model. Autocards might even prove useful for generating flashcards for educational videos, by stripping the captions and using those as a starting point, or after crudely applying a speech-to-text pass.

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

[^1]: John Voight,<br>[Quaternion Algebras](https://math.dartmouth.edu/~jvoight/quat-book.pdf)
[^2]: Grant Sanderson & Ben Eater,<br>[Visualizing Quaternions](https://eater.net/quaternions/video/intro)
[^3]: Andy Matuschak,<br>[Orbit](https://twitter.com/withorbit)
[^4]: Grant Sanderson,<br>[Manim](https://github.com/3b1b/manim)
[^5]: Mike Bostock,<br>[Data-Driven Documents](https://d3js.org/)
[^6]: Nicky Case,<br>[Explorable Explanations](https://explorabl.es/)
[^7]: Patil Suraj,<br>[Question Generation Using Transformers](https://github.com/patil-suraj/question_generation)
[^8]: Douglas Engelbart,<br>[Augmenting Human Intellect](https://www.goodreads.com/book/show/13365811-augmenting-human-intellect)
[^9]: arXiv,<br>[Past Week Machine Learning Submissions](https://arxiv.org/list/cs.LG/pastweek)
[^10]: Corporation for Digital Scholarship,<br>[Zotero](https://www.zotero.org/)
[^11]: KDE Apps,<br>[Okular](https://apps.kde.org/en/okular)
[^12]: ZotFile,<br>[Advanced PDF Management for Zotero](http://zotfile.com/)
[^13]: Anki,<br>[Homepage](https://apps.ankiweb.net/)
[^14]: Fast Company,<br>[Why You Should Read 50 Books This Year](https://www.fastcompany.com/3055608/why-you-should-read-50-books-this-year-and-how-to-do-it)
[^15]: reMarkable,<br>[reMarkable Tablet](https://remarkable.com/)
[^16]: soulisalmed,<br>[Biff](https://github.com/soulisalmed/biff)
[^17]: Heather Bloomer,<br>[How To View Kindle Highlights Online](https://www.techjunkie.com/view-kindle-highlights-online/)
[^18]: Matt Cone,<br>[Markdown Guide](https://www.markdownguide.org/)
[^19]: Microsoft,<br>[Visual Studio Code](https://github.com/Microsoft/vscode)
[^20]: Papers with Code,<br>[Language Modelling Performance over Time](https://paperswithcode.com/sota/language-modelling-on-penn-treebank-word)
[^21]: Michael Nielsen,<br>[Augmenting Long-Term Memory](http://augmentingcognition.com/ltm.html)
[^22]: Merv Griffin,<br>[Jeopardy!](https://en.wikipedia.org/wiki/Jeopardy!)