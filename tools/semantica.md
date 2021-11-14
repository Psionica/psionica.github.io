---
layout: default
title: Semantica
nav_order: 6
parent: Tools
description: "Extending conceptual thinking through semantic embeddings."
redirect_to: https://paulbricman.com/thoughtware/semantica
---

{: .info }
This project is currently on standby. Reach out to its previous contributor(s) on [Discord](/community/#members) for guidance in advancing it to the [next stage](/community/#process).

# Semantica
{: .d-inline-block .mt-0 .no_toc }

STAGE 2
{: .label }

Extending conceptual thinking through semantic embeddings.
{: .fs-6 .fw-300 .text-left .mb-0 .mt-0 }

By [@thoughtware.engineer](https://paulbricman.com/)
{: .mt-0 }

[Open Demo](https://colab.research.google.com/drive/1NCPktYHVYvD03DRMevbhb51_yjnO4aTa?usp=sharing){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [View Code](https://github.com/Psionica/Semantica){: .btn .fs-5 .mb-4 .mb-md-0 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Mental Models

Mental models are simplified descriptions of the world around us. For instance, one of them might describe networks. A forest is a network of trees. A society is a network of people. A brain is a network of neurons. Mental models help us make sense of the world by allowing us to apply previous knowledge to new situations. They are widely seen as powerful tools for thought, especially when they come in large numbers. If one's repository of mental models is vast, then they'll be able to approach new situations from many different perspectives. This is the motivation behind many recent efforts of compiling extensive lists of them.[^1]

{: .quote }
"Our systematic cross-realm translations are the roots of fruitful metaphors; they enable us to understand things we've never seen before. When something seems entirely new in one of our description-worlds, it may turn out that when translated to some other world it resembles something we already know." -- Marvin Minsky[^2]

{: .quote }
"Metaphors allow us to understand one domain of experience in terms of another. This suggests that understanding takes place in terms of entire domains of experience and not in terms of isolated concepts." -- George Lakoff & Mark Johnson[^11]

## Conceptual Thinking

However, mental models are only one side of what can be more broadly described as conceptual thinking. In this view, mental models are just sets of systematic relations between concepts. The previous network model merely captures the relation between a forest and a tree, between a society and a person, and between a brain and a neuron. Having said that, there is so much more to concepts than mental models. You can connect them to similar ones. You can mix them together into new ones. You can transform them in meaningful ways. You can explore the nuances between them.

What if we could build tools which enabled us to work with concepts in a similar way Photoshop enables us to work with images? What if we could build tools which extend our conceptual thinking beyond what is humanly possible? Instead of blending colors, we would combine concepts. Instead of creating gradients, we would explore continua of meaning. Instead of defining intricate visual patterns, we would define systematic patterns of meaning.

{: .quote }
"In this it resembles a program such as Photoshop or a spreadsheet or 3D graphics programs. Each provides a novel set of interface primitives, primitives which can be internalized by the user as fundamental new elements in their thinking." -- Shan Carter & Michael Nielsen[^3]

{: .quote }
"Human intellectual effectiveness can be affected by the particular means used by individuals for their external symbol manipulation. It seems reasonable to consider the development of automated external symbol manipulation means as a next stage in the evolution of our intellectual power." -- Douglas Engelbart[^12]

## Semantic Embeddings

However, tools like Photoshop don't directly work with colors, gradients, or patterns. At the lowest level, editing photos boils down to manipulating matrices of numbers. In order to build powerful tools for conceptual thinking, we might need an analogous way to fix concepts into firm numerical foundations which we could then easily manipulate.

Fortunately, there already are ways of doing that. The field of natural language processing has long used semantic embeddings as the numerical substrate of discrete concepts.[^4] Among others, they're used in search engines to understand queries, in chatbots to understand conversations, and in translation systems to understand foreign languages. Think of semantic embeddings as numeric coordinates. They don't describe locations in a physical space, like geographic coordinates, but locations in a space of meanings, a semantic space.[^5]

An intuitive understanding of how semantic embeddings are obtained is beyond the scope of this article, but what is relevant for our current purposes can be captured in a few neat properties exhibited by the semantic space:

1. Conceptual differences correspond to geometric distances.
2. Conceptual parallelism corresponds to geometric parallelism.

But analytic geometry is no reason for despair, because as graphic designers don't need to be knowledgeable about convolutions and tensors when using Photoshop, the tools for thought which we set out to build will be usable regardless of the user's proficiency in maths. We'll use semantic embeddings only as a low-level foundation for higher-level tools which enable anyone to work with concepts in exciting ways.

That's where we'll go next. In the following sections, we'll define and use new tools for thought built on top of semantic embeddings, and in doing so incrementally grow Semantica, a veritable computational toolkit for conceptual thinking.

{: .quote }
"But let the human specify to the instrument his particular conceptual need of the moment, relative to this internal image. Without disrupting its own internal reference structure in the slightest, the computer will effectively stretch, bend, fold, extract, and cut as it may need in order to assemble an internal substructure [...] it portrays to the human via its display a symbol structure designed for his quick and accurate perception and comprehension of the conceptual matter [...]" -- Douglas Engelbart[^12]

---

## Tools
### Field
#### Functional Description
{: .no_toc }
Finds concepts which are closely related to a given concept.

#### Spatial Intuition
{: .no_toc }
Finds concepts which are close to a given concept.

#### Numerical Implementation
{: .no_toc }
Finds concepts whose embeddings are the most similar to the embedding of a given concept.

{: .code-block }
```
>>> field('car')
['vehicle', 'cars', 'suv', 'minivan', 'truck', 'ford_focus', 'honda_civic', 'jeep']

>>> field('galaxy')
['galaxies', 'milky_way', 'planets', 'supernova', 'galactic', 'universe', 'comet', 'planet', 'cosmos']

>>> field('bed')
['beds', 'couch', 'sofa', 'sleep', 'duvet', 'sleeping', 'bunk', 'pillow', 'mattress']
```

{: .info }
A semantic field is a set of words related in meaning. This tool can be used to expand concepts into their semantic fields.

---

### Mix
#### Functional Description
{: .no_toc }
Blends given concepts into new ones.

#### Spatial Intuition
{: .no_toc }
Finds concepts which are close to the center of the given concepts.

#### Numerical Implementation
{: .no_toc }
Finds concepts whose embeddings are the most similar to the average embedding of the given concepts.

{: .code-block }
```
>>> mix('people', 'chaos')
['anarchy', 'mayhem', 'chaotic', 'civil_strife', 'bedlam', 'strife', 'bloodshed', 'upheaval']

>>> mix('computer', 'virus')
['viruses', 'computers', 'antivirus_software', 'malware', 'spyware', 'worm', 'antivirus']

>>> mix('brain', 'science')
['neuroscience', 'brains', 'biology', 'physiology', 'cognition', 'mathematics', 'neural', 'cognitive']
```

{: .info }
Conceptual blending has been described as the process of partially projecting multiple concepts onto a blended mental space.[^6] If this explanation seems largely circular, that's because it is. Still, this tool can be used to perform this ill-defined but intuitive task.

---

### Span
#### Functional Description
{: .no_toc }
Finds a sequence of concepts which spans the continuum between two given concepts.

#### Spatial Intuition
{: .no_toc }
Finds concepts located along the line between two given concepts.

#### Numerical Implementation
{: .no_toc }
Finds concepts whose embeddings are the most similar to the interpolated embeddings of two given concepts.

{: .code-block }
```
>>> span('pond', 'ocean')
['pond', 'ponds', 'retention_pond', 'drainage_ditch', 'creek', 'creek_bed', 'lake', 'river', 'lagoon', 'marsh', 'sea', 'ocean']

>>> span('city', 'house')
['city', 'mayor', 'municipality', 'municipal', 'district', 'downtown', 'town', 'neighborhoods', 'neighborhood', 'houses', 'house']

>>> span('kindergarten', 'university')
['kindergarten', 'kindergartners', 'preschool', 'sixth_graders', 'eighth_grade', 'elementary', 'school', 'students', 'university']
```

{: .info }
The selected samples are massively cherry-picked. However, in the envisioned use cases of this toolkit, there's always a human-in-the-loop who is able to sift through some moderate amounts of noise.

---

### Shift
#### Functional Description
{: .no_toc }
Captures the relation between two given concepts.

#### Spatial Intuition
{: .no_toc }
Determines the directed difference in location between two given concepts.

#### Numerical Implementation
{: .no_toc }
Computes the arithmetic difference between the embeddings of two given concepts.

{: .code-block }
```
>>> mix('cell', shift('biology', 'physics'))
['atoms', 'electron', 'electrons', 'photons', 'neutrons', 'particle', 'photon', 'physics']

>>> mix('saxophone', shift('jazz', 'rock'))
['rock', 'guitar', 'bass_guitar', 'guitars', 'electric_guitar', 'rocks', 'guitar_riffs', 'trombone', 'guitarist']

>>> mix('burrito', shift('Spain', 'Italy'))
['pizza', 'burger', 'sandwich', 'pasta', 'pizzas', 'cheeseburger', 'pizzeria', 'hamburger', 'sushi']
```

{: .info }
*Metaphor* comes from the Latin *metaphora*, meaning *to carry over*. This tool can be used to *carry over* concepts from one domain to another.

---

### Match
#### Functional Description
{: .no_toc }
Finds sets of concepts whose elements match the relations found in a given set of concepts.

#### Spatial Intuition
{: .no_toc }
Finds constellations of concepts which match the shape of a given constellation of concepts.

#### Numerical Implementation
{: .no_toc }
Finds sets of concepts whose internal differences in embeddings are the most similar to the ones found in a given set of concepts.

{: .code-block }
```
>>> match('people', 'society')
['members', 'membership']
['players', 'team']
['students', 'classroom']
['women', 'womanhood']
['customers', 'clientele']
['workers', 'workforce']
['fans', 'fandom']
...

>>> match('physics', 'Einstein', target='science')
['biology', 'charles_darwin']
['psychology', 'freud']
['linguistics', 'chomsky']
['philosophy', 'nietzsche']
['astrophysics', 'stephen_hawking']
...

>>> match('king', 'queen', target='acting')
['actor', 'actress']
['al_pacino', 'meryl_streep']
['cocky', 'bitchy']
['best_actor', 'best_actress']
['showman', 'diva']
...
```

{: .info }
Inspiration for this tool comes from a science fiction novel in which the main character needs to broadcast the location of a celestial body to an unknown civilization.[^7] However, given the lack of absolute reference frames available, he broadcasts the position of the celestial body relative to several neighboring ones. Here, because the dimensions of the semantic space aren't inherently meaningful, a mental model is expressed as a set of distances from the first concept to each subsequent concept, forming a *constellation* of concepts. The Golden Records use a similar scheme to pinpoint the Earth.[^8] After finishing this write-up, I also came across this eerily related passage:

{: .quote }
"The night sky is a partial representation of Prime Intellect's mind. It's called the Global Association Table. The points or stars represent concepts, and the lines are the links between them." -- Roger Williams[^13]

---

## Case Studies
### Physicist & Biologist
{: .no_toc }
"My research group and I have been exploring potential applications of graphene for several years now. It's a really fascinating material," says the physicist. "You know, graphene is like...

{: .code-block}
```
>>> mix('graphene', shift('physics', 'biology'))
[... 'tissue' ...]
```

...tissue. Graphene is like a tissue of carbon atoms, in a similar way in which biological tissue is composed of a latticework of interconnected cells. It turns out to be quite resistant, yet flexible."

### Artist & Scientist
{: .no_toc }
"We see ourselves as living in two radically different worlds, but there's a seamless transition between them," says the artist. "Consider interdisciplinary fields such as...

{: .code-block}
```
>>> span('art', 'science')
[... 'humanities', 'museology' ...]
```

humanities or museology. We can meet each other halfway through."

### Sociologist & Students
{: .no_toc }
"Think of a society as a...

{: .code-block}
```
>>> match('people', 'society', target='student')
['students', 'clasroom']
...
```

...classroom, composed of many independent students who all have their own individual beliefs, desires, and intentions."

---

## Further Steps
### Friendlier interfaces
{: .no_toc}
From Photoshop-like stand-alones to Wolfram-like web apps, there are exciting ways of wrapping interfaces around these conceptual tools.

### Better tools
{: .no_toc}
This early selection of tools merely scratches surface of how semantic embeddings can be used in building tools for thought. A largely unexplored space of possibilities is waiting for curious thinkers.

### Deeper integration
{: .no_toc}
This toolkit only operates with knowledge on a conceptual level. In the future, it might be able to interface with definitions (e.g. from WordNet), multimedia content (e.g. from ImageNet), external resources (e.g. via Zotero), or more established tools for thought (e.g. Zettelkasten).

### Higher performance
{: .no_toc}
The current software implementation has been developed for experimental purposes, rather than efficiency. Much needed code optimizations will significantly improve the speed of the algorithms involved.

### Better embeddings
{: .no_toc}
Not all semantic embeddings are created equal. The ones used in this prototype have been obtained through a relatively rudimentary approach. Newer techniques capture meaning more effectively and with less bias.[^5]

---

## Contributions

1. The idea that semantic embeddings -- specifically word embeddings -- can be directly used to build tools for thought, rather than only as raw ingredients in downstream machine learning tasks. Earlier work explored the potential of interacting with abstract representations more generally.[^3]

2. The idea that mental models can be formalized as constellations of semantic embeddings in semantic space.

3. The formalization and implementation of Span and Match. The other conceptual tools (i.e. Field, Mix, Shift) were already formalized and implemented in earlier work, one way or another. For example, Mix is based on additive composition of semantic embeddings.[^9] However, these operations were largely used to measure the quality of semantic embeddings for downstream tasks, rather than as first-hand tools.

4. The strengthened link between Photoshop and more radical tools for thought, through Photoshop-like names and descriptions. Photoshop has been extensively used as a prime example of tools for thought before, but the current work explores new ways of reinforcing this connection.

5. The name Semantica for a tool for conceptual thinking has been inspired by the name Mathematica, used to describe a tool for computational thinking.[^10]

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
[^1]: Farnam Street,<br/>[Mental Models](https://fs.blog/mental-models/)
[^2]: Marvin Minsky,<br/>[The Society of Mind](https://www.goodreads.com/book/show/326790.The_Society_of_Mind)
[^3]: Shan Carter & Michael Nielsen,<br/>[Using Artificial Intelligence to Augment Human Intelligence](https://distill.pub/2017/aia/)
[^4]: Christopher Olah,<br/>[Deep Learning, NLP, and Representations](https://colah.github.io/posts/2014-07-NLP-RNNs-Representations/)
[^5]: Daniel Jurafsky & James Martin,<br/>[Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/6.pdf)
[^6]: Gilles Fauconnier,<br/>[The Encyclopedia of the Social and Behavioral Sciences](http://www.cogsci.ucsd.edu/~faucon/BEIJING/blending.pdf)
[^7]: Cixin Liu,<br/>[The Three-Body Problem Trilogy](https://www.goodreads.com/book/show/34569357-remembrance-of-earth-s-past?ac=1&from_search=true&qid=5NN7oSm54Y&rank=2)
[^8]: NASA,<br/>[The Golden Record Cover](https://voyager.jpl.nasa.gov/golden-record/golden-record-cover/)
[^9]: Mikolov et al.,<br/>[Distributed Representations of Words and Phrases and their Compositionality](https://papers.nips.cc/paper/2013/file/9aa42b31882ec039965f3c4923ce901b-Paper.pdf)
[^10]: Stephen Wolfram,<br/>[Computational Universe](https://www.youtube.com/watch?v=P7kX7BuHSFI)
[^11]: George Lakoff & Mark Johnson,<br/>[Metaphors We Live By](https://www.goodreads.com/book/show/34459.Metaphors_We_Live_By)
[^12]: Douglas Engelbart,<br/>[Augmenting Human Intellect](https://www.goodreads.com/book/show/13365811-augmenting-human-intellect)
[^13]: Roger Williams,<br/>[The Metamorphosis of Prime Intellect](https://www.goodreads.com/book/show/64341.The_Metamorphosis_of_Prime_Intellect)