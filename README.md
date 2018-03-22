## BALDR

BALDR is a pipeline for reconstructing human or rhesus macaque immunoglobulin(Ig)/B cell receptor(BCR) sequences from single cell RNA-Seq data generated by Illumina sequencing. 

BALDR is based on the *de novo* assembly of RNA-Seq reads. It allows reconstructions using following methods:
1. Unfiltered (human and rhesus) - Use all reads for assembling transcripts and select Ig transcript models
2. IG-mapped_only (human and rhesus) - Assemble reads mapping to Ig loci
3. IG-mapped_Unmapped (human and rhesus) - Assemble reads mapping to Ig loci + Unmapped reads
4. IMGT-mapped (human) - Assemble reads mapping to IMGT V(D)J and C sequences
5. Recombinome-mapped (human) - Assemble reads mapping to the Ig recombinome
6. FilterNonIG (rhesus)- Assemble reads after filtering those that match to non-Ig genes in the genome

## Pre-requisites
1. [Trimmomatic 0.32](http://www.usadellab.org/cms/?page=trimmomatic)
2. [Trinity v2.3.2 or later](https://github.com/trinityrnaseq/trinityrnaseq/wiki) 
3. [bowtie2 2.3.0](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml)
4. [STAR v2.5.2b](https://github.com/alexdobin/STAR)
5. [samtools v1.3.1](http://www.htslib.org/download/)
6. [IgBLAST v1.6.1](https://www.ncbi.nlm.nih.gov/igblast/faq.html#standalone)
7. [seqtk 1.2](https://github.com/lh3/seqtk)
8. Perl 5

## Installation
Clone or download the BALDR package. 
```
cd BALDR
chmod +x BALDR
```

## Command line usage
```
Single-end:
./BALDR --single <file.fastq.gz> <options>

Paired-end:
./BALDR --paired <R1.fastq.gz,R2.fastq.gz> <options>

Options:
  --method       One or more reconstruction methods. For multiple methods, separte only by comma
  	    	 human: IG-mapped_Unmapped (default), Unfiltered, IG-mapped_only, IMGT-mapped, Recombinome-mapped 
  		 rhesus_monkey: FilterNonIG (default), Unfiltered, IG-mapped_only, IG-mapped_Unmapped
  --organism     human (default) or rhesus_monkey
  --trimmomatic  Path for trimmomatic.jar file (e.g. ~/Trimmomatic-0.36/trimmomatic-0.36.jar) (required)
  --adapter      Path for the Trimmomatic adapter file (e.g. ~/Trimmomatic-0.36/adapters/NexteraPE-PE.fa) (required)
  --STAR_index   Path for the STAR aligner genome index
  --BALDR        Path for the BALDR directory (e.g. ~/BALDR) (required)
  --memory       Max memory for Trinity (default 32G)
  --threads      number of threads for STAR/bowtie2/Trinity (default 1)
  --version      Version
  --help         Print this help
```


