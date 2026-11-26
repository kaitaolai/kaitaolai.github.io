---
layout: page
title: Long-read SVs in an unsolved family
description: PacBio HiFi and ONT genomes, methylation and Fiber-seq
img: assets/img/projects/2_longread_sv.jpg
importance: 2
category: Neuropathy genomics
---

<figure style="float: left; width: 40%; max-width: 300px; margin: 0.3rem 1.5rem 1rem 0;">
  <img src="{{ '/assets/img/projects/detail/2_longread_sv.jpg' | relative_url }}" class="img-fluid rounded z-depth-1" alt="A SMRT Cell for the PacBio Sequel sequencer: single DNA molecules are read in the wells of a chip like this one. Illustration only, not from this study.">
  <figcaption class="caption text-left">A SMRT Cell for the PacBio Sequel sequencer: single DNA molecules are read in the wells of a chip like this one. Illustration only, not from this study.<br><small>Image: Owlmonkey, <a href="https://commons.wikimedia.org/wiki/File:SequelSmrtCell.jpg" target="_blank" rel="noopener">Wikimedia Commons</a>, CC BY-SA 4.0, cropped.</small></figcaption>
</figure>

Some families keep their diagnosis open after short-read genome sequencing because the cause sits where 150-base reads cannot reach: inside long repeats, segmental duplications, inversions and complex rearrangements, or in a change to DNA methylation rather than sequence. For one CMT family that short-read sequencing could not solve, the lab generated PacBio HiFi and Oxford Nanopore genomes, and I analysed them on NCI Gadi.

**SV calling.** Sniffles2, first per sample and then jointly across family members, and cuteSV as a second, independent caller. A third caller, pbsv, was planned but refuses minimap2 alignments with hard-clipped supplementary reads, and re-aligning the raw reads just to add it was not worth the cost. A pilot on chromosome 20 measured run time and memory before the whole-genome runs, so their cost on Gadi was known in advance.

**Beyond sequence.** The same reads carry more than variants. I called CpG methylation, processed Fiber-seq data, which marks open chromatin on single molecules, and genotyped nearly 10,000 tandem repeats with TRGT, including the known pathogenic repeat loci. A family with a known RFC1 expansion, run alongside, was found correctly and confirmed the method; the CMT family had no expansion at any pathogenic locus.

**Candidate review.** The search was limited to the family's linkage regions and 358 neuropathy genes. Calls from both callers were merged, then kept only if absent from unaffected controls, rare in a long-read population database, and supported by reads in both affected family members. The 45 candidate alleles that passed were reviewed one by one against ClinVar and MANE Select transcripts.

The callers were pinned by container digest and every command was recorded, so the analysis can be rerun on the next long-read family without changes.
