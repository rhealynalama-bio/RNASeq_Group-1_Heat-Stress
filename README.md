# RNA-Seq Literature Familiarization and Data Characterization — Group 1

## Paper Title

Transcriptomic Profiling of *Paulownia elongata* in Response to Heat Stress

**Citation:** Katiyar, N., Ramadoss, N., Gupta, D., Pakala, S.B., Cooper, K., Basu, C. (2021). Transcriptomic profiling of *Paulownia elongata* in response to heat stress. *Plant Gene*, 28, 100330. https://doi.org/10.1016/j.plgene.2021.100330

## Group Members

- Alama, Rhealyn F.
- Bullanday, Jasmin Grace T.
- Calipas, Nesie D.
- Ferrer, Mary Rose V.

## Assigned RNA-Seq Accession Numbers

| Member | Accession | Condition |
|---|---|---|
| Alama, Rhealyn F. | SRR7758331 | Control |
| Bullanday, Jasmin Grace T. | SRR7758328 | Treatment |
| Calipas, Nesie D. | SRR7758330 | Treatment |
| Ferrer, Mary Rose V. | SRR7758332 | Control |

## Overview of the Study Used

| Item | Answer |
|---|---|
| Title of the paper | Transcriptomic Profiling of *Paulownia elongata* in Response to Heat Stress |
| Authors | Neerja Katiyar, Niveditha Ramadoss, Dinesh Gupta, Suman B. Pakala, Kerry Cooper, Chhandak Basu |
| Year | 2021 |
| Journal | Plant Gene (Vol. 28, 100330) |
| Organism | *Paulownia elongata* |
| Tissue / organ / cell type | Leaves |
| Biological question | Which genes and pathways are involved in *P. elongata*'s transcriptomic response to heat stress, and can they explain its heat tolerance? |
| Control condition | Plants grown at 25°C, same photoperiod (12h light/12h dark) |
| Treatment or stress condition | Plants exposed to 40°C for 24 hours (heat stress) |
| Number of biological replicates | 3 per condition (3 control, 3 heat-stressed) |
| Sequencing platform | Illumina MiSeq (MiSeq Reagent Kit v3) |
| Single-end or paired-end sequencing | Paired-end |
| Read length, if reported | 76 bp |
| RNA-seq repository | NCBI SRA / GEO |
| BioProject / Study accession | PRJNA485845 (Note: SRA record shows PRJNA488054) |
| Run accession numbers | SRP158908 (SRA study); individual runs include SRR7758328, SRR7758330, SRR7758331, SRR7758332 |
| Reference genome or transcriptome used by the authors | No public reference genome existed for *P. elongata*; authors built a de novo transcriptome assembly using Trinity (v2.0.6) |
| Main RNA-seq software or tools reported by the authors | Trinity (assembly), DIAMOND/BLAST (contamination screening), MEGAN6, OmicsBox/Blast2GO (annotation, GO/KEGG analysis), Salmon (quantification), edgeR (differential expression) |

## Major Results of FastQC (Group Samples)

| Member | Accession | Reads | Read Length | GC % | Main QC Observation |
|---|---|---|---|---|---|
| Alama | SRR7758331 | 3,147,060 | 35–76 bp | 39% | Per Base Sequence Content FAILED; mild duplication/length-distribution warnings; trace polyA adapter content |
| Bullanday | SRR7758328 | 4,956,271 | 35–76 bp | 45% | Per Base Sequence Content FAILED |
| Calipas | SRR7758330 | 3,441,734 | 35–76 bp | 41–42% | Per Base Sequence Content FAILED; Sequence Length Distribution WARNING |
| Ferrer | SRR7758332 | 1,349,099 | 35–76 bp | 41% | Per Base Sequence Content FAILED; Sequence Length WARNING |

## Conclusion

*P. elongata*'s response to heat stress is centered on protecting its existing proteins rather than producing new defensive structures. The original study found that most upregulated genes function in protein binding, unfolding, and chaperone activity, particularly heat shock proteins (HSP83, HSP90, HSP70-family members), which prevent heat-denatured proteins from aggregating and losing function. At the same time, genes tied to ribosome structure, DNA replication, and cell cycle progression were downregulated, likely conserving cellular energy and pausing growth while the plant manages the stress. Together, this indicates that *P. elongata*'s heat tolerance comes from a coordinated, protein-protective transcriptomic response rather than a single defense gene, directly answering the study's biological question about which genes and pathways underlie its thermotolerance.
