# ML Pattern Recognition on GWAS/mQTL Data for Cancer Risk Prediction
### Cotiviti Intern Assessment — Bhavya Sevak | Arizona State University | June 2026

---

## Overview

This repository contains all deliverables for the Cotiviti Intern Assessment. The chosen topic is **Clinical Decision Making and Pattern Recognition in Health Care**, with a focus on machine learning applied to genome-wide association study (GWAS) and methylation quantitative trait loci (mQTL) data for cancer risk prediction.

The core thesis: integrating GWAS SNP data with mQTL epigenetic signals and applying ML pattern recognition produces Polygenic Risk Scores (PRS) that outperform classical statistical approaches — especially in diverse, non-European ancestry cohorts. This capability has direct strategic value for Cotiviti's population health analytics portfolio.

---

## Repository Contents

| File | Description |
|------|-------------|
| `cotiviti_report.docx` | Two-page written report + APA bibliography (Word) |
| `cotiviti_slides.pptx` | 8-slide PowerPoint presentation |
| `cotiviti_poc.ipynb` | Jupyter notebook — end-to-end ML pipeline POC |
| `README.md` | This file |

> **Video recording** is submitted separately per instructions.

---

## Proof of Concept — Quick Start

### Requirements

```bash
pip install numpy pandas scikit-learn xgboost matplotlib seaborn
```

### Run the Notebook

```bash
jupyter notebook cotiviti_poc.ipynb
```

Or open directly in VS Code, Google Colab, or any Jupyter environment.

### What the POC Does

The notebook demonstrates a full GWAS → ML → PRS pipeline in ~120 lines of Python:

1. **Synthetic GWAS Dataset** — Simulates 1,000 samples × 5,000 SNPs with Hardy-Weinberg equilibrium allele frequencies; 50 causal SNPs drive colorectal cancer case/control labels
2. **mQTL Feature Engineering** — Models methylation-amplified SNP effect sizes (beta-value interaction scores)
3. **Feature Selection** — Chi-squared pre-filter (5,000 → 500 SNPs) followed by LASSO logistic regression (→ ~47 informative SNPs)
4. **XGBoost Classifier** — Gradient-boosted tree model with 5-fold stratified cross-validation; handles class imbalance via `scale_pos_weight`
5. **PRS Output** — Isotonic-calibrated per-sample risk scores stratified into Low / Intermediate / High / Very High tiers

### Key Results

| Metric | Value |
|--------|-------|
| Cross-validated AUC | ~0.81 |
| SNPs selected (LASSO) | ~47 of 5,000 |
| Runtime | < 30 seconds (CPU) |
| Lines of code | ~120 |

---

## Report Summary

**Topic:** ML Pattern Recognition on GWAS/mQTL Data for Cancer Risk Prediction

**Trends analyzed:**
- Genomic foundation models (Nucleotide Transformer, DNABERT-2) enabling zero-shot transfer to small cohorts
- Multi-omics integration at scale (UK Biobank, TCGA, All of Us)
- FDA AI/ML SaMD framework expansion and CMS reimbursement pathways (CPT 81479+)

**Strategic recommendations for Cotiviti:**
- **Option A (Recommended):** GWAS-PRS Risk Stratification API — ancestry-aware microservice plugging into existing population health platforms; 6-12 month pilot horizon
- **Option B (Follow-on):** mQTL-Informed Clinical Decision Support — FHIR CDS hooks in EHR workflows via biobank partnerships; 18-36 month horizon

---

## Author

**Bhavya Sevak**  
M.S. Biomedical Informatics Candidate (Expected 2026)  
Arizona State University  
[bsevak1504@gmail.com](mailto:bsevak1504@gmail.com) | [GitHub](https://github.com/bsevakstark)

---

*Submitted for the Cotiviti Intern Assessment. Synthetic data only — not clinically validated.*
