# TMS_FACS_Phylostratigraphy

This repository contains the full workflow and codebase for analysing age-related gene expression changes across phylostrata using the Smart-seq2 FACS subset of the Tabula Muris Senis (TMS) single-cell RNA-sequencing dataset.


## Project Overview

This project investigates how genes of different evolutionary ages are differentially expressed during ageing in mice. Using phylostratigraphy, single-cell transcriptomics, and differential expression analysis, it explores tissue-specific transcriptional trends between 3-month-old (young adult) and 24-month-old (aged) mice.
This project was conducted as part of my MSc Bioinformatics dissertation at King's College London (2025).

## Data Sources

- **Tabula Muris Senis (FACS subset)**: Single-cell RNA-seq profiles of 23 mouse tissues across multiple ages.
- **Gene Age Annotations**: Lab-supplied file mapping genes to phylostrata (named gene_phylostrata.csv)
- **MGIBatchReport_20250628_152059.txt**: An intermediate file generated using MGI’s batch ortholog tool to map mouse gene symbols to human Ensembl IDs. This file supports the phylostrata annotation process and is included for full reproducibility.
- All data used is publicly available.


## Repository Structure
```
TMS_FACS_Phylostratigraphy/**
├── data/                    # Raw data files
├── scripts/                 # R scripts for each step of the pipeline
├── results/                 # DE output, plots, GO enrichment results
├── README.md                # Project description and usage
└── TMS_FACS_Phylostratigraphy.Rproj  # RStudio project file
```

## Script Description

**TMS_FACS_Phylostrata_analysis.R**  
This single R script performs the complete analysis pipeline, including:

- **Data loading and formatting**
- **Quality control and normalisation**
- **Dimensionality reduction and batch correction** 
- **Differential expression testing**
- **Visualisation of phylostrata trends and GO enrichment**
	
## Dependencies

This project was developed using R version 4.3.3 within a containerised environment.

Key dependencies include:

- **Seurat** – Single-cell data integration, QC, normalisation, clustering  
- **MAST** – Differential expression analysis for single-cell data  
- **Harmony** – Batch correction across experimental conditions  
- **clusterProfiler** – Gene Ontology (GO) enrichment analysis  
- **ggplot2**, **ggrepel**, **patchwork** – Custom data visualisation  
- **gprofiler2** – Ortholog and phylostrata mapping  
- **data.table**, **dplyr**, **tidyr** – Efficient data manipulation  
- **scDblFinder** – Doublet detection using batch-aware modelling  

All dependencies are managed via a Docker or Singularity container for full reproducibility.

## Docker Image

This project is containerised for reproducibility and ease of use.

You can use the pre-built image from Docker Hub:[madihakhan/tsm_pheno_analysis](https://hub.docker.com/r/madihakhan/tsm_pheno_analysis)

### Step-by-step Instructions

1. Pull the image: (if not already downloaded):
   ```bash
   docker pull madihakhan/tsm_pheno_analysis:latest
   ```
2. Run the container with RStudio Server
   Set your OWN password (used to log in to RStudio):

   ```bash
   docker run -e PASSWORD=yourpassword -p 8787:8787 madihakhan/tsm_pheno_analysis:latest
   ```
3.	Access RStudio in your browser:
- Open: [http://localhost:8787](http://localhost:8787)  
- Username: `rstudio`  
- Password: `yourpassword` (from step 2)

## Running the Analysis

1. **Clone this repository**:
   ```bash
   git clone https://github.com/mads9797/TMS_FACS_Phylostratigraphy.git
   cd TMS_FACS_Phylostratigraphy
  ```
2.	Follow the Docker setup in the Docker Image section above to run the containerised environment.

3. Run the main script in RStudio (after following bash steps):
   ```R
   source("scripts/TMS_FACS_Phylostrata_analysis.R")
  ```	

### Author

Madiha Khan  
MSc Bioinformatics, King's College London  
GitHub: [@mads9797](https://github.com/mads9797)
   