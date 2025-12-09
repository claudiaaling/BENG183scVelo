# scVelo:Predicting the Future State of Cells

## RNA Velocity

## scVelo Workflow
![alt text](scVelo.jpg)
  * scVelo infers RNA velocity by leveraging both spliced and unspliced mRNA counts from single-cell RNA sequencing data, allowing  to reconstruct directional cell state transitions. The analysis begins with loading the dataset into an AnnData object, which stores the expression matrix along with metadata and separate layers for spliced and unspliced transcripts. The initial step involves confirming that the dataset contains adequate proportions of each.<br>
  Before velocity estimation can be performed, the data undergo preprocessing to ensure that the model is fit on well-normalized features. scVelo filters out lowly expressed genes, normalizes expression values per cell, and applies a logarithmic transformation to stabilize variance. Dimensionality reduction is then performed using PCA, and the algorithm constructs a k-nearest neighbor graph representing the local structure of the transcriptomic space. Using this graph, scVelo calculates each cells' neighbors averages and variances for spliced and unspliced counts, providing the foundation for its dynamical modeling approach.
  Then it models the transcriptional kinetics of each gene. The software computes a velocity vector for every cell that predicts how its gene expression profile is expected to change over time. These individual vectors are assembled into a velocity graph, which compares each cell’s predicted movement with that of its neighbors. The resulting structure highlights the most probable transitions between cellular states and reveals the developmental or differentiation trajectories in the dataset.
  Finally, scVelo projects the velocity estimates onto a low-dimensional embedding such as UMAP.  On the UMAP, streamlines and velocity arrows show how cells are expected to move in the future, revealing both overall developmental trends and details such as branching points or changes in direction. 

## scVelo Analysis
![alt text](BENG183_Analysis.webp)
