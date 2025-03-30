# RNA & DNA PRE-PROCESSING

Here is a brief description of the steps used in the RNA and DNA pre-processing:

## FASTQC
The FastQ files provided from the whole sequencing, pass first through a quality control analysis using FASTQC tool

## MULTIQC
The MULTIQC tool consists in providing a html report of all the samples fastqc files into one.

## Trimgalore-0.6.7-cutadapt
The Trim Galore tool removes contaminant adapters and read quality trimming from the raw RNA sequencing reads, which leads to the improvement of the quality of the RNA samples.

## STAR Align
Aligns the clean fastq files to the reference genome GRCh38 (depends on the type of data), to output a sam format file, as well as other files, such as, “ReadsPerGene.out.tab" used then in the differential gene expression with DESEQ2.

---FALTA AQUI O RESTO QUANTO AO VARIANT ALIGNMENT DAS AMOSTRAS DE DNA

