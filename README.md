# MyGenome
Analysis for CS485G genome assembly
Professor Mark Farman

## 1. Analysis of sequence quality
The F1 and R1 sequence datasets were analyzed using FASTQC:
```bash
ssh -Y kcga230@kcga230.cs.uky.edu
cd MyGenome
fastqc &
```
Load in F1 and R! datasets into GUI interface.
Take screen shots of the output files:
!(/data/Screenshot%2024-02-22%20140540.png).
!(/data/Screenshot%2024-02-27%143852.png").

## 2. Ran trimmomatic
```bash
java -jar ~/assembly/trimmomatic-0.38.jar PE -threads 2 -phred33 -trimlog UFVPY198_errorlog.txt UFVPY198_1.fq.gz UFVPY198_2.fq.gz UFVPY198_1_paired.fq.gz UFVPY198_1_unpaired.fq.gz UFVPY198_2_paired.fq.gz UFVPY198_2_unpaired.fq.gz SLIDINGWINDOW:20:20 MINLEN:120
```

## 3. Count number of forward reads remaining
```bash
zgrep '' UFVPY198_1_paired.fq.gz | awk 'NR%2==0' | awk '{total += length($0)} END {print total/2}'
```
