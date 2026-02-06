# Bulk RNA-seq Workshop — October 16, 2025

**Instructor:** [Dr. Aatish Thennavan](https://scholar.google.com/citations?user=g0PzOkwAAAAJ&hl=en)  
**Topic:** Introduction to bulk RNA-seq analysis using `edgeR`, `limma`, and `DESeq2`

## Overview

This workshop introduces key steps in the analysis of bulk RNA-seq data, including data preprocessing, normalization, differential expression analysis, visualization, and pathway enrichment. All analyses are performed in R using standard Bioconductor packages.


## Project structure
```
Bulk_RNAseq_Workshop/
├── slides/                            # PDF or PowerPoint slides for the workshop  
│ 
├── code/                  
│   └── BulkRNAseq_Workshop_2025.Rmd   # Full workshop R Markdown with code
│  
├── data/                              # Example datasets used in the workshop   
│ 
└── README.md                          # This file    
```  

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



## Workflow summary

### 1. Load gene-level count data
- Read the raw count matrix into R.  
- Inspect gene annotation and matrix dimensions.  
- Remove unannotated or ambiguous gene rows and standardize row names.  
- Convert counts to integer mode if needed.

### 2. Filter and explore raw counts
- Compute log-CPM (counts per million) and inspect distributions.  
- Filter lowly expressed genes (keep genes expressed in ≥ 2 samples at a chosen CPM threshold).  
- Visualize library sizes and expression distributions (histogram, barplot, boxplot).

### 3. Create `edgeR` and `DESeq2` objects
- Load sample metadata and ensure sample order matches the count matrix.  
- Create `DGEList` for `edgeR` and `DESeqDataSet` for `DESeq2`.

### 4. Normalization
Three normalization strategies are demonstrated and compared with boxplots:

1. **Upper Quartile Normalization (UQN)**  
2. **TMM normalization** (Trimmed Mean of M-values; `edgeR`)  
3. **VST / rlog normalization** (`DESeq2`)

### 5. Dimension reduction & clustering
- Multidimensional scaling (MDS) and PCA to explore sample relationships.  
- Extract additional PCs and quantify variance explained.  
- Hierarchical clustering and heatmap of top variable genes to check grouping and outliers.

### 6. Differential expression analysis

#### DESeq2
- Run `DESeq()` workflow.  
- Specify contrasts (e.g., `KL` vs `KP`) and extract results.  
- Identify significant DEGs (example thresholds: FDR < 0.05, |log2FC| ≥ 1).  
- Export results and visualize with volcano plots (`ggplot2`) and `EnhancedVolcano`.

#### limma / voom
- Use `voomWithQualityWeights` for sample-level weights.  
- Fit linear models and apply empirical Bayes (`eBayes`).  
- Extract top tables and compare to DESeq2 results.  
- Interactive exploration via `Glimma`.

### 7. Pathway analysis (GSEA and GSVA)

#### GSEA (fgsea)
- Use MSigDB curated gene sets (C2).  
- Create ranked gene list from DE statistics and run `fgsea()`.  
- Inspect top enriched pathways and plot enrichment curves.

#### GSVA
- Use variance-stabilized (VST) normalized expression matrix for per-sample pathway scoring.  
- Compute GSVA enrichment scores and run differential testing (e.g., `limma`) on pathway scores.  
- Visualize pathway-level heatmaps for top pathways.



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

---

## Further help / contact

If you have questions or want the full example data and outputs included in this folder, please open an issue in the main repository or contact us at GSBS.DSWG@uth.tmc.edu

Happy exploring your bulk RNA-seq data!


[⬅ Back to Workshops Homepage](https://github.com/GSBS-DSWG/homepage)






