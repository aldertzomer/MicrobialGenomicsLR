---
start: false
title: "Sequence Read Quality Lecture"
exercises: 5
teaching: 20
questions:
- "How does sequencing work"
- "Where do the errors come from"
objectives:
- "Recap sequence data quality"
- "Understanding read data"
keypoints:
- "Determining sequence quality of reads"
---

## Sequencing quality

Next up is a presentation on sequence read quality and sequencing methods. Here are the [slides](https://klif.uu.nl/klif/mgen/MicrobialGenomics_sequencingQuality_Linda.pdf) .

If you are following this course on your own you can make use of a [pre-recorded lecture](https://www.youtube.com/watch?v=sdxVDy0lSAE) by Professor Bas Dutilh, from Theoretical Biology and Bioinformatics at UU and Jena University in Germany.

The lecture will take approximately 20 minutes. After that there is time for asking questions.

Checking the Nanopore sequencing quality can be done using [NanoStat](https://github.com/wdecoster/nanostat). It generates a quick summary of the number of bases, the number of reads, the length of the reads and the quality of the reads. In general we expect about 30x more bases than the size of the genome and a mean read length of >3kb. The quality can range between 11 and 18 depending on the sequencing kit, flowcell, basecalling model used.

```
$ conda activate genomics # check your environment. Most software is in genomics, but some tools have their own environment.
$ conda env list # check which environments you have. If the commandline says it can't find a program, activate the correct environment.
$ cd ~/reads
$ NanoStat --fastq barcode02.fastq
$ NanoStat --fastq barcode03.fastq
```

Record the _number of bases_, the _estimated sequencing depth_ (number of bases divided by expected size of the genome) and the _mean read length_ in the [Google Docs file](https://docs.google.com/spreadsheets/d/1ImRY5QPblAv_LZrwCkHGQOKdyYQ4XHkvtYl9k8UNoKI/edit?gid=0#gid=0). Assume the genome size to be 5Mb.

Sometimes the Nanopore output is really high. [Filtlong](https://github.com/rrwick/Filtlong) can be used to reduce the amount of read data to more manageable levels. Using this command we reduce the expected coverage to about 100x. This is not necessary in the example data for this course.

```
$ cd ~/reads
$ filtlong -t 550000000 barcode02.fastq >filtered.barcode02.fastq
$ filtlong -t 550000000 barcode03.fastq >filtered.barcode02.fastq
```


{% include links.md %}
