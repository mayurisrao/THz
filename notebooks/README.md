# Notebooks

This directory contains the primary Jupyter notebooks used in **Singh, Sathyanarayana Rao, & Basu Thakur (2026)** (*AJ*, 171, 331; [DOI: 10.3847/1538-3881/ae5e4e](https://doi.org/10.3847/1538-3881/ae5e4e)).

## Directory Layout

- **`clean/`** — Output-stripped, section-organized versions of the notebooks intended for clean version control, code reading, and re-execution:
  - `pressure_level_analysis.ipynb`: Global PWV computation ($M2$), IAO–Hanle validation against 220 GHz radiometer records, Ladakh grid-wise surface pressure and $\text{PWV} \le 1\text{ mm}$ survey ($M3$), wind/cloud checks, and ESA ~30 m DEM elevation distributions.
  - `alma_mauna_kea_comparison.ipynb`: Validation of ERA5 PWV estimation methods ($M1$, $M2$, $M3$) against in situ radiometer datasets at Mauna Kea and ALMA (Chajnantor).
  - `am_radiative_transfer_config.ipynb`: Extracts site-level `o3`/`q`/`t` profiles from `data/era5/o3_q_t_ladakh.nc`, generates `am` configuration (`.amc`) files for All-month and NDJF winter quantiles, runs `am`, plots transmittance $t_x(\nu)$ and brightness temperature $T_b(\nu)$ spectra, and computes $\nu_{0.8}$ limiting frequencies.
- **`executed/`** — Original notebooks preserving all saved cell outputs, tables, and inline figures (`pressure_level.ipynb`, `alma_mauna_kea_comparison.ipynb`, `am_radiative_transfer_config.ipynb`).

## Execution Notes

- The notebooks in `clean/` include a top setup cell that automatically sets the working directory to the repository root so relative paths (e.g., `data/...`, `radiative_transfer/...`) resolve regardless of where Jupyter is launched.
- `pressure_level_analysis.ipynb` and `alma_mauna_kea_comparison.ipynb` reference large external ERA5/MERRA-2 NetCDF cubes and an ESA DEM GeoTIFF that are not bundled in Git; see [`../data/README.md`](../data/README.md) for details.
