# RNA-seq Analysis of *Daphnia magna* Exposed to River Water Chemicals
This is part of the Computational Biology coursework for the MSc Bioinformatics program. This project is divided into two parts:
- DESeq Analysis (DESeq_analysis.Rmd)
- Correlation Analysis (Correlation_analysis.ipynb)

## 1. DESeq Anaylsis:
### Project Overview
This project involves RNA-sequencing data from a study that investigated the effects of environmental chemical exposure on *Daphnia magna*. The organisms were collected from 12 different locations along a river and were exposed to river water containing various chemicals at different concentrations: Control (natural river water), 1x (baseline exposure), and 10x (artificial environment with tenfold chemical concentration). A list of the chemicals used is provided in the `water_chemicals.tsv` file.


## Objectives
The primary goal was to identify differentially expressed genes (DEGs) in *Daphnia magna* across different chemical exposure conditions (1x and 10x) compared to the control group.


## Steps Performed

### 1. **Data Preprocessing**
- **Loading Data**: Imported raw read count data (`rna_raw_counts.csv`) and sample metadata (`sample_sheet.csv`).
- **Filtering**:
  - Removed low-quality samples with >75% zero counts.
  - Filtered out genes with low expression (total count <200 or too many zeros).
  - Removed genes with near-zero variance.

### 2. **Experimental Design**
- Categorical variables were encoded as factors (`REF`, `Site`, and `Description`), and a composite factor `REF_Site` was created to represent the combined condition.
- Differential expression was analyzed using the DESeq2 package with the model: `~ REF_Site`.

### 3. **Differential Expression Analysis**
- DEGs were identified by contrasting each 1x and 10x location group with the control group.
- Adjusted p-value threshold (`padj < 0.05`) was used to select significant DEGs.

### 4. **Results Summary**
- For each location and exposure level (1x and 10x), the top 10 upregulated and downregulated genes were extracted based on log2 fold change.
- Summary results were exported as individual CSV files.
- All top DEGs were compiled into an Excel workbook (`top_genes.xlsx`) with separate sheets for each location.


## Key Findings
- Multiple genes were found to be significantly differentially expressed under both 1x and 10x exposures.
- The 10x concentration condition generally showed a greater number of DEGs, consistent with stronger biological responses.
- DEGs included both upregulated and downregulated genes, varying by location and exposure level.


## Files
- `rna_raw_counts.csv`: Raw count data.
- `sample_sheet.csv`: Sample metadata.
- `water_chemicals.tsv`: List of chemicals used in the study.
- `top_genes.xlsx`: Consolidated Excel file of top DEGs per location.
- `top_upregulated_genes_DXX.csv` and `top_downregulated_genes_DXX.csv`: Per-location DEG files.

<br><br>
## 2. Correlation Analysis
### Overview
In this section of the analysis, we explore the correlation between the differentially expressed genes (DEGs) under 1x and 10x chemical exposure conditions and the concentrations of chemicals from different sampling locations. This analysis follows the DESeq differential expression analysis and aims to understand how the expression of specific genes correlates with chemical concentrations in the environment.

## Steps:

### 1. Load and Preprocess Data:
- The analysis starts by loading and preprocessing two key datasets:
    - **Chemical Data**: Contains the concentrations of various chemicals across different sampling locations.
    - **Gene Expression Data (DEGs)**: Includes the differentially expressed genes (DEGs) from the RNA-seq analysis, split by exposure conditions (1x and 10x).

### 2. Identify Common Genes for Each Location:
- **Finding Common Genes**:
    - For each location, common genes between the **1x and 10x upregulated** and **downregulated** DEGs are identified.
    - The genes that are significantly upregulated or downregulated in both the 1x and 10x conditions for each location are retained for further analysis.
- The common genes across conditions and locations form the basis for the correlation analysis with chemical concentrations.

### 3. Filter and Clean Data:
- **Chemical Data**:
    - The chemical data is cleaned by removing rows with missing or zero values.
    - Only rows with at least 3 non-zero values are retained for robust correlation analysis.
    - The `ChemName` column is repeated across all chemical data for consistency.
- **Gene Expression Data**:
    - The gene expression data is filtered to keep only the significant upregulated and downregulated genes for the 1x and 10x exposure conditions.

### 4. Correlation Analysis:
- A **Pearson correlation** is computed between the chemical concentrations and the expression levels of the common genes.
- The correlation matrix shows the relationship between chemical exposure and gene expression for each location.
- Positive correlations indicate genes whose expression increases with higher chemical concentrations, while negative correlations suggest genes that decrease with chemical exposure.

### 5. Visualization:
- A **heatmap** of the correlation matrix is generated to visually represent the strength and direction of the correlations for all genes and chemical exposures.

## Key Findings:
- The 1x upregulated and 1x downregulated heatmaps show opposite patterns of correlation with chemical concentrations.
- The 10x upregulated and 10x downregulated heatmaps show opposite patterns of correlation with chemical concentrations.