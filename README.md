# RNA & DNA PRE-PROCESSING

![PIPELINE_PAPER](https://github.com/user-attachments/assets/2baee38e-da43-4433-bc3f-5186013a2ee4)

1. Here is a brief description of the steps used in the RNA and DNA samples quality check:

## FASTQC
The FastQ files provided from the whole sequencing, pass first through a quality control analysis using FASTQC tool.

## MULTIQC
The MULTIQC tool consists in providing a html report of all the samples fastqc files into one.

## Trimgalore-0.6.7-cutadapt
The Trim Galore tool used only on the RNA samples, removes contaminant adapters and read quality trimming from the raw RNA sequencing reads, which leads to the improvement of the quality of the RNA samples.

2. Brief description of the step to align the RNA samples:

## STAR Align
Aligns the clean fastq files to the reference genome GRCh38 (depends on the type of data), to output a sam format file, as well as other files, such as, “ReadsPerGene.out.tab" used then in the differential gene expression with DESEQ2.

3. Brief description of the step to align the DNA samples:
   
## BWA_MEM 
Secondly, the trimmed reads are then aligned to the human reference genome GRCh38 (Genome Reference Consortium Human Build 38) using the BWA-MEM mapping algorithm (Burrows-Wheeler Aligner), normally used for a better performance for 70-100bp Illumina reads.

## SAMTools
Following the BWA-MEM mapping, the align reads in the SAM format files are converted into BAM format files with SAMtools, that is a compressed binary representation of the SAM file, which reduces the workload and improves the efficiency of the processing steps.

## FastqToSam
The FastqToSam function converts the FASTQ files to an unaligned BAM, outputting read records with original base calls as well as quality scores.

## MergeBamAlinment
The MergeBamAligment function to generate a BAM file containing both alignment and metadata information using the argument -Sort="coordinate".

## MarkDuplicates
The Markduplicates function to identify and tag duplicate reads, arising from sample preparation or library construction via PCR (library duplicates), or as a result of optical duplication (where a single amplification cluster is mistakenly detected as multiple clusters by the sequencing instrument's optical sensor). 

## SortSam
Then, the reads from the Markduplicates are sorted using the SortSam tool.

## BaseRecalibrator
This step creates a base quality recalibration table, incorporating information from known variant sites.

## ApplyBQSR
Finally, the last step is the quality score recalibration (ApplyBQSR) which is performed on the BAM file generated from the MarkDuplicates step, correcting the systematic biases affecting the assignment of base quality scores by the sequencer, based on the recalibration table obtained at the previous step




