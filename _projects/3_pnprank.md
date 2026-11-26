---
layout: page
title: PNPrank
description: Ranking neuropathy genes from public single-cell atlases
importance: 3
category: neuropathy genomics
github: https://github.com/taowis/pnprank
---

PNPrank ranks human genes by how likely they are to cause inherited peripheral neuropathy, using cell-type-resolved expression from 11 public single-cell atlases. A truth set of 242 known genes with their discovery years allows a historical test: trained only on genes known before a given year, the model ranks the genes found later with AUROC 0.75 to 0.79. Manuscript submitted to the *Journal of the Peripheral Nervous System*.

Code: [github.com/taowis/pnprank](https://github.com/taowis/pnprank), archived at [doi.org/10.5281/zenodo.23884223](https://doi.org/10.5281/zenodo.23884223).
