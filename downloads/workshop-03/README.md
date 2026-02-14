# Bulk RNA-seq Workshop — October 16, 2025

**Instructor:** [Dr. Aatish Thennavan](https://scholar.google.com/citations?user=g0PzOkwAAAAJ&hl=en)  
**Topic:** Introduction to bulk RNA-seq analysis using `edgeR`, `limma`, and `DESeq2`

## Overview

This workshop introduces key steps in the analysis of bulk RNA-seq data, including data preprocessing, normalization, differential expression analysis, visualization, and pathway enrichment. All analyses are performed in R using standard Bioconductor packages.

## Dataset

We analyze paired-end RNA-seq libraries from human lung cancer samples:

**Deng et al., 2021, Nature Cancer (PMID: 34142094)**

Files used in the workshop:

- **Gene-level count matrix** (STAR / Salmon output)  
- **Sample annotation file** containing metadata and experimental conditions (e.g., KL vs KP)

## Required R packages

Core libraries used throughout the workshop:

- **Core analysis:** `limma`, `edgeR`, `DESeq2`  
- **Visualization:** `ggplot2`, `ggrepel`, `pheatmap`, `EnhancedVolcano`, `Glimma`  
- **Pathway analysis:** `msigdbr`, `fgsea`, `clusterProfiler`, `GSVA`, `GSEABase`  
- **Utilities:** `tidyverse`, `RColorBrewer`, `AnnotationDbi`, `org.Hs.eg.db`, `FactoMineR`, `factoextra`

Full installation instructions and the package-install code block are included in the R Markdown file for this workshop.


## Learning goals

By the end of this workshop, participants should be able to:

- Load and preprocess bulk RNA-seq count data.  
- Perform normalization and filter lowly expressed genes.  
- Create and work with `edgeR` and `DESeq2` objects.  
- Assess sample heterogeneity using PCA / MDS and identify outliers.  
- Perform differential expression analysis using DESeq2 and limma/voom.  
- Visualize differential expression results (volcano plots, heatmaps).  
- Perform pathway enrichment with GSEA and GSVA.



## Notes & tips

- Ensure sample IDs match exactly between the count matrix and metadata file.  
- Inspect normalization results visually (boxplots) before downstream analysis.  
- Compare DE results across methods (DESeq2 vs limma) to identify consistent signals.  
- For publication-quality figures, tweak plotting parameters (font size, label overlap, color palettes).








