# scVelo: RNA Velocity 


## scVelo Workflow
![alt text](scVelo.jpg)
1. Input

The analysis begins by loading a single-cell RNA-seq dataset into an AnnData object.
This object stores both spliced and unspliced transcript counts, which are essential for modeling transcriptional dynamics. Before analysis, the dataset is inspected to ensure that the ratio of spliced to unspliced reads is appropriate for velocity estimation.

## scVelo Analysis
![alt text](BENG183_Analysis.webp)
