# Submillimeter & Terahertz Site Characterization (`THz`)

[![Published in AJ](https://img.shields.io/badge/Published%20in-The%20Astronomical%20Journal-1f4b99)](https://iopscience.iop.org/article/10.3847/1538-3881/ae5e4e)
[![DOI](https://img.shields.io/badge/DOI-10.3847%2F1538--3881%2Fae5e4e-blue)](https://doi.org/10.3847/1538-3881/ae5e4e)
[![arXiv](https://img.shields.io/badge/arXiv-2604.13487-b31b1b)](https://arxiv.org/abs/2604.13487)

Analysis code, radiative-transfer configurations, datasets, and figures supporting:

> **Site Quality Analysis for an Indian Submillimeter Telescope: A Reanalysis-based Approach**  
> Tanmay Singh, Mayuri Sathyanarayana Rao, and Ritoban Basu Thakur  
> *The Astronomical Journal*, Vol. 171, Issue 6, Article 331 (2026)  
> DOI: [10.3847/1538-3881/ae5e4e](https://doi.org/10.3847/1538-3881/ae5e4e) · arXiv: [2604.13487](https://arxiv.org/abs/2604.13487)

---

## Overview

Ground-based millimeter, submillimeter, and terahertz (THz) astronomy is strongly limited by tropospheric water vapor absorption and emission, quantified by Precipitable Water Vapor (PWV). This repository evaluates the Himalayan plateau of **Ladakh, India**, as a potential host for a science-class submillimeter observatory using:

1. **ERA5 Monthly Reanalysis (January 2010 – April 2025; 184 months)** at 0.25° × 0.25° spatial resolution and 37 pressure levels (1000–1 hPa).
2. **Three PWV Estimation Methods**:
   - **Method 1 ($M1$):** Native ERA5 Total Column Water Vapor (TCWV) product.
   - **Method 2 ($M2$):** Site-specific geopotential-height interpolation (hypsometric surface pressure + monotonic PCHIP vertical integration of specific humidity $q(p)$) for known observatory coordinates and elevations.
   - **Method 3 ($M3$):** Regional native-grid survey using ERA5 grid-cell surface pressure (`sp`) across Ladakh.
3. **Validation against In Situ Observations:** Comparison of ERA5-derived PWV with 220 GHz tipping radiometer measurements at **IAO–Hanle** (1998–2017) as well as published radiometer datasets at **Mauna Kea** and **ALMA (Chajnantor)**.
4. **Radiative Transfer Modeling with [`am`](https://lweb.cfa.harvard.edu/~spaine/am/):** Line-by-line zenith atmospheric transmittance $t_\nu$ and sky brightness temperature $T_b(\nu)$ computed from 10–1000 GHz ($\Delta\nu = 0.025\text{ GHz}$) for four shortlisted Ladakh locations against an APEX reference profile.
5. **High-Resolution Topographic Context:** ~30 m European Space Agency (ESA) Digital Elevation Model (DEM) distributions within the candidate 0.25° × 0.25° ERA5 grid boxes.

---

## Key Candidate Sites & Radiative-Transfer Summary

| Site | Coordinates | ERA5 $P_s$ (mbar) | Months with $\text{PWV} \le 1\text{ mm}$ | $\nu_{0.8}$ All p50 (GHz) | $\nu_{0.8}$ NDJF p50 (GHz) | $\nu_{0.8}$ NDJF p25 (GHz) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **IAO–Hanle** | 32.7789° N, 78.965° E | 585.20 | ~5% (10 / 184) | 290.18 | 312.77 | 314.43 |
| **NLST–Merak** | 33.7828° N, 78.5778° E | 599.18 | ~8% (14 / 184) | 271.75 | 308.15 | 310.93 |
| **Site A** | 34.25° N, 78.75° E | 520.15 | ~23% (43 / 184) | 312.82 | 351.35 | 355.82 |
| **Site B** | 32.50° N, 79.00° E | 535.37 | ~19% | 309.70 | 350.55 | 354.60 |
| **APEX** *(reference)* | 23.01° S, 67.759° W | 555.00 | — | 358.02 | — | — |

Here $\nu_{0.8}$ denotes the highest frequency (in GHz) at which zenith transmittance satisfies $t_\nu \ge 0.8$; **NDJF** refers to the dry winter season (November–February), and **p25 / p50** denote the 25th and 50th percentiles.

---

## Repository Structure

```text
THz/
├── README.md                           # Project overview, methodology, setup, and citation
├── CITATION.cff                        # Machine-readable citation metadata
├── environment.yml                     # Conda environment specification
├── requirements.txt                    # Python pip dependencies
├── docs/
│   └── merra2_download_guide.md        # Earthdata / wget instructions for MERRA-2 downloads
├── notebooks/
│   ├── README.md                       # Guide to paper notebooks and figure mapping
│   ├── clean/                          # Output-stripped, modular notebooks for version control
│   │   ├── pressure_level_analysis.ipynb
│   │   ├── alma_mauna_kea_comparison.ipynb
│   │   └── am_radiative_transfer_config.ipynb
│   └── executed/                       # Original notebooks preserving saved outputs & plots
│       ├── pressure_level.ipynb
│       ├── alma_mauna_kea_comparison.ipynb
│       └── am_radiative_transfer_config.ipynb
├── radiative_transfer/
│   ├── README.md                       # `am` configuration templates, site runs, and outputs
│   ├── am_config_templates/            # Pressure levels, preambles, and site metadata files
│   ├── sites/                          # Site-extracted ERA5 cubes, `.amc` configs, and `.out` spectra
│   └── examples/                       # Standalone `am` tutorial/test files & interactive plotter
├── data/
│   ├── README.md                       # Bundled datasets & external reanalysis/DEM references
│   ├── era5/                           # Regional ERA5 NetCDF subsets (`o3_q_t_ladakh.nc`, etc.)
│   ├── iao_hanle/                      # IAO–Hanle 220 GHz radiometer monthly & yearly PWV tables
│   └── sites/                          # Global & Indian site coordinates and PWV quantile tables
├── results/
│   ├── README.md                       # Catalog of generated figures, comparison maps & animations
│   ├── summary_figures/                # Summary plots and GIFs
│   ├── era5_merra2/                    # ERA5 vs. MERRA-2 correlation, CDF, and map plots
│   └── animations/                     # TCWV regional time-evolution animations
└── legacy/
    ├── README.md                       # Archive of earlier exploratory notebooks & duplicate copies
    ├── notebooks/                      # Pre-paper ERA5 / MERRA-2 exploratory notebooks
    └── duplicates/                     # Preserved duplicate copies from earlier repo layout
```

---

## Notebooks & Paper Reproduction

The primary analysis workflows for the AJ (2026) paper live in [`notebooks/`](notebooks/README.md). Each workflow is provided in two forms:
- [`notebooks/clean/`](notebooks/clean/) — output-stripped and sectioned for clean diffs and re-execution (with automatic working-directory resolution to the repository root).
- [`notebooks/executed/`](notebooks/executed/) — original notebooks retaining embedded cell outputs and inline figures.

| Paper Element | Description | Notebook |
| :--- | :--- | :--- |
| **Figure 1** | Mauna Kea & ALMA (Chajnantor) PWV validation ($M1$, $M2$, $M3$ vs. radiometer) | `alma_mauna_kea_comparison.ipynb` |
| **Figures 2–7, 9 & Table 1** | Global PWV ($M2$), IAO–Hanle validation, Ladakh surface pressure & $\text{PWV} \le 1\text{ mm}$ map, site time series, ESA DEM distributions | `pressure_level_analysis.ipynb` |
| **Figure 8 & Table 2** | `am` config generation, execution, zenith $t_x(\nu)$ & $T_b(\nu)$ spectra, and $\nu_{0.8}$ limits | `am_radiative_transfer_config.ipynb` |

---

## Setup & Installation

### 1. Python Environment

Using **Conda / Mamba** (recommended for geospatial libraries such as `cartopy`, `rasterio`, and `geopandas`):

```bash
conda env create -f environment.yml
conda activate thz-site-analysis
```

Or using **pip** in a Python 3.10–3.12 virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### 2. External Radiative Transfer Code (`am`)

To regenerate atmospheric spectra from `.amc` configuration files (note that precomputed outputs are already included in `radiative_transfer/sites/*/am_output/`), install the Smithsonian Astrophysical Observatory **`am` atmospheric model** by Scott Paine:
- Website & source: https://lweb.cfa.harvard.edu/~spaine/am/
- Ensure the `am` binary is available on your `PATH`.

### 3. External Datasets

Small regional NetCDF slices, site tables, IAO–Hanle radiometer logs, and all `am` site inputs/outputs are included under [`data/`](data/README.md) and [`radiative_transfer/sites/`](radiative_transfer/sites/). Full multi-decade global ERA5 pressure-level cubes and the ~30 m ESA DEM GeoTIFF used in parts of `pressure_level_analysis.ipynb` and `alma_mauna_kea_comparison.ipynb` exceed GitHub file-size limits and should be downloaded separately (see [`data/README.md`](data/README.md) and [`docs/merra2_download_guide.md`](docs/merra2_download_guide.md)).

---

## Citation

If you use this repository in your research, please cite:

```bibtex
@article{Singh_2026_THz,
  author  = {Singh, Tanmay and Sathyanarayana Rao, Mayuri and Basu Thakur, Ritoban},
  title   = {Site Quality Analysis for an Indian Submillimeter Telescope: A Reanalysis-based Approach},
  journal = {The Astronomical Journal},
  year    = {2026},
  month   = jun,
  volume  = {171},
  number  = {6},
  pages   = {331},
  doi     = {10.3847/1538-3881/ae5e4e},
  url     = {https://doi.org/10.3847/1538-3881/ae5e4e},
  eprint  = {2604.13487},
  archivePrefix = {arXiv},
  primaryClass  = {astro-ph.IM}
}
```

You can also use GitHub's **"Cite this repository"** button powered by [`CITATION.cff`](CITATION.cff).

---

## Acknowledgements

T.S. gratefully acknowledges the Visiting Student Program (VSP) at the Raman Research Institute, Bengaluru, India, for supporting this research. This work uses ECMWF ERA5 reanalysis products (Copernicus Climate Data Store), NASA MERRA-2 reanalysis (GES DISC), IAO–Hanle 220 GHz tipping radiometer observations, ESA Copernicus DEM data, and the `am` atmospheric radiative transfer code.
