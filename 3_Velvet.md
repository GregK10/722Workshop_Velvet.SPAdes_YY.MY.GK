# Introduction to Velvet

Similar to SPAdes, Velvet is a de novo assembler designed for short reads. Velvet removes errors present within these reads and then assembles them in to contigs. 
##### Imput files can be
- Fasta
- FastQ
- sam 
- bam 
 
##### Input formats it takes:

- Illumina Paired-end reads, mate-pairs and single reads
- IonTorrent
- PacBio
- Oxford Nanopore
- Sanger
 
 Velvet is useful as it can produce long contigs in excess of 150kb from paired end short reads
 
 ## Velvet Workshop
 
Similar to SPAdes, the code to run Velvet is straightforward
 
```
velveth velvet_31 31 -shortPaired -fastq -separate ../B4546_1.fastq ../B4546_2.fastq
velvetg velvet_31 -cov_cutoff auto
```
##### Here we are using two main velvet funtions ```velveth```and ```velvetg```

- ```Velveth``` reads sequence files and builds a dictionary of all words of length k, where k is the default max hash value of 31, thus defining exact local alignments between the reads. Analyzes kmers in the reads in preparation for assembly
- ```Velvetg``` reads the alignments produced by ```Velveth```, builds a de Bruijn graph from them, removes errors and simplifies the graph and resolve repeats. Constructs the assembly and filters contigs from the graph

##### Flags for ```velveth```
- ```velvet_31``` is the file name for the dictionary
- ```-shortpaired``` is the type of reads we are using
- ```-fastq``` is read type file
- ```-separate```  read1 and read2 are in separate files. Might be a useless flag

##### Flags for ```velvetg```

## Velvetoptimiser 
Now we want to optomize our velvet runs using Velvetoptimiser. It searches a supplied hash value range (k-mer size) for the optimum, estimates the expected coverage and then searches for the optimum coverage cutoff. It does this by performing many runs of Velvet. 

#### But first we need to merge the two fastq files together as velvetoptimizer will only takes this single merged file as input
We want each read paired with the one directly above or the one directly below

To merge the two fastq files that we have, we will use the ```shufflereads_fastq.pl```, a command that is included with Velvet




















