# Wednesday October 18th, 2023  
Made a GitHub repo today that will serve as my lab notebook for now, may move it to valinor later.  
Waiting for valinor access.  
Did more onboarding stuff (calendar/email/GitHub/shared group folder setup and access).
Reading HPV integration paper in more detail. 
Ethics class.

Questions:  
- "We identified HPV integration in each sample using the sequence of the dominant HPV type in that sample." <- does this mean that you have to know the sequence ahead of time, before running Polyidus?
- -> All samples were the same HPV?? Unsure, double check this in paper.

# Thursday October 19th, 2023  
Continued going through the paper, and tracking down the datasets.    
Looked through some of Mehran's data directories.  


## Questions:  
- Why did you use RNA-seq for identifying integration sites? Like why not genomic data?
- -> There is no genomic data available apparently.
- Can I work from home tomorrow? (WFH policy in general?)
- -> Yes for tomorrow. WFH in general to be asked at a later time.
- Any good example of software I can look at?
- -> Did not ask. 
- Lab meeting conflict next week
- -> Email Natalia
- Presenting next Wednesday? How long should the presentation be?
- -> Max 25 mins
- Valinor?
- -> Forwarded email again
- Should I replicate entire paper, or focus on Polyidus parts?
- -> Just Polyidus
- H4H instead?
- -> Did not ask

## Notes from meeting:  
DNAseq vs RNAseq differences -> see if you can find genomic data for cell lines, and redo analysis using that instead, see what you find. 
Email Natalia -> CC Michael, lab meeting can't be before Wednesday -> MH can send slides of this project from before (max 25 mins)
Email MH directly about finding meeting time next week  


# Monday/Tuesday October 23rd/24th, 2023
Mostly worked on getting my slides ready, read up on oncogenic viral integration.  
Class work  

# Wednesday October 25th, 2023
Read the Isling paper Mehran had suggested.  
Worked through some of the codebase to try to understand exactly how the major steps were performed.  
Put together my slides.  
Installed Polyidius, but ran into this error, which happens when I try to run Polyidius but also when I do module load pysam:  

    Lmod has detected the following error:  The following module(s) are unknown: "python3/3.7.0"

    Please check the spelling or version number. Also try "module spider ..."
    It is also possible your cache file is out-of-date; it may help to try:
    $ module --ignore-cache load "python3/3.7.0"
    
    Also make sure that all modulefiles written in TCL start with the string #%Module
    
    Executing this command requires loading "python3/3.7.0" which failed while processing the following module(s):
    
    Module fullname  Module Filename
    ---------------  ---------------
    pysam/0.15.1     /mnt/work1/software/centos7/modulefiles/pysam/0.15.1.lua
    While processing the following module(s):
    Module fullname  Module Filename
    ---------------  ---------------
    pysam/0.15.1     /mnt/work1/software/centos7/modulefiles/pysam/0.15.1.lua  

# Thursday October 26th, 2023  
Based on feedback from my presentation, will change gears and download Isling, and use that to replicate Mehran's work instead, since it seems to be overall better in speed and accuracy.  

Repo: https://github.com/aehrc/isling
Install and test commands I used:  

    git clone https://github.com/aehrc/isling.git && cd isling
    snakemake --configfile test/config/test.yml --use-conda --conda-frontend conda --cores 1
    
Needed to specify --conda-frontend because by default it sounds like it uses mamba, a faster alternative to conda, but I don't know where to get that from.  

# Monday October 30th, 2023  
Looked through Mehran's www directories - found HeLa-S3 RNA dataset. 
Set up a snakemake dataset with this dataset. Also downloaded human reference genome (hg38), HPV 16 and ENCODE blacklisted regions v2 for the run. 
Run works for test dataset but not the HeLa-S3. I repeatedly get a variation of this error:

    InputFunctionException in line 43 of /mnt/work1/users/hoffmangroup/nhanafi/isling/snakemake_rules/find_ints.smk:
     Error:
    ValueError: attempt to get argmax of an empty sequence

Expanded error:

    InputFunctionException in line 43 of /mnt/work1/users/hoffmangroup/nhanafi/isling/snakemake_rules/find_ints.smk:
      Error:
    ValueError: attempt to get argmax of an empty sequence
    Wildcards:
      outpath=out/HeLa-S3
      dset=test-merge
      samp=ENCFF000FSU_NuclearRNA_HeLa-S3
      host=hg38
      virus=hpv16
    Traceback:
      File "/mnt/work1/users/hoffmangroup/nhanafi/isling/snakemake_rules/find_ints.smk", line 46, in <lambda>
      File "/mnt/work1/users/hoffmangroup/nhanafi/isling/snakemake_rules/preprocessing.smk", line 93, in get_split
      File "/mnt/work1/users/hoffmangroup/nhanafi/isling/snakemake_rules/preprocessing.smk", line 49, in get_value_from_df
      File "/mnt/work1/software/centos7/python/3.8.2/lib/python3.8/site-packages/pandas/core/series.py", line 2404, in idxmax
      File "/mnt/work1/software/centos7/python/3.8.2/lib/python3.8/site-packages/pandas/core/base.py", line 657, in argmax
      File "/mnt/work1/software/centos7/python/3.8.2/lib/python3.8/site-packages/pandas/core/nanops.py", line 93, in _f
      File "/mnt/work1/software/centos7/python/3.8.2/lib/python3.8/site-packages/pandas/core/nanops.py", line 1096, in nanargmax

I suspect I forgot to define a variable/wildcard somewhere. Working on debugging this. 


HPV16 genome from: https://www.ebi.ac.uk/ena/browser/view/K02718  
hg38 from: [https://genome.ucsc.edu/cgi-bin/hgTracks?db=hg38&lastVirtModeType=default&lastVirtModeExtraState=&virtModeType=default&virtMode=0&nonVirtPosition=&position=chr2%3A130592165%2D130599575&hgsid=1741388240_6bTMIFMAufhfDiaBCe4r37ZJVXVu](https://hgdownload.soe.ucsc.edu/goldenPath/melGal5/bigZips/)
ENCODE blacklisted regions from UCSC table browser.


Next steps: priority is to get a run going on HeLa-S3, and other datasets from the paper as well, and do a comparison of the called integration sites. 
