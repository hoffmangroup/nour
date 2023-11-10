# Write-up of the work done during my rotation in the Hoffman Lab from Oct 16th to Nov 10th   

At the start of my rotation project, I was aiming to replicate Mehran's HPV integration paper results using Polyidus, the tool he developed, and get it publication-ready. 
However, a paper was released in 2022, benchmarking Polyidus against a new tool called Isling. Isling appeared to perform better in terms of accuracy and speed than Polyidus. 
So, I changed my project to instead install Isling and try it out.  

Main directory: `/mnt/work1/users/hoffmangroup/nhanafi`  

Polyidus installed here: `/mnt/work1/users/hoffmangroup/nhanafi/polyidus`  
Isling installed here: `/mnt/work1/users/hoffmangroup/nhanafi/isling`  
Input datasets used to be installed here (deleted fastqs to save space) + install script and sample metadata: `/mnt/work1/users/hoffmangroup/nhanafi/data`  

Isling results found here: `/mnt/work1/users/hoffmangroup/nhanafi/isling/out`  

"pipeline-test" refers to the in-built test that Isling provided.  
"HeLa_hpv16_results" refers to a run with HeLa-S3, incorrectly using HPV16.  
"HeLa-S3" refers to a run with HeLa-S3, correctly using HPV18.  
"Si-Ha2" refers to a run with SiHa-2, using HPV18.  
"Si-Ha3" refers to a run with SiHa-3, using HPV18.  

I am not actually sure what the distinction between the 2 Si-Has are. Both were selected because they were sequenced using Illumina NextFlow, as were the RNA datasets from Mehran's paper, I believe.  

sbatch script to run isling is here: `/mnt/work1/users/hoffmangroup/nhanafi/isling/run_isling.sh`  

Isling Github:  https://github.com/aehrc/isling/tree/master  




