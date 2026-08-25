Student name: BULLANDAY, JASMIN GRACE T.  
Group number: 1  

Title and citation of the group paper:  
Transcriptomic profiling of Paulownia elongata in response to heat stress  
Katiyar, N., Ramadoss, N., Gupta, D., Pakala, S.B., Cooper, K., & Basu, C. (2021). *Plant Gene*, 28, 100330. https://doi.org/10.1016/j.plgene.2021.100330

Assigned RNA-seq accession number: SRR7758328  

Control or treatment condition: Treatment (heat-treated)  

Short explanation of what the sample represents biologically:  
Total RNA extracted from leaves of a 3-year-old Paulownia elongata plant exposed to heat stress (40 °C for 24 hours). This is one of three biological replicates of the heat-treated condition used to identify genes that change expression under heat stress.

Single-end or paired-end: Paired-end  

Number of reads: 4,956,271 (read pairs / spots)  

Read length: 76 bp  

GC content: 45%  

Summary of FastQC results:  
- Total sequences: 4,956,271  
- Overall quality: Good  
- Passed: Basic Statistics, Per base sequence quality, Per sequence quality scores, Per sequence GC content, Per base N content, Overrepresented sequences (none), Adapter Content (none)  
- Failed: Per base sequence content (common RNA-seq random-hexamer priming bias)  
- Warning: Sequence Duplication Levels  
- Conclusion: Data quality is acceptable for downstream analysis. The only notable issue is the expected per-base sequence content bias; no significant adapter contamination or overrepresented sequences were detected.

Interpretation Questions

1. What biological question was the original RNA-seq study trying to answer?  
They were trying to figure out which genes and pathways actually help P. elongata deal with heat stress. Even though everyone knows the plant is pretty heat-tolerant, nobody had really looked into the molecular details yet.

2. Why did the authors use RNA-seq instead of only examining the genome?  
Looking at the genome only tells you what genes are present. It doesn’t show which ones get turned on or off when the plant is under heat stress. RNA-seq lets you see that real-time expression response.

3. What is the difference between genomic DNA and the RNA molecules measured by RNA-seq?  
DNA is the permanent genetic blueprint—basically the same in every cell. RNA (especially mRNA) shows which genes are actively being used at a specific time and under specific conditions. RNA-seq measures that activity, not the fixed sequence itself.

4. What is a biological replicate and why is it important?  
A biological replicate is just an independent sample (a different plant) that got the exact same treatment. You need them so you can tell real treatment effects apart from normal biological variation. This study used three replicates for each condition.

5. What is the difference between single-end and paired-end sequencing?  
Single-end only sequences one end of each DNA fragment. Paired-end sequences both ends (forward and reverse), which gives better mapping accuracy and also tells you how long the fragment was. This study (and my data) used paired-end reads (R1/R2).

6. What is a FASTQ file?  
It’s a simple text file that stores four lines for every read: the read ID, the actual sequence, a separator, and the quality scores.

7. What information does FastQC provide?  
It gives you a quick overall look at the quality of the raw reads—things like per-base and per-sequence quality scores, GC content, sequence length distribution, how much duplication there is, any overrepresented sequences, and whether adapters are still hanging around.

8. What does a high per-base quality score indicate?  
It means there’s a very low chance that particular base was called wrong. A Phred score of 30 or higher is about 99.9% accurate, so the reads are pretty trustworthy.

9. Why can adapter contamination be a problem?  
If leftover adapter sequence is still in the reads, it can cause them to map to the wrong place or get mistaken for real biological sequence, which messes up the expression counts.

10. Were all RNA-seq samples in your group similar in quality? Explain.  
Not really. The number of reads varied a lot across the group—from about 1.35 million (SRR7758332) up to almost 5 million (SRR7758328)—and GC content ranged from 39% to 45%. The actual per-base quality scores were solid across the board (mostly Phred 34–38 and passed), but both control samples (SRR7758331 and SRR7758332) failed the same FastQC module. That makes it look like something related to how the control libraries were prepared rather than just random run-to-run differences.

11. Did any sample show a possible quality problem? What was it?  
Yes. Both control samples (SRR7758331 and SRR7758332) failed the “Per Base Sequence Content” module and got a warning for “Sequence Length Distribution.” SRR7758331 also had a warning for sequence duplication levels. On top of that, SRR7758332 had a much lower read count (1.3 million) than the others, which could make the later expression analysis less sensitive for that replicate.

12. What additional steps would be needed before the researchers could compare gene expression between control and treatment samples?  
They’d still need to trim and filter the reads, align or pseudo-align them to a reference (or assemble a transcriptome with Trinity since there’s no genome available), quantify the transcripts (for example with Salmon), and then run differential expression testing (like edgeR)pretty much the same pipeline the original paper used.

Conclusion  
This assignment showed how important it is to check the quality of raw RNA-seq reads before doing any real biological analysis. My sample (SRR7758331, one of the controls) passed the main quality checks—strong per-base scores and no adapter contamination—even though it had a couple of the usual FastQC warnings you often see with RNA-seq data. Looking at the whole group made it clear that both quality and sequencing depth can vary quite a bit even within the same study, which is exactly why QC has to be the first step. Next up would be trimming, assembling or aligning the transcriptome, and quantifying expression so we could try to match the differential expression results from the original paper.
