---
layout: page
title: Germline NGS panel validation
description: A clinical-style validation of a 31-gene panel pipeline
img: assets/img/projects/6_ngs_panel.jpg
importance: 6
category: Tools and methods
github: https://github.com/taowis/ngs-panel-validation
---

<figure style="float: left; width: 40%; max-width: 300px; margin: 0.3rem 1.5rem 1rem 0;">
  <img src="{{ '/assets/img/projects/detail/6_ngs_panel.jpg' | relative_url }}" class="img-fluid rounded z-depth-1" alt="Pipetting DNA in a genomics laboratory (National Human Genome Research Institute).">
  <figcaption class="caption text-left">Pipetting DNA in a genomics laboratory (National Human Genome Research Institute).</figcaption>
</figure>

Before a clinical genetics laboratory reports variants from a sequencing pipeline, it has to show that the pipeline finds the variants that are really there and does not report ones that are not. In Australia this is assessed against ISO 15189:2022 and the NPAAC requirements for massively parallel sequencing. This project carries out that validation openly, end to end, the way a diagnostic laboratory would document it.

**The pipeline.** Germline variants in 31 genes linked to hereditary breast, ovarian and colorectal cancer, including BRCA1, BRCA2, PALB2, the mismatch repair genes, APC and TP53, called with BWA-MEM and GATK HaplotypeCaller with hard filters.

**Scoring against known truth.** Genome in a Bottle reference samples, whose variants are known from many sequencing technologies, were compared with the calls inside the panel genes using RTG vcfeval. Coverage, repeat runs of the same data and two libraries from the same person tested whether results repeat. Acceptance criteria were written down before any results existed, so the bar could not move after seeing them.

**The first version failed.** All three panel variants missed in the first library had been called correctly and then removed by one strand-bias rule in the standard GATK filter. The fix went through change control: a written plan, candidate filters compared on odd-numbered chromosomes, and the chosen one tested on even-numbered chromosomes so the test data played no part in the choice. On four more GIAB genomes, sequenced by a second laboratory with a different capture kit, no panel SNV was missed (316 of 316 across five genomes).

**Running it like a lab.** A risk register covers 18 failure modes, and an update to DeepVariant was verified from the exported VCFs alone, as a laboratory would do with a supplier update it cannot inspect.

Code and reports: [github.com/taowis/ngs-panel-validation](https://github.com/taowis/ngs-panel-validation).
