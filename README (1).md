# RNA-Seq Literature Familiarization and Data Characterization

**Student:** Rhealyn F. Alama
**Group:** 1
**Assigned Topic:** Heat Stress

## Group Paper

**Title:** Transcriptomic Profiling of *Paulownia elongata* in Response to Heat Stress
**Citation:** Katiyar, N., Ramadoss, N., Gupta, D., Pakala, S.B., Cooper, K., Basu, C. (2021). Transcriptomic profiling of *Paulownia elongata* in response to heat stress. *Plant Gene*, 28, 100330. https://doi.org/10.1016/j.plgene.2021.100330

## Assigned RNA-Seq Sample

| Item | Value |
|---|---|
| Run accession | SRR7758331 (SRX4614118, GSM3357467, Control_sample1) |
| Condition | Control |
| Biological replicate | Replicate 1 |
| Single-end or paired-end | Paired-end (R1 forward, R2 reverse) |
| Number of reads | 3,147,060 (R1 and R2 each) |
| Read length | 35–76 bp |
| File size | ~175.5 Mb downloaded; R1 = 237.4 Mbp, R2 = 237.5 Mbp total bases |
| GC content | 39% |

### What this sample represents biologically

This is one of three biological replicates of *P. elongata* leaf tissue grown under normal, unstressed conditions (25°C). It serves as the baseline against which heat-stressed samples (40°C, 24h) are compared to identify genes that change expression in response to heat stress.

## FastQC Summary

| Module | Result |
|---|---|
| Per-base sequence quality | PASS — Phred scores mostly 34–38 |
| Adapter content | PASS — none detected |
| Overrepresented sequences | PASS — none detected |
| Per base sequence content | **FAILED** |
| Sequence length distribution | **FAILED** |
| Sequence duplication levels | WARNING |

**Overall:** Base-calling quality is strong throughout the read (well above the Phred 30 trustworthiness threshold), and there's no adapter contamination. The base-content and duplication flags are common in RNA-seq libraries (often reflecting normal priming bias or highly-expressed transcripts) rather than indicating unusable data.

## Screenshots

- [ ] Galaxy history showing the imported RNA-seq dataset
- [ ] Small FASTQ preview showing the four-line structure
- [ ] FastQC Basic Statistics
- [ ] FastQC Per Base Sequence Quality
- [ ] FastQC Adapter Content (or another key QC result)

*(Add screenshot files to the `screenshots/` folder and reference them here, e.g. `![Basic Statistics](screenshots/basic_stats.png)`)*

## Interpretation Questions

1. **What biological question was the original RNA-seq study trying to answer?**
   What genes/pathways let *P. elongata* tolerate heat stress, since this hasn't been characterized despite the species' known thermotolerance.

2. **Why did the authors use RNA-seq instead of only examining the genome?**
   The genome alone shows what genes exist, not which are actively transcribed/regulated under a specific condition (heat stress); RNA-seq captures the dynamic expression response.

3. **What is the difference between genomic DNA and the RNA molecules measured by RNA-seq?**
   DNA is the fixed genetic blueprint (same in all cells); RNA (mRNA) reflects which genes are actively being expressed at a given time/condition; RNA-seq measures this expression, not the static sequence.

4. **What is a biological replicate and why is it important?**
   An independent biological sample (separate plant/organism) treated identically, used to distinguish true treatment effects from natural biological variation. The paper used 3 replicates per condition.

5. **What is the difference between single-end and paired-end sequencing?**
   Single-end sequences a fragment from one direction only; paired-end sequences both ends (forward + reverse), giving better mapping accuracy and info on fragment size. This study (and my dataset) is paired-end (R1/R2).

6. **What is a FASTQ file?**
   A text format storing each read's ID, sequence, a separator, and quality scores (4 lines/read).

7. **What information does FastQC provide?**
   Per-base and per-sequence quality scores, GC content, sequence length distribution, duplication levels, overrepresented sequences, and adapter content — an overall quality snapshot of raw reads.

8. **What does a high per-base quality score indicate?**
   Low probability of a base-calling error at that position (Phred ≥30 ≈ 99.9% accuracy), i.e., trustworthy reads.

9. **Why can adapter contamination be a problem?**
   Leftover sequencing-adapter sequence in reads can mismap during alignment or be misread as biological sequence, distorting expression counts.

10. **Were all RNA-seq samples in your group similar in quality? Explain.**
    Not entirely. Read depth varied widely across the group — from 1,349,099 reads (Ferrer) to 4,956,271 reads (Bullanday) — and GC content ranged from 39% to 45%. Per-base quality itself was consistently strong (Phred 34–38, PASS) across samples. Notably, both control-condition replicates (mine and Ferrer's) failed the same FastQC module, suggesting a pattern tied to the control library prep rather than random per-run variation.

11. **Did any sample show a possible quality problem? What was it?**
    Yes. Both control samples (mine, SRR7758331, and Ferrer's, SRR7758332) failed "Per Base Sequence Content" and showed a "Sequence Length Distribution" warning. Mine also showed a "Sequence Duplication Levels" warning.

12. **What additional steps would be needed before the researchers could compare gene expression between control and treatment samples?**
    Read trimming/QC filtering, alignment or pseudo-alignment to a reference (or transcriptome, since no genome exists here, hence the Trinity assembly), quantification (e.g., Salmon), and differential expression testing (e.g., edgeR), as done in the published paper.

## Conclusion

This assignment showed how raw RNA-seq reads are structured and evaluated for quality before any biological analysis can happen. My assigned sample (SRR7758331, a control replicate) passed the core quality checks — strong per-base scores and no adapter contamination — despite a couple of expected FastQC warnings common to RNA-seq libraries. Comparing results across the group revealed that data quality and depth can vary meaningfully even within the same study, which reinforces why QC is a mandatory first step before alignment or differential expression analysis. Going forward, the next step would be trimming, transcriptome alignment, and quantification to reproduce the kind of differential expression results reported in the original paper.
