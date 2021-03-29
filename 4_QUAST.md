# What is QUAST
Stands for **QU**ality **AS**sessment **T**ool. The tool evaluates genome assemblies by generating various quality metrics.
We will be using QUAST 3.1

### To run QUAST, we need to use the contig files that are in the output directory from both assemblers
We what to be working in our QUAST directory so the files we generate will be outputted there.
```
cd /2/scratch/NAME/first_student_workshop/quast/
```
- **Code for SPAdes**
```
cd /2/scratch/NAME/first_student_workshop/spades
python2 /usr/local/quast/version_3.1/quast.py -o test_out contigs.fasta
```
- **Code for Velvet**
```
cd /2/scratch/NAME/first_student_workshop/velvet
python2 /usr/local/quast/version_3.1/quast.py -o test_out contigs.fa
```
Python is the language we will use for our workshop. QUAST capable of using others as well (such as perl).
For both codes, the flag ```-o [filename]``` will create an output file under the name we prodvide 
```contigs.fasta``` and ```contigs.fasta``` are the contig files for SPAdes and Velvet respectively.



