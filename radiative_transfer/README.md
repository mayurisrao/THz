# Radiative Transfer (`am`)

This directory stores configuration templates, site-specific inputs/outputs, and standalone examples for radiative-transfer modeling using the Smithsonian Astrophysical Observatory **`am` (Atmospheric Model)** code ([Paine 2024](https://lweb.cfa.harvard.edu/~spaine/am/)).

## Structure

- **`am_config_templates/`** — Shared templates and site parameters used by `notebooks/clean/am_radiative_transfer_config.ipynb`:
  - `am_levels.txt` / `am_levels_valeria.txt`: Pressure-level grids (hPa / mbar).
  - `preamble.txt`, `preamble_old.txt`, `preamble_valeria.txt`: `am` header templates specifying frequency range, zenith angle (`za 0 deg`), tolerance (`tol 1e-4`), `Nscale`, and CMB background (`T0 2.7 K`).
  - `metadata/`: Per-site parameter files (`hanle_metadata.txt`, `merak_metadata.txt`, `site_a_metadata.txt`, `site_b_metadata.txt`, `apex_metadata.txt`, plus earlier variants).
- **`sites/`** — Per-site extracted ERA5 profiles and `am` simulation runs for `hanle`, `merak`, `site_a`, and `site_b`:
  - `<site>_data_100.nc`: Interpolated ERA5 (`o3`, `q`, `t`, etc.) over all months.
  - `<site>_data_1000.nc`: Interpolated ERA5 subset restricted to winter months (NDJF: Nov–Feb).
  - `am/*.amc`: Generated `am` configuration files.
  - `am_output/*.out`: Computed spectra over 10–1000 GHz ($\Delta\nu = 0.025\text{ GHz}$) with columns `f (GHz)`, `tau`, `tx`, `Tb (K)`.
  - `am_output/*stderr.out`: Diagnostic stderr logs from `am`.
  - **Naming convention:** `<site>_<period>_<percentile>.*`, where `<period>` is `100` (all months) or `1000` (NDJF winter), and `<percentile>` is `25`, `50`, or `75`.
- **`examples/`** — Early standalone `am` experiment (`example2.1.amc`, `example2.1.txt`, `plot_am.ipynb`, `project_fast.mp4`, and reference plots `graph`, `pwv 0.72`).
