# What is QUAST
Stands for **QU**ality **AS**sessment **T**ool. The tool evaluates genome assemblies by generating various quality metrics.
We will be using QUAST 3.1

### To run QUAST, we need to use the contig files that are in the output directory from both assemblers
For organization, we want our contig.fasta outputs to be placed in our QUAST directory. Let's change to our working directory. Please make the quast directory if you have not done so already.

```
cd /2/scratch/NAME/first_student_workshop; mkdir quast;
```
#### The different parameters of the QUAST code are outlined below.
'''python quast.py [options] <contig_file(s)>'''

- ```python2``` 
    - The scipt language we will use for our run of QUAST. QUAST is capable of using others as well (such as perl).
- ```/usr/local/quast/version_3.1/quast.py```
    -   QUAST module
- ```-o [new_directory] ```
    - Creates the output directory that contains all output file using the name we provide. 
- ```contigs.fasta``` and ```contigs.fa``` 
    - The contig files for SPAdes and Velvet respectively

### Code for QUAST on the SPAdes contig
Make sure your path is as follows
```
pwd
$ /2/scratch/NAME/first_student_workshop
```
Then input the following scripts
```
python2 /usr/local/quast/version_3.1/quast.py -o quast/spades_out spades/contigs.fasta
```
### Code for QUAST on the Velvet contig
```
python2 /usr/local/quast/version_3.1/quast.py -o quast/velvet_out velvet/contigs.fa
```
#### Let's now move over to the quast directory
```
cd /2/scratch/NAME/first_student_workshop/quast/
```
#### We can now see that there are 2 directories containing multiple outputs.
Let's copy this directory over to our home folder so we can download the results onto our own machines
```
mkdir ~/first_student_workshop ; cd
cp -r  /2/scratch/NAME/first_student_workshop/quast/
```
#### To download the statistics
```
scp -r NAME@info.mcmaster.ca:~/quast/ .
```
We can open them now and see how our two de novo assemblers look and compare to each other.

#### If you are interested in further readings, we have additional information on the 3 programs we demonstrated today, found [here](https://github.com/GregK10/722Workshop_Velvet.SPAdes_YY.MY.GK/blob/main/5_Additional_readings.md).
### We hope you all enjoyed our workshop and had some fun!

