# Analysis of Poly A/U RNA tails from RNA-Seq data

The notebook contains the workflow of analysis of Poly A tails of mRNA. It's directed for the genome of fission yeast (*Schizosaccharomyces pombe*) - RNA-Seq data.
The **main aim** is the detection and analysis of 3' tails of mRNA.


### Input:
    data in bam format from RNA-Seq (data from HiSeq)


### Steps:
    1. Extract unmapped reads from bam files.
    2. Convert the bam file into fastq.
    3. Merge all of the technical/biological repetition - merge fastq files.    
    4. Extract only the reads containing at least 6 A or U an 3' tail of RNA.    
    5. Remove the polyA/U tails from the 3' tail of RNA, and move the tails to the header.
    6. Do mapping using HiSat2.   
    7. Convert mapped reads (the sam file) into bam, bed.   
    8. Make bw file from bam.  
    9. Use deeptools to visualize the results: computeMatrix and plotProfile.
    10. Use bedtools closest to find the genes where the reads were mapped.
    11. Make the analysis of the extracted tails.

## Prepare new folders in your local directory
We will create the temporary files and plots. We have to create folder system to keep order

> mkdir data
> 
> mkdir plots
> 
> mkdir processing_data
> 
> mkdir reference
> 
> mkdir summary_file  
  
## Prepare the data and file with annotations (references)
1. Save the raw data (in fasta/ fastq/ bam) in file 'data'. 
    We will use data in format .bam, but you can convert the format to bam.
2. Prepere references with annotation in file 'reference'

## Prepare the new environment with dependencies
In order to run locally:
    
> conda create --name rnatails python=3.7
> 
> conda activate rnatails

> conda install -c bioconda seqkit fastqc je-suite HISAT2 samtools bedops rseqc htseq cutadapt
> 
> pip install numpy==1.17.3
> 
> pip install matplotlib==3.0.3
> 
> pip install opencv-python-headless
> 
> pip install scikit-bio
> 
> 
> conda install jupyter
> 
> conda install -c anaconda openjdk
> 
> jupyter-notebook
> 
> conda deactivate rnatails

# Make the environment for IGV
> conda create --name igv python==3.7
> 
> conda activate igv
> 
> conda install -c bioconda igv
> 
> conda deactivate igv
