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
```
velvetg velvet_31 -cov_cutoff auto
```
