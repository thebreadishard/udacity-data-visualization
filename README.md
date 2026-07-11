# PAH Data Visualization

Udacity **Data Visualization** project (Parts I & II), developed locally in VS Code.
It explores a combined dataset of **polycyclic aromatic hydrocarbons (PAHs)** and
builds toward a per-molecule "fact sheet" that links molecular structure to the
molecule's infrared (IR) emission spectrum.

## Dataset

The data is the cleaned, combined output of a prior data-wrangling project
([thebreadishard/udacity-data-wrangling](https://github.com/thebreadishard/udacity-data-wrangling)),
which merged two related sources:

- **NASA Ames PAHdb** (theoretical IR spectroscopic database) — emission-line
  frequencies and intensities.
- **PubChem** (PUG REST API) — molecular structure and properties.

| File | Rows × Cols | Description |
| --- | --- | --- |
| `data/clean/pah_molecules_clean.csv` | 1136 × 12 | One row per molecule (per charge state): `MolecularWeight`, `HeavyAtomCount`, `n_lines`, `charge_state`, `SMILES`, `InChIKey`, `IUPACName`, … |
| `data/clean/pah_transitions_clean.csv` | 22710 × 3 | Tidy emission lines: `uid`, `frequency` (cm⁻¹), `intensity` |

The cleaned CSVs are the analysis **input**, carried over unchanged from the
wrangling project. The raw PAHdb XML (`data/raw/`, ~480 MB, git-ignored) is the
source for the stand-out goal's structure/spectrum work.

## Project structure

```
DataVisualization/
├── data/
│   ├── clean/            # cleaned CSVs — analysis input (tracked; small)
│   └── raw/              # raw PAHdb XML source (git-ignored; ~480 MB)
├── notebooks/
│   ├── Part_I_exploration_template.ipynb    # exploratory analysis (7 visualizations)
│   └── Part_II_explanatory_template.ipynb   # explanatory analysis (3–5 polished plots)
├── outputs/              # generated fact-sheet PDFs (git-ignored)
├── requirements.txt
├── .python-version       # pinned Python (3.14)
├── LICENSE               # MIT
└── README.md
```

## Goals

**Rubric (required):** Part I is a structured exploratory analysis with exactly
seven visualizations (univariate → bivariate → multivariate) using the
Question–Visualization–Observations framework; Part II turns the strongest
findings into 3–5 polished, presentation-quality plots. Both notebooks are
exported to HTML/PDF for submission.

**Stand-out goal:** A one-page A4 **PDF fact sheet per molecule** containing the
molecule's details, a 2D structure diagram (colored atoms + bonds), and its IR
emission stick spectrum. In the notebook (not the PDF), an interactive view lets
you enter a molecule by id and **click a spectral line to see the responsible
atoms vibrate**. Rubric work is built as reusable functions that also feed this
goal.

## Setup (local)

Create and activate the virtual environment (Python 3.14), then install
dependencies:

```powershell
py -3.14 -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

Open the notebooks under `notebooks/`, select the `.venv` kernel, and Run All.

## License

MIT — see [LICENSE](LICENSE).
