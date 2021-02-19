# Bioinformatic one-liners:

Determine length of reads in BAM file:
> `samtools view file.bam | head -n 1000000 | cut -f 10 | perl -ne 'chomp;print length($_) . "\n"' | sort | uniq -c`

Determine number of reads in fastq file:
> `cat file.fq | echo $((`wc -l`/4))`

Determine read length in fastq file:
> `cat reads.fastq | awk '{if(NR%4==2) print length($1)}' | sort -n | uniq -c > read_length.txt`

Filter out reads with certain length (e.g. >30):
> `samtools view -h /path/to/sample.bam | awk 'length($10) > 30 || $1 ~ /^@/' | samtools view -bS - > filter.bam`
