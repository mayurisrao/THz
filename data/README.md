# Datasets

This directory holds the regional reanalysis subsets, in situ radiometer records, and site catalogs bundled in the repository.

## Contents

- **`era5/`**
  - `o3_q_t_ladakh.nc` (~36.4 MB): Monthly ERA5 pressure-level fields (`o3`, `q`, `t`) over Ladakh used for `am` radiative-transfer profile extraction.
  - `spatially_refined_ladakh.nc`: Spatially refined Ladakh subset from earlier ERA5 analysis.
  - `adaptor.mars.internal-1655727168.606427-18601-13-6d9e5cb6-ff7f-4034-b7f3-b6019b39c9e6.nc`: ERA5 Copernicus CDS sample download.
  - `location.txt`: Reference coordinate pair (`32.971467, 78.592783`).
- **`iao_hanle/`**
  - `hanle_monthly_pwv.txt`: Monthly median PWV and uncertainty (mm) from the IAO–Hanle 220 GHz tipping radiometer.
  - `hanle_yearly_pwv.txt`: Annual PWV statistics (1998–2017) for IAO–Hanle.
- **`sites/`**
  - `Sites.xlsx`: Coordinates and elevations of global and Himalayan reference observatories (ALMA/Chajnantor, Ali, Hanle, Merak, Summit Camp, Mauna Loa/Kea, Dome A, Dome C, Site B).
  - `Indian_Sites.xlsx`: Candidate Indian submillimeter sites (`Site A`, `Site B`).
  - `Pabcd.xlsx`, `PWV_Quantiles_Indian.xlsx`, `PWV_Quantiles_Overall.xlsx`: Derived PWV quartile tables (`Q1: 25%`, `Q2: 50%`, `Q3: 75%`).

## External Datasets (Not Bundled Due to Size)

To re-run the full multi-year global and regional pressure-level notebooks (`notebooks/clean/pressure_level_analysis.ipynb` and `alma_mauna_kea_comparison.ipynb`) from scratch, obtain the following external datasets:

1. **ECMWF ERA5 Monthly Averaged Data** (2010–2025; single levels `tcwv`, `sp`, and 37 pressure levels `q`, `z`, `t`, `o3`) via the [Copernicus Climate Data Store (CDS)](https://cds.climate.copernicus.eu/).
2. **NASA MERRA-2 Reanalysis** via [NASA GES DISC](https://disc.gsfc.nasa.gov/) (see [`../docs/merra2_download_guide.md`](../docs/merra2_download_guide.md) for `wget` download instructions).
3. **ESA Copernicus DEM (~30 m GLO-30)** GeoTIFF tiles covering the candidate Ladakh boxes (`output_hh.tif`).
4. **IAO–Hanle Surface Pressure & Radiometer Climatology** (`hanle_monthly_surface_data.csv`; note that the notebooks fall back gracefully to ERA5 surface pressure if this optional local CSV is absent).
