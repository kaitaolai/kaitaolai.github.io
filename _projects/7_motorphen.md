---
layout: page
title: MotorPhen
description: Testing a gait Transformer on real patients
importance: 7
category: tools and methods
github: https://github.com/taowis/motorphen
---

I trained a 10-million-parameter Transformer from scratch in PyTorch, reimplementing a published gait anomaly detection model whose code is not public, as groundwork for genotype-informed gait phenotyping in inherited neuropathy. Under a plan fixed before training, it matched the published result on healthy adults but not in 50 stroke survivors (AUROC 0.54 and 0.62, against 0.84 for a one-variable clinical rule).

Code: [github.com/taowis/motorphen](https://github.com/taowis/motorphen).
