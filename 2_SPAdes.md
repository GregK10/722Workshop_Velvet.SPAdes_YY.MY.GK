# SPAdes

## Introduction
SPAdes (**S**aint **P**etersburg **A**ssembler) is a genome assembly algorithm which was designed orginally for single cell assembly but turned out to work well for multi-cell isolates too. It was intended for prokaryotic genomes but was developed later on to accommodate larger eukaryotic genomes.

SPAdes is not suitable for use with larger genomes (e.g. mammalian size genomes).

Input formats it takes: 
- Illumina Paired-end reads, mate-pairs and single reads 
- IonTorrent
- PacBio
- Oxford Nanopore
- Sanger

**The overall assembly process:**

```
Original Reads --------------> Corrected Reads --------------> Simplified De Bruijn Graph --------------> Contigs --------------> Final Contigs
               Error Correction           De Bruijn Graph Processing                     Repeat Resolution        Postprocessing
```

## Workshop

Running SPAdes is pretty straigtforward.
```
/usr/local/spades/bin/spades.py --pe1-1 B4546_1s.fastq --pe1-2 B4546_2s.fastq --careful -o spades
```
#### The funtions and flags are decribed below
- ```/usr/local/spades/bin/spades.py``` is the spades function
- ```--pe1-1 [file]```                  is the file with left reads for paired-end library number. In our workshop we use ```B4546_1s.fastq```
- ```--pe1-2 [file]```                  is the file with right reads for paired-end library number. In our workshop we use ```B4546_2s.fastq```
- ```--careful``` is a flag for illumina reads that minimizes number of mismatches and short indels in the final contigs. Also runs MismatchCorrector – a post processing tool, which uses BWA tool (comes with SPAdes). This option is recommended only for assembly of small genomes
- ```-o spades``` is the output file
