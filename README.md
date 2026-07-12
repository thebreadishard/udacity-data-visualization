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
│   ├── processed/        # atom geometry extracted from the raw XML (tracked; small)
│   └── raw/              # raw PAHdb XML source (git-ignored; ~480 MB)
├── notebooks/
│   ├── Part_I_exploration_template.ipynb    # exploratory analysis (7 visualizations + bonus)
│   ├── Part_I_exploration_template.html     # exported, with figure alt text
│   ├── Part_II_explanatory_template.ipynb   # explanatory analysis (4 polished plots, incl. 1 interactive)
│   └── Part_II_explanatory_template.html    # exported, self-contained
├── requirements.txt
├── .python-version       # pinned Python (3.14)
├── LICENSE               # MIT
└── README.md
```

## Goals

**Rubric (required):** Part I is a structured exploratory analysis with seven
visualizations (univariate → bivariate → multivariate) plus a bonus structure
render, using the Question–Visualization–Observations framework; Part II turns
the strongest findings into four polished, presentation-quality plots — including
one interactive Plotly chart. Both notebooks are exported to self-contained HTML
(with descriptive figure alt text) for submission.

**Stand-out goal:** A per-molecule **fact sheet** that links structure to
spectrum: one 2D structure diagram (RDKit, coloured atoms + bonds) alongside an
IR emission stick spectrum for **each charge state** the molecule exists in
(anion / neutral / cation). It is a reusable function — enter any molecule `uid`
to render its sheet — shown inline in the notebook (Figure 4).

Two further interactive ideas from the original plan — a rotatable 3D structure
and a "click a spectral line to see the responsible atoms vibrate" view — are
**deferred to the capstone**. They require the per-atom displacement vectors of
each vibrational normal mode, which the PAHdb data does not contain; reproducing
them faithfully means computing the normal modes ourselves (a quantum-chemistry
step). See the Part II conclusions for the full reasoning.

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
