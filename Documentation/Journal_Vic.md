# Organoid Single Cell Seminar

## 10/12/2021
### Plan:
In order to be able to process all the datasets we need in short time I'm thinking about using PiGx scRNA-seq
to do the preprocessing and QC reporting and only using the results for further downstream processing. The pipeline will
output `SingleCellExperiment` objects that are made for Bioconductor. They can be converted to the Python `AnnData` object
by using the [zellkonverter](https://bioconductor.org/packages/devel/bioc/vignettes/zellkonverter/inst/doc/zellkonverter.html)
package.

all the single-cell datasets that we need:
    1. organoid - cntrl 1
    2. organoid - cntrl 2
    3. atlas - day9
    4. atlas - day27 - donor 1
    5. atlas - day27 - donor 2

1. finish ScanPy tutorial to know about the basics
2. install PiGx scRNA and run the test
3. set up a scalable environment for the single cell data sets - start with one: organoid - cntrl 1
4. run PiGx for it
5. try to make sense from the output
6. try to convert the output
7. do some scanpy downstream analysis

## 13/12/2021

1. installing pigx-rna seq with guix  
    - test ? maybe not possible whith the package installation  
    - asked ricardo
    - yes you can - but you have to clone the repository with the test directory before :) 
    - then just run the pipeline with repo/test/samplesheet.csv etc.
2. Download first dataset to try with pigx  
    - https://www.ncbi.nlm.nih.gov/sra?term=SRX9548403  
    - SRR 131028(21-32)
    - The pipeline will do all the steps that usually would have to be done before matrix generation  
    - so download the fastq  
      * for (( i = 21; i <= 32; i++)); do fastq-dump SRR131028$i --gzip --split-files; done
    - get the human ref genome and human gtf --> took from pigx sample director
3. make a sample sheet 
    - maybe I can use the script I wrote for pigx-sars-cov-2 for this
4. I think you should also just download the matrix and the normal stuff, open this with scanpy and check it out what you will find there

## ?? 

TODO: Fill in conclusions from last year

## 04/01/2021 
### Nature paper data
1. check paper where to find data
   1. organoid data --> [here](https://www.ebi.ac.uk/arrayexpress/experiments/E-MTAB-10283/samples/)  
   2. I'm not sure yet what's the difference between the samples, I assume those with "none" are controls but I don't
   3. know the difference between the controls
   4. I'm just starting with the first two for now
2. download some control organoid data
3. open the scanpy tutorial
4. go through the tutorial steps with the organoid data
   1. the feature files always only have 1 column the gene symbol column, but we need at least two columns with the 
   additional Enselmbe ID. See [here](https://github.com/theislab/scanpy/issues/2053). Apparently there is an R-package
   that can do this automatically ([biomaRt](https://bioinformatics.stackexchange.com/questions/5229/converting-gene-symbol-to-ensembl-id-in-r)). 
   I will ask Tancredi tomorrow if there might be an easier way too. For now I continue with some of the other data.  

### Fitzgerald paper
