---
layout: page
title: Polygenic risk in inherited neuropathy
description: Do common variants shift onset and severity in CMT, dHMN and HSN?
img: assets/img/projects/0_prs.jpg
importance: 0
category: Neuropathy genomics
---

<figure style="float: left; width: 40%; max-width: 300px; margin: 0.3rem 1.5rem 1rem 0;">
  <img src="{{ '/assets/img/projects/detail/0_prs.jpg' | relative_url }}" class="img-fluid rounded z-depth-1" alt="Polygenic score and the within-family question">
  <figcaption class="caption text-left">The question in one picture: a polygenic score sums many small common-variant effects; relatives who share the same causal variant can sit at different points of its distribution. Schematic.</figcaption>
</figure>

Inherited peripheral neuropathies such as Charcot-Marie-Tooth disease (CMT), distal hereditary motor neuropathy (dHMN) and hereditary sensory neuropathy (HSN) are usually caused by a variant in a single gene. Yet people who carry the same variant, even within one family, can differ widely in age at onset and in severity. This MRFF-funded pilot asks whether common variation, summarised as polygenic scores, explains part of that spread. It is a collaboration between Prof. Marina Kennerson's group at the ANZAC Research Institute and Prof. Melanie Bahlo and Dr. Vicki Jackson (Statistical Genetics, Walter and Eliza Hall Institute, Melbourne). I run the genomics and the analysis.

**Cohort.** 109 short-read genomes from 73 families: 102 affected people, 2 carriers and 5 unaffected relatives. Most affected people have CMT2 (56), followed by HSN (16), HMN (12), and CMT1, CMTX and complex forms.

**Joint calling.** The first cohort file was merged from single-sample VCFs, which cannot tell a homozygous reference genotype from a missing call. That biases scores, and it showed up as low kinship between first-degree relatives. I rebuilt the cohort by joint genotyping from gVCFs (DeepVariant and GLnexus on NCI Gadi), re-aligning 8 genomes from FASTQ and re-calling 3 from vendor BAMs so that every sample went through the same steps. The joint call has 17.1 million sites.

**Quality control.** KING kinship and an unrelated set of 80, a sex check, and PCA by sequencing batch and caller. The PCA picked out three samples called with a different variant caller, which would have confounded any case/control comparison inside the cohort; this is one reason the design compares relatives within families. One genome aligned to two versions of GRCh38 showed that the reference build moves a score by about 0.001 SD, so it can be ruled out as a source of bias.

**Scoring.** Published PGS Catalog scores are computed with pgsc_calc, with projection onto a reference panel to adjust for ancestry. Two height scores serve as a negative control: height has no expected link with neuropathy, so a difference there would point to a technical problem rather than biology. They showed no difference between genetically solved and unsolved patients.

**Next.** Selected PGS Catalog scores tested as modifiers of age at onset and severity, comparing affected relatives within families.

The genomes and clinical data are identifiable patient data and stay on university and NCI storage. The code repository is private, and its commit hooks reject data files and sample identifiers.
