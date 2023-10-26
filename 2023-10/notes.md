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

