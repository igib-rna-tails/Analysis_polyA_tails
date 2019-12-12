## Analysis of Poly A/U RNA tails from RNA-Seq data

The notebook contains the workflow of Poly A RNA tails analysis. It's created for genome of fission yeast (Schizosaccharomyces pombe) - RNA-Seq data. The main aim is detection and analysis of 3' tails of mRNA.

Steps:
1. Extract unmapped reads from bam files.
2. Convert the bam file into fastq.
3. Merge all of technical/biological repetition - merge fastq files.    
4. Extract only the reads containing at least 10 A or U an 3' tail of RNA.    
5. Use cutadapt to cut the 3' tail of RNA.
6. Mapping of cutadapted reads using HiSat2.   
7. Convert mapped reads (new sam file) into bam, bed.
8. Make bw file from bam.  
9. Use deeptools to visualize the results: computeMatrix and plotProfile.



In order to run locally:

conda create --name rnatails python=3.7

conda install -c bioconda seqkit fastqc je-suite HISAT2 samtools bedops rseqc htseq cutadapt


conda activate rnatails
pip install numpy==1.17.3
pip install matplotlib==3.0.3
pip install opencv-python-headless
conda install jupyter
conda install -c anaconda openjdk
jupyter-notebook
# Analysis_polyA_tails
