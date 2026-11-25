# Meningioma Positional Programs — Reproducible Analysis Repository

Reproducible multi-omics analysis pipeline and source-data repository investigating **axial *HOX* DNA methylation gradients, focal cranial *ALX3* regionalization, beyond-dosage *ALX3* epigenetic attenuation on chromosome 1p13.3, and the temporal precedence of early molecular progression over late positional breakdown and ectopic *HOX* derepression in human meningiomas**.

> **Status**: Preparing structured code and numerical source-table release. All analyses use publicly available, de-identified human meningioma and normal developing/adult meningeal datasets; no new participant data were collected and no raw sequencing/array files are redistributed.

---

## Planned Repository Structure

| Directory | Planned Contents |
| :--- | :--- |
| `data/` | Public dataset download scripts and cohort-level patient, tumor, specimen, section, and intra-institutional multi-assay overlap manifests (`Supplementary Table 1a,b`; large raw IDAT, FASTQ, BAM, Loom, and RDS files excluded) |
| `scripts/01_preprocessing_spinal/` | Raw IDAT `minfi` (`preprocessNoob`) preprocessing, 59-SNP donor identity verification and deduplication, unbiased epigenome-wide spinal EWAS (`GSE212449`), and exploratory nonlinear/hinge functional-form analyses |
| `scripts/02_cranial_discovery_chromatin/` | Genome-wide cranial RNA-seq differential expression and EPIC EWAS (`GSE189672`/`GSE189521`), primary meningioma and dura `H3K27ac`/`H3K27me3` ChIP-seq window occupancy (`GSE85132`, `GSE91372`, `GSE92558`), and floor-aware nonparametric validation in external Yale cohorts (`GSE84263`, `GSE91375`) |
| `scripts/03_clival_meninges_survival/` | Exploratory clival/foramen-magnum `HOX1–4` endothelial-adjusted models and 29-partition wild-bootstrap selection audits, developing human meninges reference benchmarking (`Vinsland et al., 2026`), and calendar-date-verified Cox recurrence-free survival models |
| `scripts/04_anterior_alx3_chr1p_dosage/` | Anterior cranial *ALX3* attenuation (`MenG C` enrichment and sensitivity analyses) and chromosome 1p arm-wide gene-dosage versus locus-specific beyond-dosage *ALX3* RNA/methylation benchmarking (including `histologically WHO grade 1 tumors with 1p loss` in `GSE84263`) |
| `scripts/05_snrna_spatial_multiregional/` | Single-nucleus neoplastic-versus-endothelial *HOX* paralog dissociation (`GSE313693`, `GSE278452`), 10x Visium spatial niche colocalization across 44 sections from 39 unique meningiomas (`GSE313694`, `GSE299374`), and multiregional stereotactic biopsy ICC analyses (`GSE151067`, `GSE151921`) |
| `scripts/06_forward_prediction_nested_loocv/` | Forward positional recovery: locked `94-CpG` linear spinal LOOCV alongside strictly nested within-fold (`N − 1`) technical probe QC, 16-module × CpG-context selection, and hypothesis-free 391,574-CpG EWAS LOOCV; zero-shot fetal-to-tumor cranial classification and high-grade `posterior-like calls` confounding audits |
| `scripts/07_temporal_precedence/` | Cross-cohort event precedence (`McNemar` discordant-pair tests), stage-ordered single-nucleus progression cascades, longitudinal paired-resection trajectories (`12` patient pairs), and spatial Visium proliferative-hotspot analyses |
| `scripts/08_verification/` | Independent R–Python cross-language mathematical recomputation and automated cross-document QA checks |
| `results/` | Processed summary statistics (`CSV`) and the integrated 54-sheet supplementary workbook (`Supplementary_Tables.xlsx`) |
| `figures/` | Reproducible plotting scripts generating Main Figures 1–9 and Supplementary Figures 1–12 (`600 dpi` TIFF and PNG) |
| `env/` | Software environment specifications (`R 4.3.2` / Bioconductor 3.18 and `Python 3.12+` dependency lockfiles) |

---

## Public Datasets Referenced

- **Spinal meningioma DNA methylation**: `GSE212449` (Ricklefs et al., *Acta Neuropathol.* 2022)
- **Paired cranial RNA-seq & EPIC DNA methylation**: `GSE189672`, `GSE189521`, and companion BCM clinical deposit (Bayley et al., *Sci. Adv.* 2022; legacy 101-tumor cohort and transcriptional classifier from Patel et al., *PNAS* 2019)
- **External multi-assay expression, methylation & ChIP-seq**: `GSE84263`, `GSE85132` (Clark et al., *Nat. Genet.* 2016); `GSE91375`, `GSE91372`, `GSE92558` (Harmancı et al., *Nat. Commun.* 2017)
- **Normal developing human meninges single-cell atlas**: `linnarsson-lab/human-meninges-development` (Vinsland et al., *Nat. Cell Biol.* 2026)
- **Bulk RNA-seq, adult dura scRNA-seq, multiregional biopsies & inducible Merlin rescue xenografts**: `GSE183653`, `GSE183655` (Choudhury et al., *Nat. Genet.* 2022); `GSE151067`, `GSE151921` (Magill et al., *Nat. Commun.* 2020); `GSE224347` (Eaton et al., *Nat. Commun.* 2024)
- **Longitudinal snRNA-seq & 10x Visium spatial transcriptomics**: `GSE313693` / Zenodo `17941488`, `GSE313694` (Maas et al., *Nat. Genet.* 2026); `GSE278452` (Lee et al., *Nat. Commun.* 2025); `GSE299374` (Aggarwal et al., *Neuro Oncol.* 2026)
