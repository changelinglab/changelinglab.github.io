---
layout: page
title: WugGPT
description: Evaluating the morphological capabilities of Large Language Models
img: /assets/img/luzern-bridge-proj.jpg
importance: 3
category: llm
related_publications: true
---

Various claims have been made about the linguistic capacities of large language models. Some have asserted that, as next token prediction models, they do not display human-like linguistic “competence.” Others have claimed that the language abilities of LLMs are practically identical to those of humans. One way of testing this is to perform “psycholinguistic” experiments on LLMs.

One of the most influential psycholinguistic experiments was the Wug Test, in which small children were asked to complete sentences that required applying a morphological operation to a nonce word (a make-up word). For example, children might be shown a picture of a bird-like creature and be told “this is a wug.” Then, being shown two of the creatures, they would be told, “now there are two of them. There are two....” English speaking children, even very small children, then continue, “wugs!” This test showed that small children are able to generalize morphological and phonological patterns to contexts where they have never seen them before.

Our research applies the same technique to language models, investigating the degree to which they can generalize morphology—whether inflection or derivation—to nonce words or, in other words, the degree to which LLMs have human-like morphological behavior.

The project, about testing the linguistics capabilities of large language models, has resulted in a couple of papers, with more to come:

- {% cite weissweiler2023counting %}
- {% cite mortensen-etal-2024-verbing %}

In particular, ongoing work compares human and LLM derivational morphology and finds that—like humans—LLMs use analogical relationships to derive words but—unlike humans—current LLMs rely on token frequencies rather than type frequencies of exemplars.