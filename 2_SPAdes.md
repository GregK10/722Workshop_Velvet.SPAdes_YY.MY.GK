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
