# PCA from Scratch on African CO2 Emissions

Formative Assignment: Advanced Linear Algebra (PCA). PCA is implemented with **numpy only** (matplotlib for plots). No scikit-learn.

**Notebook:** [`PCA_Africa_CO2_Final.ipynb`](PCA_Africa_CO2_Final.ipynb)
**Data:** [`data/co2_Emission_Africa.csv`](data/co2_Emission_Africa.csv)

## Dataset
CO2 emissions for 54 African countries, 2000-2020: **1,134 rows x 20 columns** (17 numeric, 3 non-numeric: `Country`, `Sub-Region`, `Code`).
It contains real missing values: GDP per capita, GDP per capita PPP, and several emission sources (Transportation, Manufacturing/Construction, Industrial Processes, Fugitive Emissions, ...). `Fugitive Emissions` is missing in about 71% of rows.

## What is in the notebook
| Part | Content |
|---|---|
| Tasks 1-2 | Standardization, covariance matrix, eigendecomposition, sorting, projection, number of components from explained variance, before/after plots, written answers |
| Task 3 | Performance optimization and benchmarking (below) |

### Task 3 summary
1. Four PCA implementations compared: naive loops, vectorized, optimized (`eigh`), SVD (plus a float32 variant).
2. Correctness check: all versions give the same eigenvalues and the same projections (up to sign).
3. Benchmarks on the real data and scaling to 10,000 / 100,000 / 1,000,000 rows and up to 400 features.
4. Chunked (streaming) PCA processes 5,000,000 rows without holding them in memory, and matches the in-memory result.
5. Memory measured with `tracemalloc`; performance graphs are in the notebook.

Exact timings depend on the machine; the notebook prints them each time it runs.

## How to run
**Google Colab:** upload the notebook and `co2_Emission_Africa.csv` to the session (or create a `data/` folder), then *Runtime > Run all*.
**Locally:**
```
pip install numpy matplotlib jupyter
jupyter notebook PCA_Africa_CO2_Final.ipynb
```
Run it from the repo root so `data/co2_Emission_Africa.csv` is found. The notebook also accepts the CSV placed next to it.

## Repository contents
```
.
├── PCA_Africa_CO2_Final.ipynb
├── README.md
├── data/
│   └── co2_Emission_Africa.csv
└── docs/
    ├── task_sheet.pdf                 <- group contribution sheet (official)
    └── contribution_summary_Ariane_Itetero.pdf
```

## Team
| Member | Contribution |
|---|---|
| Olga Ikirezi | PCA / math (Tasks 1-2) |
| Ariane Itetero | Task 3 (optimization, benchmarking), project packaging |
| _add other members_ | _add_ |
