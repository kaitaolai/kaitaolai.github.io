---
layout: page
title: MotorPhen
description: Testing a gait Transformer on real patients
img: assets/img/projects/7_motorphen.jpg
importance: 7
category: tools and methods
github: https://github.com/taowis/motorphen
---

<figure style="float: left; width: 40%; max-width: 300px; margin: 0.3rem 1.5rem 1rem 0;">
  <img src="{{ '/assets/img/projects/detail/7_motorphen.jpg' | relative_url }}" class="img-fluid rounded z-depth-1" alt="Recording muscle activity during movement analysis.">
  <figcaption class="caption text-left">Recording muscle activity during movement analysis.</figcaption>
</figure>

Inherited neuropathies change how people walk, and different genes may leave different marks on gait. Linking genotype to gait needs a way to say which joint departs from normal walking, and by how much, in each person. MotorPhen is groundwork for that.

**The model.** A published approach (GenGait, Motta et al.) trains a masked autoencoder on healthy walking: each joint is hidden in turn and predicted from the others, and a joint that departs from what the model expects is flagged. Its code and data are not public, so I reimplemented it from the description as a 10-million-parameter Transformer in PyTorch, trained from scratch on a CUDA GPU server.

**A test written first.** Before training, I wrote down what would count as a match to the published result and what would count as working on patients. On held-out healthy adults the model matched the published result. On 50 stroke survivors, a group with a clear one-sided gait problem, it did not: asked which leg was the paretic one, the two training runs reached AUROC 0.54 and 0.62, against 0.84 for a one-variable clinical rule (lower peak knee flexion in swing).

**Looking at the cases.** Drawing random participants, not chosen for the result, showed why. All six stroke survivors drawn had a flag on the paretic side, but five also had one on the healthy side, and 44% of healthy trials were flagged too. In the clearest case the reconstruction does what the method promises, raising peak knee flexion of the paretic leg in swing from 31 to 57 degrees, and that case is shown apart from the random draw.

**Why it is still useful.** A clear negative result, measured against simple baselines, tells the neuropathy work what to change before it collects gait data from patients.

Code: [github.com/taowis/motorphen](https://github.com/taowis/motorphen).
