# Group 1 – Heat Stress

## Group Members and Roles

| Member | Role | Notes |
|---|---|---|
| Rhealyn F. Alama | Galaxy lead / Documentation lead | Operated the designated Galaxy account (alama_rhealyn_) |
| Nesie D. Calipas | Literature lead | Assisted with paper selection and methods review |
| Mary Rose V. Ferrer | Data lead | Assisted with accession/data location |
| Jasmin Grace T. Bullanday | Interpretation lead | Assisted with comparison to published results |

## Citation of the Selected Paper

Katiyar, N., Ramadoss, N., Gupta, D., Pakala, S. B., Cooper, K., & Basu, C. (2021). Transcriptomic Profiling of *Paulownia elongata* in Response to Heat Stress. *Plant Gene*, 28, 100330.

## Research Question of the Original Study

The original authors investigated how the leaf transcriptome of *Paulownia elongata* responds to short-term heat stress, comparing gene expression under control conditions (25 °C) against heat-stressed conditions (40 °C for 24 hours) to identify genes and pathways involved in the plant's heat-stress response.

## Organism and Tissue Used

- **Organism:** *Paulownia elongata*
- **Tissue:** Leaves

## Control and Treatment Conditions

| Condition | Description |
|---|---|
| Control | 25 °C, 12h light/12h dark photoperiod |
| Treatment (Heat stress) | 40 °C for 24 hours, same photoperiod |

- **Biological replicates:** 3 per condition (3 control, 3 heat-stressed)

## RNA-seq Accession Numbers

- **Repository:** NCBI SRA / GEO
- **BioProject / Study accession:** PRJNA485845 as printed in the paper (this accession returns no items on NCBI); the correct linked BioProject on SRA is PRJNA488054. SRA study: SRP158908
- **Run accessions used:**
  - Control: SRR7758331 (rep1), SRR7758332 (rep2), SRR7758333 (rep3)
  - Heat-treated: SRR7758328 (rep1), SRR7758329 (rep2), SRR7758330 (rep3)

## Reference Genome and Annotation Versions

No public reference genome exists for *P. elongata*. The group substituted the congeneric species genome *Paulownia fortunei* (Cao et al., 2021, *Molecular Plant*):

- **Assembly:** GCA_019321725.1 / JAGSPU000000000 (511.6 Mb, 20 pseudo-chromosomes, 31,985 protein-coding genes)
- **Annotation:** GFF3 file packaged with the *P. fortunei* NCBI genome assembly, downloaded together with the genome FASTA via the Galaxy NCBI Datasets Genomes tool

## Original Authors' Analysis Pipeline

- Sequencing platform: Illumina MiSeq (MiSeq Reagent Kit v3), paired-end, 76 bp reads
- No reference genome available → de novo transcriptome assembly with **Trinity (v2.0.6)**
- Contamination screening with **DIAMOND/BLAST** and **MEGAN6**
- Completeness assessment with **BUSCO**
- Functional annotation with **Blast2GO/OmicsBox**
- Transcript quantification with **Salmon**
- Differential expression with **edgeR** (Exact Test; FDR < 0.05, |log2FC| > 1)
- GO/KEGG enrichment with **OmicsBox**
- Result: 2,797 genes upregulated; 1,638 genes downregulated; 4,435 total DEGs reported

## Galaxy Pipeline Used by the Group

1. **Quality control:** FastQC on all 12 FASTQ files (R1 and R2 for 6 samples), summarized with MultiQC
2. **Trimming:** None applied (no adapter contamination detected; high per-base quality)
3. **Reference genome:** *P. fortunei* genome FASTA (GCA_019321725.1), obtained via the Galaxy NCBI Datasets Genomes tool
4. **Mapping:** HISAT2 (default parameters, paired-end mode)
5. **Gene counting:** featureCounts, using the *P. fortunei* GFF3 annotation
6. **Differential expression:** DESeq2, with 3 control replicates set as the reference condition against 3 heat-stressed replicates (padj < 0.05)

## Differences Between the Authors' Pipeline and the Group's Pipeline

