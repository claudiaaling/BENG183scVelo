# scVelo: Predicting the Future State of Cells

## RNA Velocity

## scVelo Workflow
![alt text](scVelo.jpg)
### 1. Input <br>
scVelo infers RNA velocity by leveraging both spliced and unspliced mRNA counts from single-cell RNA sequencing data, allowing  to reconstruct directional cell state transitions. The analysis begins with loading the dataset into an AnnData object, which stores the expression matrix along with metadata and separate layers for spliced and unspliced transcripts. The initial step involves confirming that the dataset contains adequate proportions of each.<br>
### 2. Preprocessing <br>
  Before velocity estimation can be performed, the data undergo preprocessing to ensure that the model is fit on well-normalized features. scVelo filters out lowly expressed genes, normalizes expression values per cell, and applies a logarithmic transformation to stabilize variance. Dimensionality reduction is then performed using PCA, and the algorithm constructs a k-nearest neighbor graph representing the local structure of the transcriptomic space. Using this graph, scVelo calculates each cells' neighbors averages and variances for spliced and unspliced counts, providing the foundation for its dynamical modeling approach.<br>
### 3. RNA Velocity Inference <br>
  Then it models the transcriptional kinetics of each gene. The software computes a velocity vector for every cell that predicts how its gene expression profile is expected to change over time. These individual vectors are assembled into a velocity graph, which compares each cell’s predicted movement with that of its neighbors. The resulting structure highlights the most probable transitions between cellular states and reveals the developmental or differentiation trajectories in the dataset.<br>
### 4. Projection <br>
  Finally, scVelo projects the velocity estimates onto a low-dimensional embedding such as UMAP.  On the UMAP, streamlines and velocity arrows show how cells are expected to move in the future, revealing both overall developmental trends and details such as branching points or changes in direction. <br>

## scVelo Analysis
![alt text](BENG183_Analysis.webp)
Using scVelo, we can extract key insights about cellular dynamics, lineage progression, and gene regulation from single-cell RNA sequencing data.<br>
### 1. Dynamical Model: Directionality and Lineage Structure <br>
The dynamical model highlights both the identity of cell populations and the direction in which they progress. In the UMAP, RNA velocity streamlines reveal how cells transition from early  states toward differentiated endpoints such as ductal, endocrine, or hormone-producing lineages. Compared to the steady-state model, the dynamical model provides biologically consistent trajectories that align with known developmental pathways. <br>
### 2. Latent Time: True Biological Progression  <br>
scVelo can compute latent time, an inferred continuous timeline that orders cells based on their transcriptional kinetics. Latent time acts as the cell’s internal developmental clock and reveals the true biological progression more accurately than traditional pseudotime. Distinct embryonic stages can be clearly separated, showing how populations evolve over developmental time.  <br>
 ### 3. Heatmap
scVelo identifies dynamical genes which are genes expression changes meaningfully across the inferred developmental trajectory. The heatmap displays these genes in waves of activation and repression across latent time. This pattern confirms the direction of differentiation and highlights genes that likely regulate major transitions, such as early progenitor markers turning off and lineage-specific markers turning on.  <br>
### 4. Transcriptional Switches 
Phase plots for individual genes show the relationship between spliced and unspliced mRNA, revealing when genes switch on or off. These transcriptional switches help identify regulators that may drive fate decisions. For example, genes like Actn4, Ppp3ca, Cpe, or Nnat show distinct kinetic patterns that correlate with major branch points in the trajectory.


