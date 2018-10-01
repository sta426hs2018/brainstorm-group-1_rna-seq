# brainstorm-group-1_rna-seq
brainstorm-group-1_rna-seq created by GitHub Classroom

# Group Members
GitHub name in (brackets)

* Falko Noe (CodingKaiser)
* Weifan Sun (Wenfei-Sun)
* Xi
* Ainesh Sewak (asewak)

## RNAseq introduction
[RNAseq introduction](https://prezi.com/view/4Xsw1r6RbN8kvAiNyKqZ)

## Why do we sequence RNA? 
Since DNA sequence is identical (in theory) throughout one individual organism, what makes the various tissue/cell types is the usage of the DNA. The first step of using the DNA is transcription that generates RNA. The transcriptome conveys biological information that reflects the function of a cell/tissue. Thus, profiling RNA could help us understand how a cell/tissue work and probe the state of a cell/tissue.
## Applications
(1) Differentiation gene expression analysis
(2) Explore novel RNA expression, eg. non-coding RNA, micro RNA, piwi RNA etc.
(3) Explore the RNA post-transcription processing, eg. splicing, etc.
## Statistics
Negative binominal GLM, Cox-Reid Approximate Conditional Variance, 

#### General info
* RNA splicing patterns: How are genes actually transcribed and subsequently translated into proteins?
* Gene discovery: Presence of unique stretches of DNA might reveal previously undiscovered genes.
* Gene expression profiling: Expression levels of known genes can be inferred by looking at relative amounts of RNA expression.
* Profiling of miRNAs implicated in cancer
* Targeted cancer gene profiling

#### Links
* [Wikipedia](https://en.wikipedia.org/wiki/RNA-Seq)
* [Ebi](https://www.ebi.ac.uk/training/online/course/functional-genomics-ii-common-technologies-and-data-analysis-methods/applications-rna-seq)
* [Illumina](https://www.illumina.com/areas-of-interest/cancer/research/sequencing-methods/cancer-rna-seq.html)

## Methodology

#### The cDNA Library
The first step is to prepare the _cDNA library_ (using Illumina protocol):

1. RNA isolation / extraction from tissue of interest
2. Break RNA into small fragments - This can be done using liquid nitrogen and using a mortar and pestle to break it apart. It is essential to maintain the integrity of the RNA in this step. It is done because the machine can only sequence 200-300 bp fragments.
3. cDNA synthesis - The RNA is now reverse transcribed to cDNA. DNA is more stable because it is **double stranded** and can be easily amplified and modified.
4. Add sequencing adaptors - This is done so the machine can recognise the fragments and sequence multiple samples at once.
5. PCR amplify
6. Quality control! - verify library concentration and library fragment lengths.


#### Sequencing
The second step is to _sequence_:

* Fragments laid out on a grid vertically
* Machine has fluorescent probes that are colour coded based on the nucleotide they bind to
* Machine takes a picture (so we know what are the first bases)
* The machine washes the first base and binds to the second base. It takes a picture again to find the second base. As such, the process is repeated till the machine determines each sequence of nucleotides
	* Scores are based on colour e.g. low quality if colour is faint
	* Also, low quality scores are given if lot of probes in the same region of the same colour (low diversity). 
	* Especially a problem at the start of the sequencing


Data looks something like: Unique ID + Bases in sequenced fragment + Quality scores

Steps to sequencing are:

1. Filter out low quality reads - either low quality base calls (discussed above) or artifacts of the chemistry (e.g. adapter sequences binding to each other).
2. Align high quality reads to genome - Fragment the reference genome and match the read fragments to the genome fragments. This will determine the location in the genome.
3. Count number of reads per gene - Once we know the chromosome and position of a read, we can see if it falls within the coordinates of a gene or any othe interesting feature e.g. Single nucleotide polymorphisms (SNPs)

In **bulk RNA-seq** a sample (6 million cells) might have 3 normal and 3 mutated samples.
In **single-cell RNA-seq** it treats each cell as an individual sample, so a lot of samples can be generated.

#### Data Analysis
The last step is _data analysis_:

* We must normalize the data first since:
	* One sample may have lower quality reads OR
	* One sample may have high concentration on the flow cell

1. Generally it is necessary to log transform the CPM (counts per million) expression data.
2. Plot the data!! e.g. PCAs, MDS. Usually the first two dimensions show the difference between normal and mutated samples. The distance on the graph shows which difference is larger i.e. PC1 distance may be larger in distinguishing the samples.
3. Identify differentially expressed genes between the normal and mutated samples
4. Conclusion: Either see if the experiment validated your hypotheses or see if certain pathways are enriched in either normal or mutatant gene sets.






