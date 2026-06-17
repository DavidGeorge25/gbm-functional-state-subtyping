# GBM Iavarone state subtyping (v1)

Single-cell analysis of the Mikolajewicz GBM snRNA-seq cohort. Tumour cells are classified into four Iavarone functional states (GPM, MTC, NEU, PPR), then we test whether glycogen phosphorylases **PYGL** and **PYGB** are enriched in the metabolic **GPM** state.

## Requirements

- **R** (4.2+ recommended)
- **Quarto** CLI ([install](https://quarto.org/docs/get-started/))
- R packages: `Seurat` (v5), `tidyverse`, `ggplot2`, `patchwork`, `UCell` (Bioconductor; optional, falls back to `AddModuleScore`)

```r
install.packages(c("Seurat", "tidyverse", "ggplot2", "patchwork", "quarto"))
if (!requireNamespace("BiocManager", quietly = TRUE)) install.packages("BiocManager")
BiocManager::install("UCell")
```

## How to run

From the project root:

```bash
quarto render analysis.qmd
```

This writes `analysis.html` and saves figures to `figures/`.

In RStudio: open `analysis.qmd` and click **Render**.

## Input files (`data/`)

| File | Description |
|------|-------------|
| `gbm_seurat.rds` | Processed Seurat object (~10⁵ cells, 18 patients) |
| `iavarone_signatures.csv` | 4×~13 gene signatures (GPM, MTC, NEU, PPR) |
| `mikolajewicz_metadata.csv` | Per-cell metadata (optional; also in Seurat `@meta.data`) |

## Output figures (`figures/`)

| Figure | What it shows |
|--------|----------------|
| `umap_states.png` | UMAP of tumour cells coloured by Iavarone state |
| `pseudobulk_PYGL_PYGB_by_state.png` | Patient-level mean PYGL/PYGB expression by state |

## Summary

GBM tumour cells occupy distinct functional states, including a glycolytic/plurimetabolic **GPM** program from Iavarone et al. We score each malignant cell against four published signatures and assign a winner-take-all state label. The lab hypothesis is that **PYGL** and **PYGB**, which mobilise glycogen for energy, should be enriched in GPM. Pseudobulk comparisons across ~18 patients test that without treating cells from the same biopsy as independent replicates.

## Project layout

```
Glioblastoma/
├── analysis.qmd          # Main Quarto notebook (render this)
├── README.md
├── data/
└── figures/              # PNG outputs (created on render)
```
# gbm-functional-state-subtyping
# gbm-functional-state-subtyping
# gbm-functional-state-subtyping
