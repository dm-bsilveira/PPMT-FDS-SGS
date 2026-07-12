# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Master's dissertation project for publication in **Natural Resources Reserves** (Springer journal). The project implements a hybrid geostatistical workflow combining Principal Component Analysis (PCA) with Sequential Gaussian Simulation (SGSIM) for mineral property estimation (porosity and permeability).

**Primary objectives:**
- Simplify and organize the code (`PPMT-FDA-SGS.ipynb`, `PPMTs_VARIOGRAMS.ipynb`, `VALIDATION.ipynb`) for journal publication
- Ensure code is accessible and reproducible for journal readers
- Validate all figures and code outputs included in the manuscript
- Comply with Springer publication guidelines

## Key Files & Directories

### Main Notebook
- **PPMT-FDA-SGS.ipynb** - Main analysis notebook (210 cells, ~100k tokens)
  - Data import and exploratory data analysis (EDA)
  - PPMT (Principal Point Moment Transform) preprocessing
  - FDA (Functional Data Analysis) dimensionality reduction
  - Sequential Gaussian Simulation (SGSIM) for property estimation
  - Validation of simulations

### Supplementary Materials (for journal submission)
- **PPMTs_VARIOGRAMS.ipynb** - Supplementary analysis of PPMT variograms
  - Detailed variogram analysis for PPMT-transformed data
  - Theoretical vs. experimental variogram comparisons
  - Parameter validation for SGSIM simulation
  
- **VALIDATION.ipynb** - Supplementary validation and diagnostic analysis
  - Cross-validation results and error analysis
  - Distribution matching for simulated realizations
  - Variogram reproduction assessment
  - Quality control metrics for simulations

### Manuscript & Figures
- **Manuscript_Hybrid_Decorrelation - original.docx** - Dissertation manuscript (needs formatting)

- **figs_for_claude/** - Output figures for manuscript (currently 30+ PNG files)
  - Must be converted to EPS (vector graphics) or TIFF (halftones) per Springer guidelines
  - Must meet resolution requirements (300 dpi for halftones, 600 dpi for combination artwork)

- **04-GSlib/** - GSLib executables (sgsim.exe, vmodel.exe, etc.)
  - External geostatistical simulation tools used in workflow

- **01-Data/**, **20-Correlograma/**, **08-Nscore_back/**, etc. - Data and intermediate results directories

- **old/** - Archive of previous notebook versions (can be removed after finalization)

## Running the Notebooks

**Main workflow** (required):
```bash
jupyter notebook PPMT-FDA-SGS.ipynb
```

**Supplementary analyses** (for journal submission):
```bash
jupyter notebook PPMTs_VARIOGRAMS.ipynb
jupyter notebook VALIDATION.ipynb
```

All notebooks are self-contained with inline data files and external GSLib calls. Execution order within each notebook matters (dependencies between cells). The main notebook must be executed first; supplementary notebooks analyze its outputs.

## Publication Compliance Checklist

### Springer Guidelines (https://link.springer.com/journal/11053/submission-guidelines)

1. **Figure Format & Resolution** (Main notebook + Supplementary materials)
   - [ ] Vector graphics → Convert PNGs to EPS format
   - [ ] Halftones → TIFF format, minimum 300 dpi
   - [ ] Combination artwork → Minimum 600 dpi
   - [ ] Current: All figures from all notebooks are PNG files (need conversion)
   - [ ] Organize figures by notebook origin (main, variograms, validation)

2. **References**
   - [ ] Audit bibliography format in manuscript
   - [ ] Ensure all references comply with Springer standards
   - [ ] Flag non-standard references for correction

3. **Manuscript Formatting**
   - [ ] Update formatting in `Manuscript_Hybrid_Decorrelation - original.docx`
   - [ ] Ensure figure captions and labels are publication-ready

## Code Simplification Goals

When refactoring or documenting code:
- Focus on clarity for journal readers (not just reproducibility)
- Include only figures that appear in the final manuscript
- Remove or archive experimental/deprecated code (see `old/` directory)
- Add comments explaining methodological choices (why PPMT? why FDA? etc.)
- Ensure all hardcoded paths use relative paths for portability

## Data & Processing Pipeline

1. **Input**: Well logs (porosity, permeability) from `01-Data/Set1_wells.prn`
2. **Preprocessing**: PPMT transform for correlation structure analysis
3. **Dimensionality Reduction**: FDA/PCA on transformed data
4. **Simulation**: Sequential Gaussian Simulation using GSLib
5. **Validation**: Cross-validation and distribution/variogram matching

## Notebook Dependencies

Main Python libraries used:
- `pandas`, `numpy` - Data manipulation
- `matplotlib` - Plotting (all figures)
- `scipy` - Statistical functions
- GSLib executables (via subprocess calls)

Note: Some cells call external GSLib programs; ensure `04-GSlib/` directory is present.

## Important Notes

- **Multi-notebook workflow** - Main analysis in `PPMT-FDA-SGS.ipynb` + supplementary materials in separate notebooks for modular submission
- **Relative paths** - Data paths should be relative to notebook location for portability
- **Figure Output** - All visualization cells output PNG files to `figs_for_claude/`; review these for inclusion in manuscript and supplementary materials
- **Validation Cells** - Multiple cells (realizations, distributions, variograms) are for journal validation and should remain despite producing many plots
- **Supplementary Strategy** - Variogram and validation notebooks are supporting analyses that demonstrate rigor and reproducibility for peer reviewers

## Next Steps for Publication

### Main Notebook Simplification
1. Simplify notebook structure (remove experimental cells, consolidate where possible)
2. Add methodological comments explaining each section
3. Ensure all hardcoded paths are relative for reproducibility

### Supplementary Materials Preparation
4. Clean up `PPMTs_VARIOGRAMS.ipynb` and `VALIDATION.ipynb` for clarity
5. Remove experimental cells; keep only publication-ready analyses
6. Convert figures to Springer-compliant format (EPS/TIFF)

### Figure Conversion & Validation
7. Convert all PNG figures from all notebooks to Springer-compliant format (EPS/TIFF)
8. Validate resolution and quality of all included figures
9. Organize figures by source notebook (main, variograms, validation)

### Manuscript Finalization
10. Audit references in manuscript Word document
11. Update figure captions and cross-references for supplementary materials
