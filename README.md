# TF
Bioc Breseq for Tom Finn

>Log into the bioc server via command line/terminal - It just occurred to me that breseq is now installed on biochemcompute . . . this will save heaps of time

> Navigate to directory containing your sequences

```bash
cd ~/path/to/sequences/

```

>Trim files using Trimmomatic - This is if you do not trust what NZGL has trimmed, personally i prefer to have control of all this myself

```bash
java -jar /usr/local/bin/Trimmomatic-0.35/trimmomatic-0.35.jar PE -threads 20 -phred33 sample_read1.fastq.gz \
sample_read2.fastq.gz output1_forward_paired.fq.gz output1_forward_unpaired.fq.gz \
output1_reverse_paired.fq.gz output1_reverse_unpaired.fq.gz \
ILLUMINACLIP:/usr/local/bin/Trimmomatic-0.35/adapters/TruSeq3-PE.fa:2:30:10 LEADING:5 TRAILING:5 SLIDINGWINDOW:4:20 MINLEN:20

```

> Run BREseq on TRIMMED samples (Even raw samples can work with Breseq - i just prefer to trim first).

```bash
breseq -j 100 -r REFERENCE.gbff -o sampleX_output output1_forward_reads.fastq.gz output1_reverse_reads.fastq.gz

```

>outputs will be in sampleX_output/output/summary.html - enjoy. Sam
