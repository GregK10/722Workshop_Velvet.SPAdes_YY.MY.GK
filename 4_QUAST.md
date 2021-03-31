# What is QUAST
Stands for **QU**ality **AS**sessment **T**ool. The tool evaluates genome assemblies by generating various quality metrics.
We will be using QUAST 3.1

### To run QUAST, we need to use the contig files that are in the output directory from our assemblers
### QUAST runs from a command line as follows: 
```
python2 quast.py -o [new_directory] [contig_file(s)]
```
#### The different parameters of the QUAST code are outlined below.
- ```python2``` 
    - The script language we will use for our run of QUAST. QUAST is capable of using others as well (such as perl).
- ```/usr/local/quast/version_3.1/quast.py```
    -   QUAST module
- ```-o [new_directory] ```
    - Creates the output directory that contains all output file using the name we provide. 
- ```contigs.fasta``` and ```contigs.fa``` 
    - The contig files for SPAdes and Velvet respectively
  
#### Some other options (that may or may not apply to _de novo_ assembly)
 - ```-t (or --threads) <int>```
     - Maximum number of threads. The default value is the number of CPUs. If QUAST fails to determine the number of CPUs, the number is set to 4
 - ```--scaffolds```
     - The assemblies are scaffolds (rather than contigs). QUAST will add split versions of assemblies to the comparison. Assemblies are split by continuous fragments of N's of length ≥ 10
 - ```-R <path>```
     - Reference genome file. Optional. Many metrics can't be evaluated without a reference. If this is omitted, QUAST will only report the metrics that can be evaluated without a reference

## Running QUAST
Make sure your path is as follows
```
pwd
/2/scratch/NAME/first_student_workshop
```
#### Code for QUAST on the SPAdes contig
```
python2 /usr/local/quast/version_3.1/quast.py -o quast/spades_out spades/contigs.fasta
```
#### Code for QUAST on the Velvethg contig
```
python2 /usr/local/quast/version_3.1/quast.py -o quast/velvethg_out velvet_hg/contigs.fa
```
#### Code for QUAST on the Velvetoptimiser contig
```
python2 /usr/local/quast/version_3.1/quast.py -o quast/velvet_opt_out velvet_opt/contigs.fa
```
#### Let's now move over to the quast directory
```
cd /2/scratch/NAME/first_student_workshop/quast/
```
#### We can now see that there are 3 directories containing multiple outputs. The outputs a listed below
```
basic_stats/
report_html_aux/
quast.log
report.pdf
report.html
report.txt
report.tsv
report.tex
transposed_report.tsv
transposed_report.txt
transposed_report.tex
```
### Let's open the reports created by QUAST and compare the _de novo_ assemblers compare to each other.
```
nano spades/report.txt
nano velvet_opt/report.txt
nano velvet_hg/report.txt
```
### You can copy the quast folder to your computer from the cluster by following these steps
You want to make a directory in your home directory for this to work
```
mkdir ~/first_student_workshop ; cd
cp -r  /2/scratch/NAME/first_student_workshop/quast/
```
#### To download the statistics
```
scp -r NAME@info.mcmaster.ca:~/quast/ .
```

### If you are interested in further readings, we have additional information on the 3 programs we demonstrated today, found [here](https://github.com/GregK10/722Workshop_Velvet.SPAdes_YY.MY.GK/blob/main/5_Additional_readings.md).

## We hope you all enjoyed our workshop and had FUN!

