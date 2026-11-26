---
layout: page
title: SV calling in neuropathy genomes
description: Re-aligning 103 MRFF whole genomes and calling structural variants
img: assets/img/projects/1_mrff_sv.jpg
importance: 1
category: Neuropathy genomics
---

<figure style="float: left; width: 40%; max-width: 300px; margin: 0.3rem 1.5rem 1rem 0;">
  <img src="{{ '/assets/img/projects/detail/1_mrff_sv.jpg' | relative_url }}" class="img-fluid rounded z-depth-1" alt="Workflow from raw reads to candidate structural variants">
  <figcaption class="caption text-left">The workflow, from raw reads on the university data store to filtered candidate structural variants and back.</figcaption>
</figure>

Families with inherited peripheral neuropathy (Charcot-Marie-Tooth disease and related disorders) whose genetic cause is still unknown were whole-genome sequenced under an MRFF grant at the ANZAC Research Institute. Many of them are likely to carry a variant that short-read pipelines tuned for single-nucleotide changes miss: a deletion, duplication, inversion or insertion of hundreds to millions of bases.

**Why re-align.** The first alignments used a GRCh38 build without decoy sequences, so reads from sequences missing from the reference were forced onto the nearest lookalike and produced false calls. Before re-aligning anything I tested the choice on the Genome in a Bottle HG002 genome: the analysis set with the hs38d1 decoy gave the same structural variant (SV) recall with significantly fewer false SV calls (p < 0.0001) and 44% fewer false SNVs.

**Re-alignment at scale.** All 103 genomes are being re-aligned with GPU Parabricks (fq2bam and DeepVariant), split between NCI Gadi, run as PBS jobs, and the lab's RTX 5090 server. Each genome costs about 140 service units on Gadi. When Gadi's A100 GPU queue was stopped I tested one genome on the H100 queue, then moved the rest across; it turned out cheaper. 68 genomes are done.

**Data handling.** Raw reads come from the university research data store as sftp copy jobs with md5 checks on arrival. Checking every lane against the provider's delivery list found two genomes missing three lanes each in the original 2022 delivery, which explained their low depth. Results go back to the data store under a fixed layout as add-only copies, checked against md5 lists made on Gadi.

**SV workflow for the group.** Manta, smoove and TIDDIT, merged with SURVIVOR and annotated with AnnotSV, then filtered to 356 neuropathy genes, with a read-depth check of the PMP22 region for CMT1A duplications and HNPP deletions. I wrote it up as a step-by-step workshop on Gadi so the team runs it themselves on each new batch.

Patient data stay on secure university and NCI storage; no genome data are public.
