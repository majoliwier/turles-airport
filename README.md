# Wildlife Strikes EDA

Exploratory analysis of wildlife strike reports from the
[FAA Wildlife Strikes dataset on Kaggle](https://www.kaggle.com/datasets/faa/wildlife-strikes?resource=download).
Each row represents a reported incident.

## Project structure

```text
.
├── data/
│   └── database.csv    # original dataset
├── eda.ipynb           # analysis and visualizations
├── pyproject.toml      # project dependencies
├── uv.lock             # locked dependency versions
└── .python-version     # Python version used by uv
```

## Run

Install [uv](https://docs.astral.sh/uv/), then run from the project root:

```powershell
uv sync
uv run jupyter lab
```

Open `eda.ipynb` and run the cells in order. In VS Code, select the `.venv`
kernel. Run Jupyter from the project root so the notebook can find the data.

## Analysis

- Data types, missing values, duplicates and reporting trends.
- Airports, animals, flight phases and reported aircraft damage.
- Pearson correlations between height, speed and distance for all rows with
  those three values present.
- All matching turtle reports, analyzed separately by year, state, airport,
  month and species, including changes in data quality over time.

The notebook stores the full turtle records in `turtle_reports` and the
complete correlation records in `complete_records`.

## Notes

- Report counts are not collision rates per flight. Reporting practices may
  change, and the dataset ends in September 2015.
- Missing values are not zero. In particular, missing injury or fatality
  values do not confirm that nobody was hurt.
- Damage rates use only known 0/1 values in `Aircraft Damage`.
- Other columns in the correlation records may still have missing values.
- Turtle counts are small, so yearly and regional comparisons can be unstable.
- Field definitions, codes and units should be checked against the source documentation.
