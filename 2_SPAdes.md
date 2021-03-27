# SPAdes

## Introduction
SPAdes (**S**aint **P**etersburg **A**ssembler) is a genome assembly algorithm which was designed orginally for single cell assembly but turned out to work well for multi-cell isolates too. It was intended for prokaryotic genomes but was developed later on to accommodate larger eukaryotic genomes.

SPAdes is not suitable for use with larger genomes (e.g. mammalian size genomes).

Input formats it takes: 
- Illumina Paired-end reads, mate-paires and single reads 
- IonTorrent
- PacBio
- Oxford Nanopore
- Sanger

**The overall assembly process:**

Original Reads --------------> Corrected Reads --------------> Simplified De Bruijn Graph --------------> Contigs --------------> Final Contigs
               Error Correction           De Bruijn Graph Processing                     Repeat Resolution        Postprocessing



