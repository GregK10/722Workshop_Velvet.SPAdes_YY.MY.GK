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
#### Here we are using two main velvet funtions ```velveth```and ```velvetg```

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
######  (```shufflereads_fasta.pl``` if your files are in fasta format)

The format is
```
shuffleReads_fastq.pl [reads_1.fastq] [reads_2.fq] [merged_output.fastq]
```
For out results, imput the following script
```
/usr/local/velvet/velvet_1.2.10/contrib/shuffleSequences_fasta/shuffleSequences_fastq.pl B4546_1s.fastq B4546_2s.fastq merged.fastq
```

### to run Velvetoptimiser using the merged file we created we will use the following script
```
/usr/local/velvet/velvet_1.2.10/contrib/VelvetOptimiser-2.2.4/VelvetOptimiser.pl -d 'velvet' -f '-fastq -shortPaired merged.fastq'
```
#### In addition to the VelvetOptimiser function, two flags are necessary. The flags require their parameter string to be encased with either '' or ""
- ```-d [directory_name]``` will create a directory for our output files
- ```-f {[-file_format][-read_type] filename}``` contains similar information to the velveth function.

#### Some details on Velvetoptimiser
- The optimisation function used for k-mer choice default 'n50' but this can be changed with the flag ```--optFuncKmer```
- This time we are just using default range of hash values (or kmer) to try of 19 to 31, with the steps being 2 (the program is trying to find the most optimal hash size)
 	-  In our workshop, the optimal hash value was determined to be 25
- The flag ```-shortPaired``` represents that illumina paired end reads are used. 
- coverage cutoff can also be set automatically to half the length weighted median contig coverage depth. Although you may wish to optimise this parameter in further iterations, this option allows you to quickly obtain a decent assembly in your first run

### The output directory contains 8 files.

29-03-2021-12-37-05_Logfile.txt  
contigs.fa  
Graph  
Graph2  
Log  
PreGraph  
Sequences  
stats.txt


### Now that we have assembled contigs using both SPAdes and Velvet, let us check out summary statistics using QUAST
















