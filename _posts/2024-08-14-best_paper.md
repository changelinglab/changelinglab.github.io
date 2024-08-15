---
layout: post
title: On our ACL Best Paper Award Paper
date: 2024-08-15 16:40:16
description: a short philosophical discursion
tags: formatting links
categories: sample-posts
---

Yesterday, my student Liang (Leon) Lu won the Best Paper Award (Non-Publicized) at the 2024 Association for Computational Linguistics conference in Bangkok for his paper “Semisupervised Neural Proto-Language Reconstruction.” We are generally impressed by students who win this awards, but in Leon's case their is double reason to be impressed. Not only is he an undergraduate student (just starting his third year of university), he has only submitted two papers to conferences. Both were accepted and the second (his first submission to a *ACL conference) was the subject of this best paper award. But what is the substance of this paper?

If you are technical, you can go and read the paper for yourself. It is short and is, I think, fairly clearly written. If you are not technical but you have some training in historical linguistics, you will recognize some of the principal themes, even if you don't follow the complete methodology or analysis. However, if you are neither technical nor trained in historical linguistics, but you still want to know what this paper was about, I will do me best to let you know.

First, let us consider a table of words from the related languages Kachai, Huishu, and Ukhrul (members of the family of languages called Tangkhulic):

|--------|---------------|--------|----------|---------|
| Gloss  | ‘grandchild’  | ‘bone’ | ‘breast’ | ‘laugh’ |
|--------|---------------|--------|----------|---------|
| Kachai | ðɐ            | rɐ     | nɐ       | ni      |
| Huishu | ruk           | ruk    | nuk      | nuk     |
| Ukhrul | ru            | ru     | nu       | nu      |
|--------|---------------|--------|----------|---------|

Note that the ð sound is like the th in *this* and the ɐ sound is sort of like the u in cup.

If you look at these words, you can see that there is, for example, a systematic relationship between the words for ‘bone‘ and those for ‘breast’. This extends to ‘grandchild’ as well, even though there is a somewhat unexpected consonant in Kachai (ð). What did the ancestors of these words look like in the shared ancestor of these languages? Is this lost in the mists of history?

A group of 19th century linguists (of philologists, to use the terminology then current) called the Neogrammarians said you can know how these ancestral forms of words (protoforms) were pronounced by applying a methodology we now call the Comparative Method. Central to this method is the **regularity principle** which states that changes in pronunciation apply as general rules to which **all** words in a language are subject. This means that if you know the protoform for one of the columns in the table (these columns are what are known as “cognate sets”) you can derive all of the rows in that column deterministically—mechanically and unambiguously.

Under these Neogrammarian assumptions, we could posit *ruk or *ru as reconstructions for ‘bone’. If we posit *ru, we must assert that there was a sound change in Kachai that changed u to ɐ and a sound change in Huishu that inserted k at the ends of words (perhaps after u). If we reconstruction \*ruk, we have to assume that there was a sound change in both Kachai and Ukhrul that deletes k at the end of words (perhaps after u) and another sound change in Kachai that changes u to ɐ. The first option (\*ru) ends up working better if we look at all of the cognate sets instead of just these four.

By this logic, we get:

|--------|---------------|--------|----------|---------|
| Gloss  | ‘grandchild’  | ‘bone’ | ‘breast’ | ‘laugh’ |
|--------|---------------|--------|----------|---------|
| Kachai | ðɐ            | rɐ     | nɐ       | ni      |
| Huishu | ruk           | ruk    | nuk      | nuk     |
| Ukhrul | ru            | ru     | nu       | nu      |
|--------|---------------|--------|----------|---------|
| Proto-Tangkhulic | *?u | *ru    | *nu      | *n?     |
|------------------|-----|--------|----------|---------|

The reconstruction of ‘grandchild’ must end in u, but it must start with something other than r. Why? Because if it did start with r, there would be no way of explaining why, in Kachai, ‘grandchild’ starts with ð but ‘bone’ starts with r through the application of regular sound change. This would be an **unconditioned split**, something that the regularity principle rules out.

Looking at the full collection of cognate sets, we would probably make the following reconstructions (or their formal equivalents):

|--------|---------------|--------|----------|---------|
| Gloss  | ‘grandchild’  | ‘bone’ | ‘breast’ | ‘laugh’ |
|--------|---------------|--------|----------|---------|
| Kachai | ðɐ            | rɐ     | nɐ       | ni      |
| Huishu | ruk           | ruk    | nuk      | nuk     |
| Ukhrul | ru            | ru     | nu       | nu      |
|--------|---------------|--------|----------|---------|
| Proto-Tangkhulic | *du | *ru    | *nu      | *nɨ     |
|------------------|-----|--------|----------|---------|

where ɨ is a vowel that is half-way between i and u. These protoforms make sense based on the reflexes: they are similar in pronunciation to the reflexes and the reflexes can all be derived from them mechanically.

There have been past efforts to build neural models (neural networks) that can perform this kind of reconstruction (including some from our lab), but they have two unfortunate properties:

1. They only take the reflex-to-protoform mapping into account (not the protoform-to-reflex mapping).
2. Training them (teaching them to generate reconstructions given sets of cognate reflexes) requires many cognate sets, each of which must be paired with a reconstruction.

In actual reconstruction projects, as I know from first hand experience, the constraint in 2 is only satisfied when the most challenging and interesting work in reconstructing a protolanguage has already been done. What Leon discovered as part of this paper is that 2 is a consequence of 1—we are forced to do fully supervised training (a protoform for every cognate set) because we are not enforcing the regularity principle (not rejecting protoforms if—for example—identical protoforms are mapped to different reflex forms in a single language).

To make things clearer, let's return to our example. The older kind of fully-supervised reconstruction models is likely to produce the reconstructions below:

|------------------|---------------|--------|----------|---------|
| Gloss            | ‘grandchild’  | ‘bone’ | ‘breast’ | ‘laugh’ |
|------------------|---------------|--------|----------|---------|
| Kachai           | ðɐ            | rɐ     | nɐ       | ni      |
| Huishu           | ruk           | ruk    | nuk      | nuk     |
| Ukhrul           | ru            | ru     | nu       | nu      |
|------------------|---------------|--------|----------|---------|
| Proto-Tangkhulic | *du           | *ru    | *nu      | ***nu** |
|------------------|---------------|--------|----------|---------|

This is because having a u in Ukhrul and a u in Huishu is generally a reliable cue for reconstructing *u in the protoform. However, this reconstruction cannot be right, following the regularity principle, because a single pronunciation in the protolanguage would be reflected as two different pronunciations in Kachai.

Leon's technical innovation was to design a neural network that can learn both to reconstruct protoforms based on reflexes (daughter-to-protoform) and to disfavor protoforms from which reflexes cannot be derived (proto-to-daughter). The D2P and P2D networks are joined together with a “bridge network” that allows both networks to be trained as a single network. The resulting type of neural network is similar in some ways to what is called a “variational autoencoder” but it differs in that the outputs of the D2P network are not real-valued vectors but strings of symbols (in the International Phonetic Alphabet).

In training, the model can thus take advantage of cognate sets without a protoform, something that the earlier, fully supervised, models could not do.

The implications of this development are striking. Given the same amount of labeled data (cognate sets with protoforms), our DPD models outperform the best fully supervised models as well as the best semisupervised models we could train. And careful statistical testing shows that the differences are as significant as they look at first glance.

We think that this approach is very promising and looks forward to a day, not too far in the future, when neural models like this will be a tool in the belt of every historical linguist and will help shed light on the dark recesses of the human past.