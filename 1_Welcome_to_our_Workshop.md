
# Welcome to our workshop (2021-03-31)
**Editors: GK, YF, and MY** 

The sample we will be using in today's workshop is a _Cryptococcus gattii_ VGIII strain. Whole genome sequencing was performed at The Centre for Applied Genomics (The Hospital for Sick Children) on HiSeq X, PE150bp, with ~50 x coverage.

### Before we get into it, we want you to all be prepared

First, let's create a directory in your scratch folder. Feel free to name it whatever you like
```
cd /2/scratch/NAME/
mkdir first_student_workshop ; cd first_student_workshop/
```
Next let's create symbolic links to the two fastq files we will be working with. These are paired end reads so there are 2 files.
They have already been trimmed using ```trimmomatic``` and are all set for genome assembly.
The two fastq files (B4546_1s.fastq and B4546_2s.fastq) can be accessed from one of our scratch directories: 
```
ln -s /2/scratch/yuying/B4* .
```
These are not the full fastq files as that will take SPAdes a long to run (velvet is faster). We will only be using a random subset of 100,000 forward and reverse reads.

However, if you are interested, the full fastq files can be found in: ```/2/scratch/manyou/workshop/```

### Creating a directory for the future
While we are in our ```first_student_workshop``` directory, lets make 1 additional directory for our QUAST results.
```
mkdir quast
```
#### We are all set to run both of de novo asemblers. Click [here](https://github.com/GregK10/722Workshop_Velvet.SPAdes_YY.MY.GK/blob/main/2_SPAdes.md) to assemble a genome using SPAdes! We are just getting started :)
