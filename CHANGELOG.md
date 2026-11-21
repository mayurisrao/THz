# Changelog

All notable milestones and structural updates to this repository are documented in this file.

## [1.0.0] — 2026-06-01 (AJ 2026 Publication Release)

Corresponding publication:  
**Site Quality Analysis for an Indian Submillimeter Telescope: A Reanalysis-based Approach**  
Tanmay Singh, Mayuri Sathyanarayana Rao, and Ritoban Basu Thakur  
*The Astronomical Journal*, Vol. 171, Issue 6, Article 331 (2026) · [DOI: 10.3847/1538-3881/ae5e4e](https://doi.org/10.3847/1538-3881/ae5e4e) · [arXiv:2604.13487](https://arxiv.org/abs/2604.13487)

### Added
- Comprehensive root `README.md` and directory-level `README.md` guides (`notebooks/`, `radiative_transfer/`, `data/`, `results/`, `legacy/`).
- `CITATION.cff` for machine-readable citation metadata.
- `environment.yml`, `requirements.txt`, and `.gitignore` for reproducible Python/Conda environments.
- Repository-root working-directory resolution in `notebooks/clean/*.ipynb`.

### Changed
- Reorganized repository into modular directories (`notebooks/clean/`, `notebooks/executed/`, `radiative_transfer/`, `data/`, `results/`, `docs/`, `legacy/`) with zero deletion of project data, notebooks, figures, or outputs.
- Updated relative paths in `notebooks/clean/am_radiative_transfer_config.ipynb` to match `radiative_transfer/` and `data/era5/o3_q_t_ladakh.nc`.
- Formatted `docs/merra2_download_guide.md` from `download script.md`.
- Removed tracked `.DS_Store` macOS metadata files.

## [0.2.0] — 2025-09 to 2026-04 (Paper Analysis & Radiative Transfer)
- Added ERA5 pressure-level PWV calculations ($M1$, $M2$, $M3$), Mauna Kea & ALMA validation, IAO–Hanle comparisons, and Ladakh grid-wise surveys (`New_Codes/`).
- Added `am` radiative-transfer configuration templates, site-interpolated NetCDF profiles, `.amc` files, and 10–1000 GHz output spectra for Hanle, Merak, Site A, and Site B (`program/`, `sites/`).
- Added `o3_q_t_ladakh.nc` and IAO–Hanle monthly/yearly PWV datasets (`IAO-Hanle/`).

## [0.1.0] — 2022-05 to 2024-01 (Initial Exploratory Work)
- Initial MERRA-2 and ERA5 PWV exploration over Hanle and global reference sites.
- Added early NetCDF reading, altitude/elevation interpolation, visualization notebooks, and MERRA-2 download guide.