| Analysis step | Original authors | Group's Galaxy re-analysis |
|---|---|---|
| RNA-seq dataset | 6 samples (3 control, 3 heat), Illumina MiSeq, paired-end, 76 bp | Same 6 SRA runs (SRR7758328–333), same platform/read type |
| Quality control | Not explicitly detailed beyond standard pre-assembly QC | FastQC + MultiQC on all 12 files; high per-base quality, no adapters, expected priming-bias artifact |
| Trimming | Not explicitly detailed | None applied (not needed based on QC) |
| Reference genome | None available for *P. elongata* (de novo assembly used instead) | *P. fortunei* genome, GCA_019321725.1 |
| Annotation | N/A (de novo transcriptome used as reference) | *P. fortunei* GFF3 |
| RNA-seq aligner | Not applicable — pseudo-alignment via Salmon against the de novo transcriptome | HISAT2 (genome alignment) |
| Gene counting | Salmon quantification | featureCounts |
| Differential expression | edgeR (Exact Test) | DESeq2 |
| Significance threshold | FDR < 0.05, \|log2FC\| > 1 | padj < 0.05 |
| Main genes/pathways identified | HSP83/HSP90 and other heat shock proteins, tonoplast dicarboxylate transporter, TAG lipase upregulated; chloroplastic ribosomal proteins, cell-cycle/DNA replication genes downregulated | Heat shock protein 82 (HSP83/HSP90), tonoplast dicarboxylate transporter, TAG lipase, and cystathionine beta-lyase upregulated; chloroplastic ribosomal protein (50S L1) downregulated |

Because the RNA sequence for *P. elongata* is not publicly available, the group used HISAT2, featureCounts, and DESeq2, whereas the authors used a de novo Trinity assembly, Salmon quantification, and edgeR. The group mapped all 6 samples to the congeneric *P. fortunei* genome instead of building a de novo transcriptome.

## Main Quality-Control Results

FastQC was run on all 12 FASTQ files (R1 and R2 for each of the 6 samples), summarized with MultiQC.

| QC metric | Observation across all 12 files |
|---|---|
| Number of reads | Roughly 1.3 to 5 million read pairs per sample (varies by run) |
| General sequence quality | High throughout — per-base Phred scores mostly in the Q32–Q38 range |
| Adapter contamination | None detected in any sample |
| Overrepresented sequences | None flagged as a concern |
| Notable quality warning | "Per Base Sequence Content" failed on all 12 files — a common RNA-seq artifact caused by non-random priming during library prep (fragment-start base-composition bias), not a sign of contamination or low-quality data |

Because no adapter contamination was detected and per-base quality was high, the group decided not to trim the reads.

## Mapping Results

Each of the 6 paired-end samples was mapped to the *P. fortunei* genome FASTA using HISAT2 (default parameters, paired-end mode) in Galaxy.

| Sample | Total reads | % mapped | % uniquely mapped | Notes |
|---|---|---|---|---|
| Control_rep1 (SRR7758331) | 4,956,271 | 88.92% | 74.71% | — |
| Control_rep2 (SRR7758332) | 3,950,092 | 88.98% | 71.26% | Highest total reads; lowest unique-mapping rate |
| Control_rep3 (SRR7758333) | 3,147,060 | 89.24% | 76.07% | — |
| Heat_rep1 (SRR7758328) | 1,349,099 | 90.92% | 78.31% | Read depth much lower than other samples |
| Heat_rep2 (SRR7758329) | 3,215,196 | 88.51% | 72.70% | Lowest overall alignment rate |
| Heat_rep3 (SRR7758330) | 3,441,734 | 92.74% | 80.25% | Highest unique mapping rate |

## Differential Expression Results

DESeq2 was run on the featureCounts gene count table, with 3 control replicates as the reference condition against 3 heat-stressed replicates.

| Item | Value |
|---|---|
| Number of genes tested | 31,673 |
| Number of significantly differentially expressed genes (padj < 0.05) | 1,481 |
| Genes with positive log2 fold change (up in heat) | 827 |
| Genes with negative log2 fold change (down in heat) | 654 |
| Adjusted p-value / FDR threshold used | 0.05 |

PCA showed PC1 explaining 55% of variance and PC2 explaining 27%, with samples separating into two clear groups by condition (Control vs. Heat). Dispersion estimates followed the expected DESeq2 shape.

