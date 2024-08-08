---
layout: page
title: Automating Comparative Reconstruction
description: Work on developing models that reconstruct protolanguages based on collections of cognate sets
img: assets/img/basel-muenster-proj.jpg
importance: 1
category: diachronic
related_publications: true
---
In the 19th century, European philologists made a discovery that would change the direction of the human sciences: they discovered that languages change in systematic ways and that, by leveraging these systematic patterns, it was possible to reproducibly reconstruct ancestors of families of languages (proto-languages) even when no record of those languages survived. This technique, called the comparative method, provided an unprecedented window into the human past—its cultures, its migrations, and its encounters between populations.

The assumption that historical changes in pronunciation (“sound changes”) are regular, known as ‘the regularity principle’ or ‘the Neogrammarian hypothesis’, is fundamental to the comparative method. As the 19th century Neogrammarians Hermann Osthoff and Karl Brugmann put it:

> Every sound change, in so far as it proceeds mechanically, is completed in accordance with laws admitting of no exceptions; i.e. the direction in which the change takes place is always the same for all members of a language community, apart from the case of dialect division, and all words in which the sound subject to change occurs in the same conditions are affected by the change without exception (*Morphologische Untersuchungen auf dem Gebiete der indogermanischen Sprachen i*).

The comparative method, however, is challenging for humans to apply. This is true largely because it involves dealing with large volumes of data and modeling numerous interactions between competing patterns. One must balance the need for phonetic similarity between reconstructed words and their descendants (reflexes) with the need to be able to deterministically derive reflexes from reconstructed words with a single set of sound changes. It imposes a heavy cognitive load. For this reason, researchers have long aspired to implement the comparative method computationally.

In this research, we build upon past research in this area.

- In {% cite chang2022wikihan %}, we propose a new resource for Chinese historical phonology (including Middle Chinese and modern Chinese varieties). This data is foundational to our later papers.
- In {% cite kim2023transformed %}, we show that Transformer-based models can perform better than RNN (e.g., GRU) based models for supervised protoform reconstruction.
- In {% cite lu-etal-2024-improved %}, we further improve automatic comparative reconstruction by using reflex prediction to perform reranking on the beam search results from protoform prediction, emulating the methodology of practicing historical linguists.
- In {% cite cui2024neuralprotolanguagereconstruction %}, we explored VAEs for supervised comparative reconstruction.
- Finally. in {% cite lu2024semisupervisedneuralprotolanguagereconstruction %}, we showed that it is possible to achieve strong performance on the protoform reconstruction task using only a fraction of the number of labeled data by using the Proto-Daughter-Proto architecture, an end-to-end architecture that favors protoforms that can be derived from cognate sets and from which cognate sets can be derived.

References
----------

{% bibliography --cited %}