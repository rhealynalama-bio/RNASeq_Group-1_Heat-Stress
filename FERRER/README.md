# RNA-Seq Literature Familiarization and Data Characterization

**Student Name:** Mary Rose V. Ferrer **Group Number:** 1

## Title and Citation of the Group Paper

Title: Transcriptomic Profiling of *Paulownia elongata* in Response to Heat Stress
Citation: Katiyar, N., Ramadoss, N., Gupta, D., Pakala, S.B., Cooper, K., Basu, C. (2021). Transcriptomic profiling of *Paulownia elongata* in response to heat stress. *Plant Gene*, 28, 100330.
https://doi.org/10.1016/j.plgene.2021.100330

## Assigned RNA-Seq Accession Number

SRR7758332 (experiment SRX4614119, GSM3357468, Control_sample2)

## Control or Treatment Condition

Control

## What This Sample Represents Biologically

This is one of three biological replicates of *P. elongata* leaf tissue grown under normal, unstressed conditions (25°C). It serves as the baseline against which heat-stressed samples (40°C, 24h) are compared to identify genes that change expression in response to heat stress.

## Single-End or Paired-End

Paired-end (R1 forward, R2 reverse)

## Number of Reads

1,349,099 (R1 and R2 each)

## Read Length

34–76 bp

## GC Content

41%

## Summary of FastQC Results

| Module | Result |
|---|---|
| Per-base sequence quality | PASS — Phred scores mostly 32–38 |
| Adapter content | PASS — none detected |
| Overrepresented sequences | PASS — none detected |
| Per base sequence content | FAILED |
| Sequence length distribution | WARNING |
| Sequence duplication levels | PASS |

Overall: Base-calling quality is strong throughout the read (well above the Phred 30 trustworthiness threshold), there's no adapter contamination, and duplication levels pass cleanly. The base-content flag is common in RNA-seq libraries, usually reflecting normal random-hexamer priming bias at the start of reads rather than unusable data. The length-distribution warning tracks the trimmed 34–76 bp range in the run rather than a quality defect.

## Interpretation Questions

1. **What biological question was the original RNA-seq study trying to answer?** What genes/pathways let *P. elongata* tolerate heat stress, since this hasn't been characterized despite the species' known thermotolerance.

2. **Why did the authors use RNA-seq instead of only examining the genome?** The genome alone shows what genes exist, not which are actively transcribed/regulated under a specific condition (heat stress); RNA-seq captures the dynamic expression response.

3. **What is the difference between genomic DNA and the RNA molecules measured by RNA-seq?** DNA is the fixed genetic blueprint (same in all cells); RNA (mRNA) reflects which genes are actively being expressed at a given time/condition; RNA-seq measures this expression, not the static sequence.

4. **What is a biological replicate and why is it important?** An independent biological sample (separate plant/organism) treated identically, used to distinguish true treatment effects from natural biological variation. The paper used 3 replicates per condition.

5. **What is the difference between single-end and paired-end sequencing?** Single-end sequences a fragment from one direction only; paired-end sequences both ends (forward + reverse), giving better mapping accuracy and info on fragment size. This study (and my dataset) is paired-end (R1/R2).

6. **What is a FASTQ file?** A text format storing each read's ID, sequence, a separator, and quality scores (4 lines/read).

7. **What information does FastQC provide?** Per-base and per-sequence quality scores, GC content, sequence length distribution, duplication levels, overrepresented sequences, and adapter content — an overall quality snapshot of raw reads.

8. **What does a high per-base quality score indicate?** Low probability of a base-calling error at that position (Phred ≥30 ≈ 99.9% accuracy), i.e., trustworthy reads.

9. **Why can adapter contamination be a problem?** Leftover sequencing-adapter sequence in reads can mismap during alignment or be misread as biological sequence, distorting expression counts.

10. **Were all RNA-seq samples in your group similar in quality? Explain.** Mostly, but not entirely. All four samples passed per-base and per-sequence quality scores, adapter content, and overrepresented sequences, and all shared the same per base sequence content failure — likely tied to library prep rather than any one run's fault. GC content varied more between conditions than within them: the two control samples (Alama 39%, mine 41%) sat close together, while the two treatment samples (Bullanday 45%, Calipas 41–42%) ran higher, hinting at an expression shift under heat stress. Read counts also varied widely, from about 1.3M (mine) to nearly 5M (Bullanday's), reflecting differences in sequencing depth rather than quality per se.

11. **Did any sample show a possible quality problem? What was it?** My sample (SRR7758332) showed a Sequence Length Distribution warning in addition to the per base sequence content failure shared across the group. This likely reflects the trimmed 34–76 bp read-length range rather than a serious quality issue, since duplication levels, adapter content, and overrepresented sequences all still passed.

12. **What additional steps would be needed before the researchers could compare gene expression between control and treatment samples?** Read trimming/QC filtering, alignment or pseudo-alignment to a reference (or transcriptome, since no genome exists here, hence the Trinity assembly), quantification (e.g., Salmon), and differential expression testing (e.g., edgeR), as done in the published paper.

## Conclusion

This assignment showed how raw RNA-seq reads are structured and evaluated for quality before any biological analysis can happen. My assigned sample (SRR7758332, a control replicate) passed the core quality checks — strong per-base scores and no adapter contamination — despite a couple of expected FastQC warnings common to RNA-seq libraries. Comparing results across the group revealed that data depth and GC content can vary meaningfully even within the same study, which reinforces why QC is a mandatory first step before alignment or differential expression analysis. Going forward, the next step would be trimming, transcriptome alignment, and quantification to reproduce the kind of differential expression results reported in the original paper.
