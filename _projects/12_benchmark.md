---
layout: page
title: FBCC Benchmark
description: Evaluating the ability of code language models to generalize and plan based on examples
img: /assets/img/luzern-bridge2-proj.jpg
importance: 2
category: llm
---

Introductory historical linguistics students are often asked to determine the relative chronology of sound changes—changes in pronunciation acting  like regular-expression replacements that apply across the whole vocabulary of the language. These sound changes can interact in found different ways that constrain their relative chronology:

- **Feeding:** Change A creates contexts were Change B can apply.
- **Bleeding:** Change A destroys context where Change B would otherwise apply.
- **Counter-feeding:** Change B would create contexts where Change A would apply if it occurred before Change A.
- **Counter-bleeding:** Change B would destroy contexts were Change A would apply if it occurred before Change A.

For example, in what is known as Grimm's law (which occurred in the history of Germanic), the change in which t become θ (a th sound) must have occurred before the change in which d become t. Otherwise, English two—which, in the shared ancestor of Indo-European languages like English, Greek, Latin, and Sanskrit, started with a d—would start with a θ just like three (which started with a t originally). We can say that these two changes are in a counter-feeding relationship can their ordering can be deduced from that fact.

LLMs like GPT-4 are very good at inducing single sound changes. Based on extensive preliminary work, they are reasonably poor at determining the relative chronologies of multiple rules (that is, at doing the very task introductory historical linguistics students are expected to do). The task, put simply, it to write a program, a composition of functions, that map from a set of input examples (ancestral forms of words) to the corresponding outputs (modern reflexes). This task requires to types of reasoning:

- Inductive generalization across sets of input-output pairs.
- Planning a trajectory through the space of generalizations (to discover the possible relative chronologies of generalizations).

We are developing a benchmark based on problems of this kind (both using string rewriting and image rewriting). This benchmark will differ from earlier coding by example (CbE) benchmark in that it allows for a tightly controlled evaluation of these two kinds of reasoning. Because the the benchmark will rely on a tightly controlled DSL, confounders like the model's proficiency in a particular programming language or set of libraries will be eliminated. Because the difficulty of the task emerges entirely from relatively simple primitives, it is possible to control, with great precision, the logical requirements for each problem.

For example, feeding a bleeding are, to use linguists' term, “surface true.” The generalized rule is always directly reflected in the outputs. In contrast, counter-feeding and counter-bleeding are “opaque” (like Grimm's law). We hypothesize that LLMs score better on surface true interactions that opaque interactions.