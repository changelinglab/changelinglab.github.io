---
layout: page
title: Systematic Relationships for Improved ASR
description: Better ASR for low resource varieties
img: assets/img/fribourg-cathedral-proj.jpg
importance: 1
category: speech
related_publications: true
---

We seek to take advantage of the systematic relationships between languages—the consequence of regular sound change and morphological developments—to build better ASR systems for low-resource varieties given ASR models for high-resource varieties.

In {% cite chou2023evaluating %}, we collected a corpus of soap operas spoken in Taiwanese Hokkien, a low resource variety spoken in Taiwan, 
and trained E2E ASR models with (frozen) self-supervised speech representations. The S3M pretrained on Mandarin performed the best in our model, showing the effectiveness of transfer learning from a high resource sister language. However, the word error rates (WERs) were still abysmal due to the low amount of data.

As we show in {% cite chang-chou-etal-2024-s3m-aave %}, SSL pre-training on Mainstream American English per se cannot generalize to unseen pronunciation variants in African American Vernacular English in a zero shot manner, despite being touted for their ability to lower WERs with less data and for the linguistic (phonetic, phonological, etc) information they encode. This motivates a new approach based on speech in-context learning and on the regularity of sound change.
