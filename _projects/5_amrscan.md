---
layout: page
title: AMRScan
description: Antimicrobial resistance calling with recorded provenance
img: assets/img/projects/5_amrscan.jpg
importance: 5
category: Tools and methods
github: https://github.com/taowis/amrscan
---

<figure style="float: left; width: 40%; max-width: 300px; margin: 0.3rem 1.5rem 1rem 0;">
  <img src="{{ '/assets/img/projects/detail/5_amrscan.jpg' | relative_url }}" class="img-fluid rounded z-depth-1" alt="Lactose-fermenting <i>Escherichia coli</i> colonies on agar.">
  <figcaption class="caption text-left">Lactose-fermenting <i>Escherichia coli</i> colonies on agar.</figcaption>
</figure>

Antimicrobial resistance (AMR) can now be predicted from a bacterial genome, but a prediction is only as good as the record behind it: which tool, which database release, which input file. AMRScan makes that record part of the result.

**The workflow.** AMRScan calls AMR genes and point mutations in bacterial genome assemblies with NCBI AMRFinderPlus, inside a Nextflow workflow that follows nf-core conventions. Each run writes the software versions, the database release and a hash of every input next to the calls, and harmonises the calls into one table. A second tool archives public antimicrobial susceptibility test results from NCBI Pathogen Detection, so every phenotype can be traced back to its source export and genome. It has run on 1,000 public *E. coli* assemblies on NCI Gadi with every report byte-identical to an earlier run of the same files on another platform.

**The *E. coli* study.** AMRScan is the data layer for a study of genomic AMR prediction: 10,521 public *E. coli* genomes with 162,629 susceptibility results from 26 countries, collected from 2009 to 2025, every genome called with the same pinned AMRFinderPlus release. The question is whether resistance predicted from the genome holds up on lineages, countries, submitting projects and years that were not in training, and why it fails where it does. One model design, L1-penalised logistic regression on sampled k-mers, was tested for 24 antimicrobials, comparing random splits with lineage, country, project, geographic and temporal holdouts on the same test isolates, and against curated AMRFinderPlus rules.

**What it found.** For most drugs, random cross-validation overstated performance only slightly: the median AUROC drop under a holdout was 0.005 for lineage to 0.025 for country.

Code: [github.com/taowis/amrscan](https://github.com/taowis/amrscan). Preprint: [arXiv:2507.08062](https://arxiv.org/abs/2507.08062).
