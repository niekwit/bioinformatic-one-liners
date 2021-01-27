# Bioinformatic one-liners:

Determine length of reads in BAM file:
`samtools view file.bam | head -n 1000000 | cut -f 10 | perl -ne 'chomp;print length($_) . "\n"' | sort | uniq -c`
