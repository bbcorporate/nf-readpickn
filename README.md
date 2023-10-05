## Simple Nextflow script to truncate FASTQ files ##

This is intended to be a super-simple positive control example for running Nextflow in a Docker container

Take the first N reads of a pair of FASTQ files and output truncated FASTQ files.
This provides a simple way to get a small testset of reads

based on:
https://stackoverflow.com/questions/69010242/nextflow-how-should-i-truncate-a-fastq-file-at-line-x-process-fails-with-error

To retrieve any images from ECR, you need to authenticate first.  Note that this is not needed to run the example below
```
export AWS_ACCOUNTNO='insert_here'
aws ecr get-login-password --region us-west-1 | docker login --username AWS --password-stdin $AWS_ACCOUNTNO.dkr.ecr.us-west-1.amazonaws.com
```

usage:
```
nextflow run readpickn/main.nf -with-docker [nextflow-image] --datadir [path or s3 folder uri] --outdir [path or s3 folder uri]
```

more specific usage example is below.  See ./data/README.md to first get dataset
```
rm -fR results/ work/ .nextflow/ .nextflow.log*
nextflow run https://github.com/bbcorporate/nf-readpickn -with-docker quay.io/biocontainers/pysam:0.16.0.1--py37hc334e0b_1 --datadir ./data/
```
this creates a results/ directory and dumps reads to it

