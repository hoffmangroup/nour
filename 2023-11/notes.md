# Monday Nov 6th 2023  

Figured out the Snakemake error today - the fastq.gz files do not have the same prefix, this causes issues for the automatic sample name recognition.  

This is the failed dry-run output that I would get:  

<img width="1030" alt="Screen Shot 2023-11-06 at 11 08 49 AM" src="https://github.com/hoffmangroup/nour/assets/67124068/81fca4d2-17b3-4b1d-9c25-236300b1b8ee">  

When instead I expected a DAG like this:  


<img width="528" alt="Screen Shot 2023-11-06 at 11 10 00 AM" src="https://github.com/hoffmangroup/nour/assets/67124068/d2d2435d-b280-474a-b79a-d9cd8a85ac65">

So I tracked back through the config, changing line by line. Issue materialized at this [line](https://github.com/aehrc/isling/blob/ee32e24891a99d00af988e24538847a82a74d31c/test/config/test.yml#L7C1-L7C1)  

Also - for mysterious reasons the fastq files must be uncompressed for input! Pipeline failed otherwise (although look into this later, might be a consequence of me renaming the fastq.gz to .fastq during my troubleshooting for the above issue).  

Mehran's HeLa-S3 Polyidius results can be found here for comparison:  /mnt/work1/users/hoffmangroup/mkarimzadeh/2019/hpvCTCF/HeLa-S3/RNA-seq/polyidus  
Can't find them in the published datasets.  

Found Mehran's Polyidius integrations in supplemental table 1 of the paper.  

Fixed the Pysam Polyidus module issue: downgrading to pysam/0.11.1 restores compatibility with python3/3.7.2  


