---
layout: post
title: Information and Comparative Reconstruction
date: 2024-08-14 16:40:16
description: Informal information-theoretic framing of the comparative method in historical linguistics
tags: formatting links
categories: sample-posts
---

When the Neogrammarians said that “sound changes admit no exceptions,” they were saying that sound changes apply deterministically. Thus, the output can always be derived given the input (but the converse is not necessarily true). To put this in terms of information, a sound change never adds information. It may destroy information (mergers, deletions); it may move information around (conditioned splits, transphonologization); but it may never delete information. In other words, there can be no unconditioned splits.

Of course, there are language changes that do add information and, using the regularity principle as a definition, these are not sound changes. The Neogrammarians assumed a qualitative difference between these changes and those encoded in “sound laws.” Analogical processes, for example, add information, so the whole family of analogical changes (paradigmatic extension, paradigm leveling, contamination, and so forth) are treated as something entirely different, as is borrowing—including “dialect borrowing” which may yield forms that look superficially like true cognates of other, semantically similar, words in sister languages.

At some level, it is not clear to me that there is a qualitative difference between dialect borrowing and the propagation of a sound change through a speech community. However, because the Neogrammarian formulation of the Regularity Principle provides a way of—by definition—separating changes that proceed mechanistically from those than proceed sporadically, it serves an important methodological function: it allows for a precise formulation of a framework for doing comparative reconstruction.

When viewed from the standpoint of information, comparative reconstruction is a kind of compression and the comparative method is a compression algorithm. It takes collections of cognate sets and reduces each of them to a single form from which all of the reflexes in the cognate set can be derived through the application of finite sequences of rewrite rules (one for each language). By definition, then, each reconstructed protoform must contain all of and only the information in the corresponding cognate set.

It is probably possible to formalize this algorithm in a backwards direction only (from cognate sets to protoforms). However, in my experience, linguists solve this compression problem by iterating over the protoforms and the rules until

1. The protoforms can be predicted from the cognate sets
2. The cognate sets can be predicted from the protoforms, give the sound laws

Humans are generally not bad at noticing cases of analogy and borrowing, given their ability to integrate rich evidence from diverse sources. This is a challenge for computational implementations of this “algorithm”. We have tried various approaches {% cite chang2022wikihan kim2023transformed lu-etal-2024-improved lu2024semisupervisedneuralprotolanguagereconstruction %} and have found the most successful to be (1) neural approaches that (2) take into account both the lossless mapping from reflex to protoform and the lossy mapping from protoform to reflex {% cite lu-etal-2024-improved lu2024semisupervisedneuralprotolanguagereconstruction %}. These approaches have the virtue of being robust to “noise” (analogy and borrowing) and the disadvantage that they cannot provide cascades of sound laws like humans can.

I have left another thing out: it is possible for a reconstruction to be valid with regards to these information-theoretic criteria and still be a bad reconstruction. That is to say, a reconstruction may be structurally sound but substantively incoherent. Consider, for example, that substitution ciphers do not change the information present in a string. However, there are a very large number of possible substitution ciphers, even for a finite alphabet. Some constraint is needed to enforce the similarity between protoforms and reflexes. This could be seen as a constraint upon sound laws and cascades of sound laws. For example, sound laws must be equivalent to finite state transducers and cascades are legal only when there is no equally compliant set of cascades with a smaller number of sound laws.