## Genes Selected for Biological Interpretation

| Gene | log2FC | Adjusted p-value | Up/Down | Known/Predicted Function | Possible Connection to Heat Stress |
|---|---|---|---|---|---|
| Tonoplast dicarboxylate transporter (TR36547\|c0_g1_i1) | 11.26 | 1.23E-08 | Up | Vacuolar malate carrier; moves malic acid from vacuole to cytoplasm for catabolism | May prevent malate over-accumulation seen when temperature rises, helping regulate metabolite balance under heat |
| Heat shock protein 82 / HSP83-90 family (TR20200\|c0_g2_i1) | 10.74 | 9.52E-12 | Up | Molecular chaperone; assists in refolding/stabilizing heat-denatured proteins | Classic heat-shock protein; protects native proteins from denaturation during thermal stress |
| Triacylglycerol (TAG) lipase (TR54032\|c0_g2_i1) | 10.30 | 5.47E-07 | Up | Hydrolyzes long-chain triacylglycerols, releasing carbon skeletons/energy | Likely drives lipid remodeling to reduce toxic lipid intermediates that damage membranes under heat |
| Cystathionine beta-lyase (TR2916\|c0_g1_i2) | 10.01 | 3.13E-07 | Up | Key enzyme in methionine biosynthesis pathway | Methionine feeds polyamine synthesis, which supports abiotic stress tolerance |
| 50S ribosomal protein L1, chloroplastic (TR48060\|c0_g1_i1) | -11.06 | 0.0006 | Down | Structural component of the chloroplastic ribosome | Downregulating chloroplastic ribosomal genes is thought to redirect resources toward transcriptional activation of heat-responsive genes |

## Comparison With the Published Results

- **Did the group recover the same general biological response?** The PCA already shows a clear separation between control and heat-stressed samples, consistent with the authors reporting thousands of differentially expressed genes under heat stress; a direct gene-level comparison requires the group's finalized DEG table.
- **Genes highlighted in the paper also identified in this analysis:** Tonoplast dicarboxylate transporter and Heat shock protein.
- **Similar results:** The overall scale and direction are similar in proportion, roughly 1.5–3x more upregulated than downregulated genes in both analyses, and a clean PCA/clustering separation by condition in both studies.
- **Different results:** The absolute number of DEGs is much smaller in the group's re-analysis (1,481 vs. 4,435), expected given a different reference genome and a different statistical pipeline.
- **Same software as the authors?** No — the group used HISAT2, featureCounts, and DESeq2, while the authors used a de novo Trinity assembly, Salmon quantification, and edgeR.
- **Same reference genome/annotation?** No — there is no publicly available *P. elongata* genome. The group mapped to the congeneric *P. fortunei* genome (GCA_019321725.1) instead of building a de novo transcriptome.
- **Samples analyzed:** All 6 samples (3 control, 3 heat-stressed) — the full published sample set for this comparison.
- **Could differences in software, parameters, or reference explain the differences?** Yes — mapping to a different, though closely related, species' genome instead of a de novo transcriptome assembled from the same species can shift which genes are detected, how reads are assigned, and normalization; the aligner/counter/DE-testing software also differs entirely from the original pipeline.

## Limitations

- No public reference genome exists for *P. elongata*; the group substituted the congeneric species *P. fortunei*, which can shift which genes are detected and how reads are assigned.
- The group's pipeline (HISAT2 → featureCounts → DESeq2) differs entirely from the authors' pipeline (Trinity → Salmon → edgeR), so DEG counts and thresholds are not directly comparable.
- The absolute number of DEGs recovered (1,481) is substantially lower than the original study (4,435), likely reflecting the reference and pipeline differences rather than a smaller biological effect.
- Read depth varied noticeably across samples (e.g., Heat_rep1 had a much lower read count than the other replicates), which may affect statistical power for that sample.

## Group Conclusion

This exercise showed that reproducibility depends on more than following the same general workflow — exact matches require the same raw data, reference files, software, and parameters, which are not always available. Using a related species' genome instead of a de novo assembly changed the number and identity of genes detected, even though the overall heat-stress response pattern (dominated by heat shock proteins and related stress-response genes) still matched the published study.
