# 🧬 Gene Expression Analysis using RNA-Seq and edgeR

> **Project Title:** Differential Expression Analysis of [Sample Type] under [Condition]  
> **Author:** Kenneth Chen  
> **Affiliation:** iTCGA Cancer Research Workshop 2025  
> **Date:** June 2025  

---

## 📌 Project Overview

This project analyzes RNA-Seq data from [e.g., glioblastoma patient samples] to identify **differentially expressed genes** using `featureCounts` and `edgeR`. The pipeline involves preprocessing FASTQ files, aligning them to the reference genome, generating count matrices, and visualizing results via volcano plots.

---

## 🧪 Objectives

- Quantify gene expression from RNA-Seq data
- Identify differentially expressed genes between [Condition A] and [Condition B]
- Visualize significant genes using statistical plots
- Interpret findings in the context of [e.g., cancer progression]

---

## 🧰 Tools & Libraries

| Tool/Package      | Purpose                        |
|-------------------|--------------------------------|
| `featureCounts`   | Read quantification            |
| `edgeR` (R)       | Differential expression        |
| `pandas` / `ggplot2` | Data wrangling & visualization |
| `fastQC`, `HISAT2`| Quality control and alignment  |

---

## 🗃️ Dataset

- **Samples:** [Number of samples], single-end or paired-end
- **Source:** [GEO accession / local dataset]
- **Reference Genome:** `Homo_sapiens.GRCh38.111.gtf`

---

## 📂 Project Structure

---

## ⚙️ Pipeline Summary

1. **Quality Control**  
   - `fastQC` on raw reads

2. **Alignment**  
   - `HISAT2` to align reads to reference genome  
   - Output: sorted `.bam` files

3. **Quantification**  
   - `featureCounts` to generate `counts.txt`

4. **Differential Expression**  
   - `edgeR` used to calculate Log2 Fold Change, FDR  
   - Visualized using volcano plots and gene-specific jitter plots

---

## 📊 Sample Visualizations

### Volcano Plot
![Volcano Plot](results/volcano_plot.png)

### Gene-Level Expression
![Gene Plot](results/HSPA6_counts.png)

---

## 🧬 Top Differentially Expressed Genes

| GeneID         | logFC | FDR     | Status       |
|----------------|-------|---------|--------------|
| ENSG00000041982 | 3.21  | 0.00004 | Upregulated  |
| ENSG00000123456 | -2.87 | 0.00015 | Downregulated|

Full table available in [`results/topGenes.tsv`](results/topGenes.tsv)

---

## 🔬 Interpretation

> Genes such as **HSPA6** were significantly upregulated under [TGF-β treatment], indicating potential involvement in the stress response pathway. Further biological validation is needed.

---

## 🚀 How to Reproduce

```bash
# Run alignment
bash scripts/run_alignment.sh

# Run count quantification
featureCounts -a genome.gtf -o counts.txt -T 24 aligned_bam/*.bam

# Open R and run analysis
Rscript scripts/edgeR_analysis.R
