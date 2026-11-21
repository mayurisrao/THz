# Contributing

Contributions, bug fixes, and extensions to the submillimeter/THz site-characterization workflows are welcome!

## Repository Conventions

- **Notebooks (`notebooks/`):**
  - Place runnable, output-stripped notebooks with clean section headings under `notebooks/clean/`.
  - Keep saved-output reference snapshots (if needed) under `notebooks/executed/`.
  - Use relative paths anchored at the repository root (see the top working-directory setup cell in `notebooks/clean/*.ipynb`).
- **Radiative Transfer (`radiative_transfer/`):**
  - Store shared `am` pressure levels, preambles, and site metadata files in `radiative_transfer/am_config_templates/`.
  - Store per-site inputs/outputs in `radiative_transfer/sites/<site>/`.
- **Datasets (`data/`):**
  - Avoid committing large (>50 MB) raw reanalysis or DEM files directly to Git; document external data sources in `data/README.md` instead.
- **Hygiene:**
  - Do not commit `.DS_Store`, `.ipynb_checkpoints/`, or machine-specific local paths.

## Submitting Changes

1. Fork `mayurisrao/THz` and create a feature branch from `main`.
2. Make focused, well-described commits.
3. Verify that all modified `.ipynb` files are valid JSON and all relative links in Markdown docs resolve.
4. Open a Pull Request against `mayurisrao/THz:main` describing the motivation and changes.
