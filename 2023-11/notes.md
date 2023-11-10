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

# Tuesday Nov 7th 2023  

Update: found Mehran's Polyidus integrations in Supp Table 1, although I do not think this is the raw output.  
HeLa-S3 run worked! But I ran it using HPV16 by accident (Mehran's table + literature shows that this is actually an HPV18 infected sample). Re-running using HPV18.  
Downloaded HPV18 genome from: https://www.genome.jp/entry/-f+refseq+NC_001357  
Downloaded Si-Ha RNA-seq datasets from https://www.ncbi.nlm.nih.gov/bioproject/PRJNA663801  
One additional change I made was to make sure the bwa indices were pre-made and in the same directory as the genomes. It turns out that it takes HOURS to index hg38.  
Met with Emma Collier (Bratman lab) to discuss her project and viral integration tools that she uses.  
Started putting together my slides for Thursday.  

# Wednesday Nov 8th 2023  

Trying to download the CasKi dataset as well. Running into a lot of issues, it keeps timing out, do not think that I will have it ready in time.  
Put together my slides.  
Class in the afternoon. 

# Thursday Nov 9th 2023  

Class in the morning. 
Did some final presentation prep.  

# Friday Nov 10th 2023  

Focus today is on clean-up and documentation.  

To do: 
- [ ] Delete fastqs?
- [ ] Write-up note of what I did and where all the directories are  
- [ ] Check directory permissions
- [ ] Move notebook to Valinor

Notebook link: https://github.com/hoffmangroup/nour  

