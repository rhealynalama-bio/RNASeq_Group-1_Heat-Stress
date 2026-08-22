# Group Paper: Transcriptomic Profiling of *Paulownia elongata* in Response to Heat Stress

**Group:** 1
**Assigned Topic:** Heat Stress

## Full Citation

Katiyar, N., Ramadoss, N., Gupta, D., Pakala, S.B., Cooper, K., Basu, C. (2021). Transcriptomic profiling of *Paulownia elongata* in response to heat stress. *Plant Gene*, 28, 100330.

## Paper DOI / Stable Link

https://doi.org/10.1016/j.plgene.2021.100330

## Study Accession / BioProject Number

- **BioProject:** PRJNA485845 (Note: SRA record shows PRJNA488054)
- **SRA study:** SRP158908
- **GEO series:** GSE119074

## RNA-Seq Run Assignments

| Student | Accession | Condition |
|---|---|---|
| Alama | SRR7758331 | Control |
| Bullanday | SRR7758328 | Treatment |
| Calipas | SRR7758330 | Treatment |
| Ferrer | SRR7758332 | Control |

## Experimental Design Summary

*P. elongata* plants were grown for 14 days, then split into two conditions with three biological replicates each: control plants kept at 25°C, and heat-stress plants exposed to 40°C for 24 hours, both under the same 12h light/12h dark photoperiod. Total RNA was extracted from leaves of both groups, DNase-treated, and sequenced paired-end (76 bp) on an Illumina MiSeq. Since no reference genome exists for *P. elongata*, the authors assembled a de novo transcriptome with Trinity, screened it for contamination, annotated it with Blast2GO, quantified expression with Salmon, and identified differentially expressed genes with edgeR (FDR < 0.05, |log2FC| > 1). This produced 4,435 differentially expressed genes (2,797 upregulated, 1,638 downregulated) under heat stress, followed by GO and KEGG pathway enrichment analysis.
