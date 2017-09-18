GSAlign: a large genome sequence alignment tool with Burrows-Wheeler Transform
===================

Developers: Dr. Hsin-Nan Lin and Dr. Wen-Lian Hsu Institute of Information Science, Academia Sinica, Taiwan.

# Introduction

Personal genomics and comparative genomics are two fields that are more and more important in clinical practices and genome researches. Both fields require sequence alignment to discover sequence conservation and structural variation. Though many methods have been developed to handle genome sequence alignment, some are designed for small genome comparison while some are not efficient for large genome comparison. Here, we present GSAlign to handle large genome comparison efficiently. GSAlign includes three unique features: 1) it is the first attempt to use Burrows-Wheeler Transform on genome sequence alignment; 2) it supports parallel computing; 3) it adopts a divide-and-conquer strategy to separate a query sequence into regions that are easy to align and regions that require gapped alignment. With all these features, we demonstrated GSAlign is very efficient and sensitive in finding both the exact matches and differences between two genome sequences and it is much faster than existing state-of-the-art methods. 

# Download

Current version: 2.3.0. Please use the command 
  ```
  $ git clone https://github.com/hsinnan75/GSAlign.git
  ```
to download the package of Kart.

# Compiling

To compile GSAlign and the index tool, please change to GSAlign's folder and just type 'make' to compile GSAlign and bwa_index. If the compilation or the programs fail, please contact me (arith@iis.sinica.edu.tw), Thanks.

# Changes

version 0.9.0: First release version.

# Instructions

For indexing a reference genome, GSAlign requires the target genome file (in fasta format) and the prefix of the index files (including the directory path).

  ```
  $ ./bwa_index ref_file[ex.ecoli.fa] index_prefix[ex. Ecoli]
  ```
The above command is to index the genome file Ecoli.fa and store the index files begining with ecoli.

If the index files are not mdade beforehand, GSAlign will generate index files istself with the given reference genome sequences.

# Datasets

You may download test datasets at http://bioapp.iis.sinica.edu.tw/~arith/GSAlign/ to test the performance of GSAlign.
The dataset contains four simulated human genome sequences with 0.1%, 0.2%, 0.5%, and 1% of mutation rates, respectively. It also contains the corresponding VCF file listing the variants between the hg38 genome and the mutant ones.
You can also use the evaulation tool (Evaluation.cpp) to measure the precision and recall of the resulting VCF files. 
To compile Evaluation.cpp, just type 'g++ Evaluation.cpp -o eva'

# File formats

- Reference and query genome files

    Both the reference genome and query genome files should be in FASTA format.

- Output file

	1. aln file: it shows the pairwise alignments between the two genomes.
	2. vcf file: it shows the sequence variants between the two genomes (standard VCF format).
	3. ps  file: it shows the dotplot between two chromosomes (gnuplot is required).
	4. snp file: it shows all the SNPs of the query genome (compared to the reference genome).
	5. ind file: it shows all the insertions and deletions of the query genome (compared to the reference genome).

All above file formats are in text mode.

# Parameter setting

 ```
-t INT number of threads [16]

-i STR index prefix [BWT based (BWA)]

-r STR reference genome filename [fasta]

-q STR query genome filename [fasta]

-sub output the identified SNPs

-ind output the identified indels

-o STR prefix of output files

  ```
