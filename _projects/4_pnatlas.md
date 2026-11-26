---
layout: page
title: PNPAtlas
description: A multiscale reference of the human peripheral nervous system
img: assets/img/projects/4_pnatlas.jpg
importance: 4
category: Neuropathy genomics
github: https://github.com/taowis/pnatlas
---

<figure style="float: left; width: 40%; max-width: 300px; margin: 0.3rem 1.5rem 1rem 0;">
  <img src="{{ '/assets/img/projects/detail/4_pnatlas.jpg' | relative_url }}" class="img-fluid rounded z-depth-1" alt="PNPAtlas gene lookup page for MPZ">
  <figcaption class="caption text-left">The PNPAtlas gene lookup for MPZ: its expression is concentrated in myelinating Schwann cells.<br><small>Screenshot: <a href="https://taowis.github.io/pnatlas/#gene/MPZ" target="_blank" rel="noopener">taowis.github.io/pnatlas</a>.</small></figcaption>
</figure>

Peripheral neuropathy can start in the neuron body, which sits in a ganglion next to the spinal cord, or along the axon and its Schwann cells, which can run a metre down the leg. Public single-cell data now exist for both places, but mostly as separate studies with different labels and methods, which makes it hard to ask in which cells a neuropathy gene is active.

**What it is.** PNPAtlas is a reference of human peripheral nervous system cell states built only from public data. It joins single-nucleus data from sensory and autonomic ganglia and peripheral nerve under one set of labels, and places those states in tissue with spatial data (44 Visium sections and 3 Xenium panels).

**Three questions.**

1. Which ganglion and nerve cell states carry the genes for each class of inherited neuropathy (CMT, dHMN, HSAN)?
2. How does the cell make-up of tibial nerve vary across 670 GTEx donors, and which nerve eQTLs act in specific cell states?
3. Do nerve and spatial features improve PNPrank's historical test?

**A test fixed in advance.** The third question was written into the analysis plan, with the comparison and the decision rule, before it was run, and a null result would have been reported as such. Adding the PNPAtlas features improved the historical test from AUROC 0.771 to 0.778 (p = 0.031). The gain is small, and is reported as small.

**Using it.** A public gene lookup site shows, for any gene, its expression in each of 31 reference cell states, how it tracks nerve cell fractions across GTEx tibial nerve samples, its colocalisation tests with neuropathy GWAS, and whether it belongs to a known neuropathy gene class. A data archive for Zenodo is being prepared.

Gene lookup: [taowis.github.io/pnatlas](https://taowis.github.io/pnatlas/). Code: [github.com/taowis/pnatlas](https://github.com/taowis/pnatlas).
