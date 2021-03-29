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
- ```--pe1-1 [file]``` is the file with left reads for paired-end library number. In our workshop we use ```B4546_1s.fastq```
- ```--pe1-2 [file]``` is the file with right reads for paired-end library number. In our workshop we use ```B4546_2s.fastq```
- ```--careful``` is a flag for illumina reads that minimizes number of mismatches and short indels in the final contigs. Also runs MismatchCorrector – a post processing tool, which uses BWA tool (comes with SPAdes). This option is recommended only for assembly of small genomes
- ```-o spades``` is the output file

### Understanding the SPAdes Output
SPAdes creates its own directory in your current directory. There are many outputs that are created and we have listed them below
```
assembly_graph.fastg
assembly_graph_with_scaffolds.gfa
before_rr.fasta
contigs.fasta
contigs.paths
corrected/
dataset.info
input_dataset.yaml
K21/
K33/
K55/
K77/
misc/
mismatch_corrector/
params.txt
scaffolds.fasta
scaffolds.paths
spades.log
tmp/
warnings.log
```
```
    scaffolds.fasta – resulting scaffolds (recommended for use as resulting sequences)
    contigs.fasta – resulting contigs
    assembly_graph.fastg – assembly graph
    contigs.paths – contigs paths in the assembly graph
    scaffolds.paths – scaffolds paths in the assembly graph
    before_rr.fasta – contigs before repeat resolution

    corrected/ – files from read error correction
        configs/ – configuration files for read error correction
        corrected.yaml – internal configuration file
        Output files with corrected reads

    params.txt – information about SPAdes parameters in this run
    spades.log – SPAdes log
    dataset.info – internal configuration file
    input_dataset.yaml – internal YAML data set file
    K<##>/ – directory containing intermediate files from the run with K=<##>. These files should not be used as assembly results; use resulting contigs/scaffolds in files mentioned above.
```

#### Now we have the SPAdes output ready. Now we will be assembling the genome using Velvet. 


