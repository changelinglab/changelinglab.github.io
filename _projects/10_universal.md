---
layout: page
title: Universal Phone Recognition
description: Recognizing phonetic units in a language-neural fashion
img: assets/img/gruyere-tower-proj.jpg
importance: 1
category: speech
related_publications: true
---

Modern ASR systems typically units larger than an individual sound. However, sometimes it is desirable to recognize individual sounds, whether as structural units of a particular language (phonemes) or as language-neural idealizations of an acoustic/articulatory unit (phones). Recognizing phones is valuable for a variety of applications:

- Language documentation
- Very low resource ASR
- Zero-shot language identification from speech
- Analysis of atypical speech (e.g., dysarthric or non-native speech)
- 
However, existing universal ASR systems suffer from a couple of deficits:

- They display very high phone error rates
- They do not handle some important phenomena like tone.
  
Tone and other **suprasegmentals** are very challenging because they are really phonological rather than phonetic. All speech, for example, displays acoustic variation in frequency, but only some languages use this variation to distinguish words from each other. Thus, hard work is required in order to know how to characterize tone in a language-neural fashion.

Building both on past efforts at universal phone recognition {% cite li2020universal yan2021differentiable %}and current self-supervised speech models, we aim to build high-accuracy models that can transcribe speech as IPA (International Phonetic Alphabet) with the same reliability as a human linguist.