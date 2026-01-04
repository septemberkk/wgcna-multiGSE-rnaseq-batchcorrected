# wgcna_record

# WGCNA (batch-corrected multi-study FPKM) – integration from four GEO series

This repository contains a WGCNA workflow built on an integrated **mouse FPKM** expression matrix assembled from multiple GEO studies. Batch correction was performed prior to network construction. The goal is to keep the pipeline auditable: clear inputs, explicit batch handling, and concise key outputs (modules, eigengenes, module–trait associations, hub genes).

---

## Data sources
Integrated from the following GEO series:
- **GSE224358**
- **GSE223156**
- **GSE49329**
- **GSE65067**
- Data type: RNA-seq (GEO: Expression profiling by high throughput sequencing).

---

## Inputs
All analysis is driven by two files:

1) **Batch-corrected expression matrix (FPKM)**
- `results/batch/limma_with_removeBatchEffect`
- Rows: genes  
- Columns: samples  
- Unit: FPKM (batch corrected)

2) **Sample metadata**
- `data/processed/sample_metadata.tsv`
  - `sample`
  - `group` (phenotype/condition used for downstream association)

A simple provenance list is stored at:
- `data/raw/source_geo_ids.txt`

---

## Batch correction
Batch correction was applied to reduce study-specific effects before WGCNA.

- Batch variable: data/raw/source_geo_ids.txt
- Output matrix: `limma_with_removeBatchEffect`

QC figures (before vs after batch correction) are stored under:
- `results/batch/limma_pca_after_with_removeBatchEffect`
- `results/batch/limma_removeBatchEffect`

(If you re-run the pipeline, regenerate these figures to confirm batch separation is reduced without collapsing group structure.)

---

