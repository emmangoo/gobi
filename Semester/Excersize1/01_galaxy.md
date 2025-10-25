# Galaxy

> Galaxy is a free, open-source web-based software for analyzing biological data without programming.

First, we created a new Galaxy account. In order to upload the data, we went to the [NCBI](https://www.ncbi.nlm.nih.gov/) website and from there found the GEO accession number (GSE78711). From there, we found the SRA (SRP070895). Then, we put this number into the [ENA browser](https://www.ebi.ac.uk/ena/browser/home?show=reads). 

From there, we retrieved our FASTQ files. We created a text file with the Id (we had to modify it slightly because we had to use unique names in order for Galaxy to accept them), url, read, and collection. 

In order for this to work we had to add the following filters: 
Filter out first 1 row(s) 
Set column B as URL  
Set column C as Paired-end Indicator  
Set column A as List Identifier(s)  
Set column D as Collection Name

Then we used the FASTQ tool. At the end we had HTML and .txt files for each of the four files.

Next, we created a workflow called "RNA-Seq-fastqc", and added all the necessary steps:
1. Input dataset collection
2. Flatten collection
3. FastQC
4. MultiQC

Lastly, we imported the shared workflow. It contains several pipelines, which are combined in the last step (MultiQC):

1. Input 
2. Quality control: FastQC and Trimmomatic (read trimming based on QC)
3. Alignment: eg, RNA STAR is used to map reads to reference genome (alignment results eg in .bam format)
4. Quantification: featureCounts (and gene locations eg in .bed format) and Count Matrix 
5. Summarising: MultiQC is the last step for each pipeline

All in all, this workflow is a detailed RNA-Seq analysis.

