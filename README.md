# Analyzing Crime in Los Angeles

[![Python](https://img.shields.io/badge/Python-3.11-blue)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Analysis-150458)](https://pandas.pydata.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org/)
[![Workflow](https://github.com/UCJPENIEL/Analyzing-Crime-in-Los-Angeles/actions/workflows/execute-analysis.yml/badge.svg)](https://github.com/UCJPENIEL/Analyzing-Crime-in-Los-Angeles/actions/workflows/execute-analysis.yml)

## Project overview

This project explores recorded crime reports in Los Angeles using Python and Pandas. It examines when reports occurred, which LAPD geographic areas had the largest number of reports during a defined night-time window, and how recorded reports are distributed across victim age groups.

The goal is to demonstrate a reproducible data-analysis workflow: inspect the data, validate important fields, define analysis populations explicitly, visualize patterns, and communicate findings with appropriate limitations.

## Questions explored

1. Which hour of the day has the highest number of recorded crime reports?
2. Which LAPD area has the highest number of reports between **10:00 PM and 3:59 AM**?
3. How are recorded reports distributed across the victim age groups 0–17, 18–25, 26–34, 35–44, 45–54, 55–64, and 65+?

## Dataset and provenance

- Repository data file: [`crimes.csv`](./crimes.csv)
- Dataset reference supplied for this project: [Kaggle — Crimes in Los Angeles](https://www.kaggle.com/datasets/sudhanvahg/crimes-in-las-angeles)
- Original public-data context: [Los Angeles Open Data — Crime Data from 2020 to Present](https://data.lacity.org/d/2nrs-mtv8)
- Analysis notebook: [`Los_Angeles_Crimes_Analysis_RECOVERED.ipynb`](./Los_Angeles_Crimes_Analysis_RECOVERED.ipynb)
- Generated report: [`LAPD_Crime_Analysis_Report (1).pdf`](./LAPD_Crime_Analysis_Report%20(1).pdf)

**Provenance note:** the notebook and existing CSV originated from a modified educational analysis dataset. The Kaggle link is recorded as a dataset reference, but the repository does not yet establish a file-level checksum or documented transformation proving that its CSV is byte-for-byte the Kaggle download. The Kaggle reference should therefore not be presented as definitive provenance for every row in the repository file. The Los Angeles Open Data portal provides the upstream public-data context.

The legacy LAPD Crime Data from 2020 to Present dataset is historical: LAPD transitioned to NIBRS-based reporting in March 2024 and the legacy dataset is no longer updated. Do not interpret this repository's extract as live or current crime monitoring.

## Analysis workflow

1. **Load and inspect** — read the CSV using a repository-relative path; review shape, data types, and missingness.
2. **Validate occurrence time** — convert `TIME OCC` safely and retain valid HHMM values only for time-based analysis.
3. **Preserve analytical population** — do not discard records with missing victim sex/descent when answering overall hourly or area questions.
4. **Analyze hourly patterns** — derive the occurrence hour and compare report counts across all 24 hours.
5. **Analyze night-time reports** — use the explicitly defined window 22:00–03:59 and rank LAPD areas by report count.
6. **Analyze victim age groups** — use numeric ages from 0 to 109 and left-inclusive bins so the named groups are represented correctly.
7. **Validate and visualize** — assert key assumptions and export figures for the report.

## Visualizations

The executed notebook exports the following charts to `images/`:

- `01_crimes_by_hour.png` — report counts by hour.
- `02_night_crimes_by_area.png` — top five areas in the defined night window.
- `03_crimes_by_victim_age_group.png` — report counts by victim age group.

## Reproduce the analysis

Requires Python 3.11 or later.

```bash
git clone https://github.com/UCJPENIEL/Analyzing-Crime-in-Los-Angeles.git
cd Analyzing-Crime-in-Los-Angeles
python -m venv .venv
```

Activate the environment, then install dependencies:

```bash
# Windows PowerShell
.venv\\Scripts\\Activate.ps1

# macOS / Linux
source .venv/bin/activate

pip install -r requirements.txt
jupyter notebook
```

Open `Los_Angeles_Crimes_Analysis_RECOVERED.ipynb` and run all cells from top to bottom.

The notebook expects `crimes.csv` in the repository root. The dataset is included in this repository, so no separate download is required for the current version.

## Automated quality checks

GitHub Actions runs when the notebook, dataset, dependencies, or workflow changes. It installs the declared dependencies, executes every notebook cell from a clean state, verifies the saved outputs and three chart exports, regenerates the PDF report, and commits generated artifacts when they change.

You can also start a run manually from the repository's **Actions** tab.

## Interpretation and limitations

- These are counts of recorded reports, not population-adjusted crime rates.
- More reports in an area do not automatically imply a higher individual risk; population, exposure, reporting behaviour, and patrol practices matter.
- The victim-age analysis excludes missing, non-numeric, negative, and 110+ ages. Overall time and area analyses do not require victim demographics.
- Historical datasets may contain transcription errors, missing values, reporting delays, and changing definitions.
- Descriptive associations do not establish causation and should not be used to profile individuals or communities.

## Tools

Python, Pandas, NumPy, Matplotlib, Seaborn, Jupyter Notebook, ReportLab, and GitHub Actions.

## Author

**Ugochukwu Joshua Toluwaleke**

- [GitHub](https://github.com/UCJPENIEL)
- [LinkedIn](https://www.linkedin.com/in/joshuaugochukwu/)
