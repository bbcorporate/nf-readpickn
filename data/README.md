## get a sample Illumina readset
wget ftp://webdata:webdata@ussd-ftp.illumina.com/Data/SequencingRuns/MG1655/MiSeq_Ecoli_MG1655_110721_PF_R1.fastq.gz
wget ftp://webdata:webdata@ussd-ftp.illumina.com/Data/SequencingRuns/MG1655/MiSeq_Ecoli_MG1655_110721_PF_R2.fastq.gz

## shorten the reads so it runs faster
gzcat MiSeq_Ecoli_MG1655_110721_PF_R1.fastq.gz | head -n 400000 > trunc400K_MiSeq_Ecoli_MG1655_110721_PF_R1.fastq
gzcat MiSeq_Ecoli_MG1655_110721_PF_R2.fastq.gz | head -n 400000 > trunc400K_MiSeq_Ecoli_MG1655_110721_PF_R2.fastq
gzip *.fastq

## erase the downloaded readsets cuz they're 1G
rm MiSeq_Ecoli_MG1655_110721_PF_R1.fastq.gz MiSeq_Ecoli_MG1655_110721_PF_R2.fastq.gz

