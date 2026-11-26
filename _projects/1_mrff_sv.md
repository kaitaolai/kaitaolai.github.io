---
layout: page
title: SV calling in neuropathy genomes
description: Re-aligning 103 MRFF whole genomes and calling structural variants
img: assets/img/projects/1_mrff_sv.jpg
importance: 1
category: neuropathy genomics
---

Families with inherited peripheral neuropathy (Charcot-Marie-Tooth disease and related disorders) whose genetic cause is still unknown were whole-genome sequenced under an MRFF grant at the ANZAC Research Institute. The first alignments used a reference without decoy sequences, so I am re-aligning all 103 genomes to GRCh38 with the hs38d1 decoy, using GPU Parabricks on the NCI Gadi supercomputer (PBS) and a lab RTX 5090 server.

- **Reference choice tested first:** on the GIAB HG002 genome, the decoy reference gave the same structural variant (SV) recall with significantly fewer false SV calls (p < 0.0001) and 44% fewer false SNVs.
- **SV workflow for the group:** Manta, smoove and TIDDIT merged with SURVIVOR and annotated with AnnotSV, a filter for 356 neuropathy genes, and a read-depth check of the PMP22 (CMT1A/HNPP) region; documented as a workshop so the team runs it themselves.
- **Data management:** raw data pulled from the university research data store with md5 checks, and results backed up the same way.

Patient data stay on secure university and NCI storage; no genome data are public.
