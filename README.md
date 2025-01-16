# RNA-seq-Data-Analysis-A-Framework-for-Comparing-Computational-Pipelines


## Streamlining RNA-seq Data Analysis Using Clustering Pipelines
This repository provides code, results, and documentation for a comparative study on clustering pipelines applied to bulk RNA-seq data. By integrating dimensionality reduction techniques with clustering algorithms, the study offers insights into transcriptomic patterns in COVID-19 patients and healthy controls.

## Project Summary
RNA sequencing (RNA-seq) provides transformative insights into transcriptomic changes, but analyzing high-dimensional RNA-seq data is computationally challenging. In this project, we compare four clustering pipelines to assess their performance in grouping RNA-seq data and uncover biologically meaningful insights. The best-performing pipeline was applied to identify differentially expressed genes (DEGs) and enriched pathways, shedding light on molecular mechanisms of COVID-19.

## Key Objectives
1. Evaluate clustering pipelines combining dimensionality reduction techniques (PCA, t-SNE) with clustering algorithms (K-means, Hierarchical Clustering).
2. Identify biologically significant clusters associated with disease states.
3. Perform differential expression analysis (DEA) and pathway enrichment.
   
## Dataset Overview
Source: GEO Accession: GSE152418
Samples: 68 total (34 Healthy, 32 COVID-19, 2 Convalescent)
Data Type: Bulk RNA-seq
Relevance: Investigates the transcriptomic landscape of SARS-CoV-2 infection, recovery, and host immune response.

## Workflow
1. Preprocessing
Quality control and read trimming using FastQC and TrimGalore.
Alignment to the human genome (hg38) with HISAT2.
Gene count matrix generation using featureCounts.
2. Data Normalization
Input Files:
Gene Expression Matrix: Contains raw gene counts with metadata.
Metadata File: Includes sample conditions and biological information.
Steps:
Filter genes with counts > 5.
Log transformation with log2(x + 1).
Scaling using StandardScaler for zero-mean and unit variance.
Output: Preprocessed dataset saved as normalized_data.csv.
3. Clustering and Evaluation
Techniques:
Dimensionality reduction: PCA, t-SNE.
Clustering: K-means, Hierarchical Clustering.
Evaluation Metrics:
Adjusted Rand Index (ARI), Silhouette Score, runtime, memory usage.
4. Differential Expression Analysis (DEA)
Identify significant DEGs between clusters.
Perform Gene Ontology (GO) and KEGG pathway enrichment.

## Results
Clustering Pipelines
Pipeline	ARI	Silhouette Score	Runtime (s)	Memory Usage
PCA + K-means	0.32	0.10	5.56	103.78 MB
PCA + Hierarchical	0.24	0.47	30.14	104.62 MB
t-SNE + K-means	0.51	0.41	13.00	102.81 GB
t-SNE + Hierarchical	0.60	0.42	12.80	103.62 GB

## Key Findings
Best Performing Pipeline: t-SNE + Hierarchical Clustering.
Achieved ARI of 0.60 and revealed meaningful biological clusters.
Enabled downstream DEG and pathway enrichment analysis.

## Biological Insights
Differential Expression Analysis (DEA):
Identified 14,667 DEGs (3,873 upregulated, 10,794 downregulated).
Notable genes: CYP1B1, RNF216, HERC3 (upregulated); ZNF573, KIAA1279, NEMP1 (downregulated).
Gene Ontology (GO) Enrichment:
Top processes: RNA splicing via the spliceosome, mRNA processing, ribosome biogenesis.
KEGG Pathway Enrichment:
Significant pathways: PD-L1/PD-1 checkpoint, ubiquitin-mediated proteolysis, Herpes simplex virus 1 infection.

## How to Run
Dependencies
Python 3.8+
Libraries: pandas, numpy, scikit-learn, matplotlib, seaborn, umap-learn, scipy.
Outputs
Visualizations: PCA, t-SNE, UMAP, dendrograms.
Metrics: Silhouette scores, ARI, runtime, memory usage.

## Acknowledgments
Team Members:
Asra Tasneem Shaik, Muni Manasa Vema, Mahima Mahabaleshwar Siddheshwar, Saranya Guvvala.

Course: Computational Methods for Biomedical Informatics (B536).
