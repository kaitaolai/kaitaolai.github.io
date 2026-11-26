---
layout: page
title: PNPrank
description: Ranking neuropathy genes from public single-cell atlases
img: assets/img/projects/3_pnprank.jpg
importance: 3
category: Neuropathy genomics
github: https://github.com/taowis/pnprank
---

<figure style="float: left; width: 40%; max-width: 300px; margin: 0.3rem 1.5rem 1rem 0;">
  <img src="{{ '/assets/img/projects/detail/3_pnprank.jpg' | relative_url }}" class="img-fluid rounded z-depth-1" alt="Immature Schwann cells along nerve fibres, stained for NGFR.">
  <figcaption class="caption text-left">Immature Schwann cells along nerve fibres, stained for NGFR.</figcaption>
</figure>

More than a hundred genes are known to cause inherited peripheral neuropathy, and new ones are still found every year, yet many families remain without a diagnosis. When exome or genome sequencing leaves a family with dozens of rare variants in genes of unknown function, a ranked list of which genes look most like neuropathy genes helps decide where to look first.

**What it does.** PNPrank ranks every human protein-coding gene by how likely it is to cause inherited peripheral neuropathy (CMT, dHMN, HSAN and related hereditary spastic paraplegia). Its features come from cell-type-resolved expression in 11 public single-cell and single-nucleus atlases, together with GTEx tissue expression and gnomAD gene features.

**How it is tested.** Most gene-ranking tools are scored on the same known genes they learnt from, which flatters them. PNPrank uses a truth set of 242 known genes with the year each was first reported. For a given cutoff year the model is trained only on genes known before it and then asked to rank the genes discovered afterwards. This mimics the real use: finding the next gene, not recalling the old ones. Across cutoff years the later genes rank near the top, with AUROC 0.75 to 0.79.

**How the work was run.** The model is compared with simple baselines and with a version without the single-cell features, and negative results are reported as such. Every input atlas is recorded with its source and version so the ranking can be rebuilt from scratch.

The manuscript is submitted to the *Journal of Neuroscience Research*.

Code: [github.com/taowis/pnprank](https://github.com/taowis/pnprank), archived at [doi.org/10.5281/zenodo.23884223](https://doi.org/10.5281/zenodo.23884223).
