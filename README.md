# Analysis of Gene Expression in HER2 Amplified Breast Cancer.

## Overview
This scrip will analyse gene expression dta in HER2 amplififed and non-amplified breast cancer. It will contain Data preprocessing, normalisation, differential expression analysis, pathway enrichment, visualisation and survival modeling.

## Required Packages
- DESeq2
- clusterProfiler
- org.Hs.eg.db
- enrichplot
- ReactomePA
- pathview
- ggplot2
- glmnet
- pheatmap
- survival
- survminer

## Data Sets
- Patient data: data_clinical_patient.txt
- RNA-seq data: data_mrna_seq_v2_rsem.txt
- Copy Number Aberrations (CNA): data_cna.txt

## Code
### 1. Data Preperation
Read and preprocess all three text files:
- Untar folder and extract files
- Import and read the patient, RNA-seq and CNA data
- Filter data and match the RNA-seq patient ids with the CNA and patient ids
- Create metadata with zero matrix and assign rows and columns using CNA levels of ERBB2

### 2. Normalisation 
Normalise RNA-seq counts for differential expression analysis.
- Convert metadata to dataframe
- Create Desq Dataset
- using low count genes, normalise data and extract normalised assay
- Get variance stabalised transformed expression values (vst)

### 3. Differential Expression Analysis
Identify genes with significant expression differences between ERBB2 amplified and non-amplified groups 

- Obtain Differentially expressed genes with the results function 
- Extract and plot the results with a volcano plot and rank genes by adjusted p-value and log2 Fold Change
- Visaulise top 10 differentially expressed genes with bar plot

### 4. Pathway Enrichment Analysis
Identify enriched pathways for over and under-expressed genes
- Convert gene symbols to Entrez IDs using clusterprofiler
- Perform Gene Ontology pathway enrichment analysis
- Visualise results using dot plots and tree diagrams

### 5. Principal Component Analysis
Visualise clustering based on VST expression data
- Perform PCA using DESeq2 plotPCA function

### 6. Heatmap Visualisation 
Visualise expression pattern of top differentially expressed genes
- Extract VST values for top genes
- Create heatmap using pheatmap

### 7. Lasso Regularised Cox Regression
Model survival outcomes based on differentially expressed genes

- Align survival data with expression data
- Fit Lasso Regularised Cox Regression using glmnet
- Plot Cross-validation curve with the fitted regression
- Divide samples into high and low risk groups by predicited risk score
- Plot Kaplan-Meier Survival curves using survminer

