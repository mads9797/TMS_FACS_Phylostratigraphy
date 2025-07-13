# TMS_FACS_Phylostratigraphy

This repository contains the full workflow and codebase for analysing age-related gene expression changes across phylostrata using the Smart-seq2 FACS subset of the Tabula Muris Senis (TMS) single-cell RNA-sequencing dataset.

## Project Overview

This project investigates how genes of different evolutionary ages are differentially expressed during ageing in mice. Using phylostratigraphy, single-cell transcriptomics, and differential expression analysis, it explores tissue-specific transcriptional trends between 3-month-old (young adult) and 24-month-old (aged) mice.

## Data Sources

- **Tabula Muris Senis (FACS subset)**: Single-cell RNA-seq profiles of 23 mouse tissues across multiple ages.
- **Gene Age Annotations**: Lab-supplied file mapping genes to phylostrata (named gene_phylostrata.csv)
- All data used is publicly available.

## Reproducibility

All code is containerised (Docker/Singularity) and version-controlled using Git. The repository is structured to support reproducible and transparent research

## Repository Structure

TMS_FACS_Phylostratigraphy/
├── data/                    # Raw data files (read-only)
├── scripts/                 # R scripts for each step of the pipeline
├── results/                 # DE output, plots, GO enrichment results
├── docker/                  # Docker/Singularity files for reproducibility
├── README.md                # Project description and usage
└── TMS_FACS_Phylostratigraphy.Rproj  # RStudio project file


## Script
	•	TMS_FACS_Phylostrata_analysis.R:
This single R script performs the complete analysis pipeline, including:
	•	Data loading and formatting
	•	Quality control and normalisation
	•	Dimensionality reduction and batch correction
	•	Differential expression testing
	•	Visualisation of phylostrata trends and GO enrichment
	
## Dependencies

This project was developed using R version 4.3.3 within a containerised environment. Key dependencies include:
	•	Seurat – Single-cell data integration, QC, normalisation, clustering
	•	MAST – Differential expression analysis for single-cell data
	•	Harmony – Batch correction across experimental conditions
	•	clusterProfiler – Gene Ontology (GO) enrichment analysis
	•	ggplot2, ggrepel, patchwork – Custom data visualisation
	•	gprofiler2 – Ortholog and phylostrata mapping
	•	data.table, dplyr, tidyr – Efficient data manipulation
	•	scDblFinder – Doublet detection using batch-aware modelling

All dependencies are managed within a Docker/Singularity container, defined in /docker/Dockerfile. This ensures reproducibility across environments.


## How to Reproduce repository 

1. Clone this repo:
   (bash)
   git clone https://github.com/mads9797/TMS_FACS_Phylostratigraphy.git
   
   