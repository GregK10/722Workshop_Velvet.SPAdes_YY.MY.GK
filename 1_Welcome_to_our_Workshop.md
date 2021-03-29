
# Welcome to our workshop (2021-03-31)
Editors: GK, YF, and MY 

### Before we get into it, we want you to all be prepared

First, let's create a directory in your scratch folder. Feel free to name it whatever you like
```
mkdir first_student_workshop ; cd first_student_workshop/
```
Next let's create symbolic links to the two fastq files we will be working with. These are paired end reads so there are 2 files.
They have already been trimmed and are all set for genome assembly.
The 2 Fastq files can be accessed from one of our scratch directories.
```
ln -s /2/scratch/yuying/B4* .
```
These are not the full fastq files as that will take SPAdes too long to run (velvet is faster). We will only be using a random subset of 100,000 forward and reverse reads.

### Creating some directories
While we are in our ```first_student_workshop``` directory, lets make 2 additional directories for our output files from both asspeblers, as well as a directory for our QUAST analysis.
```
mkdir velvet_out; mkdir quast
```
#### We are all set to run both of de novo asemblers. Click [here](https://github.com/GregK10/722Workshop_Velvet.SPAdes_YY.MY.GK/blob/main/2_SPAdes.md) to assemble a genome using SPAdes!

