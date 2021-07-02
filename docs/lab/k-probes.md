---
layout: default
title: K-Probes
nav_order: 4
parent: Lab
description: "Promoting critical thinking through prompt generation."
---

# Knowledge Probes
{: .no_toc }

Promoting critical thinking through prompt generation.
{: .fs-6 .fw-300 .text-left .mb-0 }

By Paul Bricman
{: .mt-1 }

[View Code](https://github.com/Psionica/K-Probes){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [View Spec](https://github.com/Psionica/psionica.github.io/issues/5){: .btn .fs-5 .mb-4 .mb-md-0 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## The Curious Child

Take a moment to picture the following prototypical narrative. "Why is the sky blue?" the curious child asks. "Well, sunlight passes through the atmosphere before it gets here, which makes the sky appear blue," answers the parent. At this point, both parties seem content with the exchange. Several moments later, the inevitable happens. "But why?" the child asks. Somewhat frustrated, the parent conveniently wraps up the conversation: "Because I said so."

There are a couple of remarkable things to note about this narrative. First, the child manages to challenge the knowledge of the adult *without* possessing that knowledge herself. This is quite different from the situation in which a teacher is challenging the knowledge of a student. In this more formal setting, the teacher is very much aware of the established body of knowledge. In contrast, the very premise of the opening story is based on the ignorance of the curious child. It appears that we have a deeply-rooted drive to answer questions, which often requires us to draw on our *own* knowledge. This innate tendency is called instinctive elaboration, and it enables questions to force your brain into a relentless search for answers.[^1]

The second remarkable thing to note about this narrative is the simple nature of the questions. They are far from being elaborate descriptions of the requested information. Even a simple "Why?" would suffice in challenging the adult. Despite their minimal contents, the replies are effortlessly understood. The reason for that is that they are genuinely *soaked* in context, following the unwritten rules of pragmatics.[^2] The ongoing dialogue infuses each reply with meaning, enabling speakers to cut down on words without sacrificing the contents. This state of affairs makes it surprisingly easy to play the challenger, as many parents may be particularly aware of.

---

## The Curious Machine

Given how effective the child is in challenging the parent's knowledge, could we promote critical thinking by embedding her behavior into a tool for thought? Could we incentivize people to actively reflect on their own beliefs by allowing them to converse with a "curious" machine? Even if the user wouldn't actually receive new information in the exchange, the very act of highlighting gaps in their knowledge might be valuable. Such a tool could be used to challenge faulty beliefs, incentivize deeper understanding, and make assumptions salient.

Those objectives are key to changing our relationship with hard questions into a healthier one. Annoying inquiries turn into opportunities for growth. This paradigm shift is fittingly captured by the concept of aporia.

{: .quote }
"Aporia is the feeling of realizing that what you thought was a path to truth actually doesn't lead there at all. A shortcut to certainty has revealed itself to be an illusion. The first reaction to aporia might be frustration and even anger, but if you consider that it's providing new information and could be saving you from wasting additional effort maintaining false certainty about an existing belief, it can flip into an Aha! moment that is even enjoyable." -- Buster Benson[^3]

---

## Design

After changing our perspective on hard questions, we can finally start building. Being inspired by the unreasonable effectiveness of the curious child, this tool will consist of nothing more than a set of questions and a basic method for sampling them. Difficult questions. Vague, muddy, demanding questions. Questions which genuinely get the person thinking. Revising, reframing, reviewing what they hold to be true. Questions which probe the otherwise obstructed depths of knowledge. Given their current purpose, we'll also refer to these questions as knowledge probes, or k-probes for short.

To integrate a minimal level of structure into the question set, we'll use Bloom's revised taxonomy as a starting point.[^4] This taxonomy is a widely used system for organizing learning outcomes across all levels of formal education, from kindergarten to university. These outcomes essentially capture the abilities which students are expected to possess by the end of a lesson, course, or programme. Formal education can be seen in part as a process of internalizing these abilities.

The taxonomy consists of six broad categories, exemplified below with intended learning outcomes from the degree I'm currently pursuing. 

1. **Remember** -- Retrieve relevant knowledge.
- Recall the high-level anatomy of the brain.
- Recognize questionable research practices.
- Know how to create reproducible workflows.
2. **Understand** -- Construct meaning.
- Explain the principles behind the general linear model.
- Describe algorithms used for adversarial search.
- Summarize the main approaches to speech synthesis.
3. **Apply** -- Use knowledge in new situations.
- Carry out a multivariate statistical analysis.
- Implement a genetic algorithm.
- Solve homogeneous differential equations.
4. **Analyze** -- Determine how parts relate to a structure.
- Investigate the relationship between syntax and semantics.
- Analyze the interaction between various forms of memory.
- Determine the relationship between subfields of cognitive science.
5. **Evaluate** -- Make informed judgements.
- Interpret the results of brain data analyses.
- Determine the complexity of simple algorithms.
- Evaluate set-theoretic statements.
6. **Create** -- Reorganize elements into a structure.
- Construct formal proofs for first-order logic.
- Design a user interface based on cognitive ergonomics.
- Develop models in a cognitive architecture.

Due to the popularity of Bloom's revised taxonomy, there are a lot of online resources containing examples of learning outcomes, complete with suggestions for classroom activities. After compiling examples from several such resources and rephrasing them as questions, I used a text generation service to extend the question set even further.[^5] Following several hours of co-creating questions with the machine, the total number of knowledge probes surpassed two hundred, a sample of which can be found below.

1. **Remember** -- Retrieve relevant knowledge.
- What are the basic facts of this?
- What puzzle is this part of?
- How would you characterize this?
2. **Understand** -- Construct meaning.
- How would you explain this to a peer?
- What would be an analogy for this?
- How would you represent this visually?
3. **Apply** -- Use knowledge in new situations.
- How can this be helpful?
- Who can benefit from this?
- How could this be applied to other domains?
4. **Analyze** -- Determine how parts relate to a structure.
- What's the structure of this?
- How do the components of this relate to each other?
- How can this be viewed as a system?
5. **Evaluate** -- Make informed judgements.
- What assumptions underlie this?
- What evidence supports this?
- How would different people view this?
6. **Create** -- Reorganize elements into a structure.
- How can this be expanded?
- How does this fit into a narrative?
- How would you design something based on this?

As in the case of the curious child, the value lies in the dialogue itself, rather than in the questions. Therefore, we need a method of stitching together questions with user replies, fostering an ongoing discussion. Fortunately, this method can be as simple as a chat-like textual interface which alternates between printing output questions and reading input replies. The unwritten rules of pragmatics will do the rest, helping the user instinctively turn the sequence of questions and replies into a meaningful dialogue by filling in the gaps.

As a final layer of complexity, we'll also use Bloom's revised taxonomy as a basis for a more customizable experience. By specifying a numeric weight for each of the six categories, the user can adjust the probabilities of certain questions being asked. Larger weights will result in more questions being sampled from that category, relative to others. This way, the user can better tailor the tool to their current needs. Or, perhaps, to their intended "learning outcomes."

---

## Dialogue Sample

The following is a short excerpt discussing the technology behind [Semantica](https://paulbricman.com/docs/tools/semantica/#semantic-embeddings):

*Let's talk about semantic embeddings.*

- **What field is this part of?**

*Computational semantics or natural language processing, depending on who you ask.*

- **What is this a consequence of?**

*They're the result of exploiting word co-occurence information derived from large corpora.*

- **How would you explain this to a teenager?**

*Imagine you're planning on traveling to a foreign country. The catch is, there's no map available! You see, it's quite an obscure country, perfect for a curious teen. The only thing available is a list of past itineraries -- lists of cities which other travelers have visited before, in order. The interesting thing is that you can use those itineraries to sketch a map! Cities visited one after another should be near each other, right? You could try to come up with a map which matches the distance relations derived from the itineraries, and you'll get a pretty accurate map you can use on your journey. In essence, language is like a set of itineraries, called sentences. However, instead of cities, it's got words! I just took you along a journey through the country of language, traveling from one word to the next. It turns out that if you try to use the same reasoning here, you can actually pinpoint words on a map, based solely on a lot of text. Not a map of cities, mountains, and rivers, but a map of meaning. Semantic embeddings are the "geographical" coordinates of words in this country of language.*

- **What issues can this help with?**

*They can help machines extract meaning from otherwise plain text.*

- **What other concepts are related to this?**

*Text mining, natural language processing, vector semantics, lexical semantics.*

- **How can this be a source for inspiration?**

*If words can be represented as points in a space, what else could be represented this way? The effectiveness of semantic embeddings gets you thinking about what other things can be expressed like this.*

- **Why is this relevant?**

*It's the most popular approach to extracting meaning from text. It drives most, if not all, of modern natural language processing efforts.*

- **How do the components of this relate to each other?**

*Each word is associated with a vector. All vectors inhabit the same space. There's a relation between any two words, represented through the difference between their vectors.*

- **What has to be in place before this can be applied?**

*A lot of text for obtaining the embeddings, and a broader understanding of semantic embeddings in academia and industry.*

- **What can this lead to?**

*Machines which can reason about relatable concepts. Tools for thought as well.*

---

## Random Sample

Use the following button to randomly sample one probe from the collection.

<button class="btn btn-primary" onclick="newProbe()">New Probe</button>
<div id="probeDisplay"></div>
<script src="../../../assets/js/k-probes.js"></script>

---

## Final Thoughts

The simple nature of this tool might be deceiving. Its beauty lies not in its codebase, but in the way it builds on quirks of the human mind. Pragmatics helps with coherence. Instinctive elaboration triggers an automatic drive for engaging with the knowledge probes. The conversational medium even makes the experience feel social.

Despite the potential benefits of this approach, it's also worth considering its downsides. The main disadvantage is the lack of rich feedback, which has otherwise been shown to be very effective in learning.[^6] However, one could argue that the increased ease of adapting the tool to new fields outweighs this shortcoming. Moreover, the self-supervised nature of this approach might still provide a feedback signal which is strong enough to be useful.

We have a unique relationship with questions, so why not leverage that to our advantage? Knowledge probes are an early attempt of explicitly doing just that. I'll predictably end with an open-ended question: "How can knowledge probes be helpful for you?"

---

## Acknowledgements

Our work is supported by awesome sponsors:
- [Andreas Stuhlmüller](https://stuhlmueller.org/)
- [David Dohan](https://twitter.com/dmdohan)
- [Serj Hunt](https://twitter.com/Serjhunt_ARK)
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

[^1]: David Hoffeld,<br/>[Want To Know What Your Brain Does When It Hears A Question?](https://www.fastcompany.com/3068341/want-to-know-what-your-brain-does-when-it-hears-a-question)
[^2]: Richard Nordquist,<br/>[The Cooperative Principle in Conversation](https://www.thoughtco.com/cooperative-principle-conversation-1689928)
[^3]: Buster Benson,<br/>[Why Are We Yelling?](https://busterbenson.com/whyareweyelling/)
[^4]: CELT,<br/>[Revised Bloom's Taxonomy](https://www.celt.iastate.edu/teaching/effective-teaching-practices/revised-blooms-taxonomy/)
[^5]: Hugging Face,<br/>[Write With Transformer](https://transformer.huggingface.co/)
[^6]: John Hattie & Helen Timperley,<br/>[The Power of Feedback](http://mrbartonmaths.com/resourcesnew/8.%20Research/Marking%20and%20Feedback/The%20Power%20of%20Feedback.pdf)