# 🚓 Analyzing Crime in Los Angeles

[![Python](https://img.shields.io/badge/Python-3.9-blue)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-yellowgreen)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-Charts-blueviolet)](https://seaborn.pydata.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org/)
[![ReportLab](https://img.shields.io/badge/ReportLab-PDF%20Reports-lightgrey)](https://www.reportlab.com/)

## 📊 Overview

Los Angeles is a large, highly active city where understanding when, where, and against whom crimes occur can support better operational decisions.

This project analyzes a modified **Los Angeles Police Department (LAPD) crime dataset** to identify patterns in crime occurrence and turn them into practical, data-driven insights for resource allocation and public-safety planning.

### Key Questions

- ⏰ Which hour of the day records the highest frequency of crimes?
- 🌃 Which LAPD area records the highest frequency of crimes during the defined nighttime period?
- 👥 Which victim age groups experience the highest number of recorded crimes?

---

## 📂 Dataset

- **Source:** Modified version of [Los Angeles Open Data – Crime Data](https://www.datacamp.com/datalab/w/fb1992cd-cf01-4cea-a0ad-cd477d93f0c3/edit)
- **File:** [`crimes.csv`](./crimes.csv)
- **Original size:** approximately **185,715 rows × 12 columns**
- **Analysis notebook:** [`Los_Angeles_Crimes_Analysis_RECOVERED.ipynb`](./Los_Angeles_Crimes_Analysis_RECOVERED.ipynb)
- **PDF report:** [`LAPD_Crime_Analysis_Report (1).pdf`](./LAPD_Crime_Analysis_Report%20(1).pdf)

### Key Columns

| Column | Description |
|---|---|
| `DR_NO` | LAPD Division of Records Number |
| `DATE OCC` | Date the crime occurred |
| `TIME OCC` | Time of occurrence in 24-hour military format |
| `AREA NAME` | LAPD geographic patrol area |
| `Crm Cd Desc` | Description of the crime |
| `Vict Age` | Victim age |
| `Vict Sex` | Victim sex |
| `Vict Descent` | Victim descent code |
| `Weapon Desc` | Weapon description, where applicable |
| `Status Desc` | Crime status |
| `LOCATION` | Street location of the crime |

---

## 🛠️ Tools & Libraries

- **Python** — data cleaning, transformation, and analysis
- **Pandas** — tabular data manipulation and aggregation
- **NumPy** — numerical operations and age-bin boundaries
- **Matplotlib** — chart creation
- **Seaborn** — exploratory visualizations
- **Jupyter Notebook** — interactive analysis workflow
- **ReportLab** — PDF report generation

---

## 📈 Methodology

### 1. Data Preparation

The dataset was inspected for structure and missing values before analysis. Rows with missing values in selected low-missingness demographic fields were removed, while fields with substantial missingness, such as weapon descriptions, were retained rather than being discarded automatically.

The analysis also created derived variables, including:

- `HOUR OCC` from `TIME OCC`
- victim age brackets using `pd.cut()`

### 2. Crime Frequency by Hour

The first two digits of `TIME OCC` were extracted and converted into an integer hour.

The hour with the largest number of recorded crimes was identified using frequency counts.

**Finding:** the highest crime frequency occurs at **12:00 PM (noon)**.

### 3. Night Crime Analysis

For the project question, nighttime is defined as **10:00 PM through 3:59 AM**.

Because each extracted integer represents a complete hour, the relevant hours are:

```python
night_hours = list(range(22, 24)) + list(range(0, 4))
# [22, 23, 0, 1, 2, 3]
```

These represent:

- `22` → 10:00 PM–10:59 PM
- `23` → 11:00 PM–11:59 PM
- `0` → 12:00 AM–12:59 AM
- `1` → 1:00 AM–1:59 AM
- `2` → 2:00 AM–2:59 AM
- `3` → 3:00 AM–3:59 AM

Crimes occurring in these hours are filtered and grouped by `AREA NAME`.

**Peak night-crime location:** **Central**.

> Note: an earlier version of the notebook used a wider nighttime window. The project definition above reflects the actual question and should be used when reproducing the final result.

### 4. Victim Age-Group Analysis

Victim ages are grouped into the following ranges:

- `0-17`
- `18-25`
- `26-34`
- `35-44`
- `45-54`
- `55-64`
- `65+`

The age groups are created with `pd.cut()`, using bin boundaries that preserve the required inclusive upper limits.

**Finding:** the **26–34** age group has the highest recorded frequency among the defined victim age groups.

### 5. Reporting and Visualization

The findings are supported with bar charts showing:

- crime frequency by hour
- areas with the highest night-crime frequency
- crime frequency by victim age group

A PDF report is also included in the repository for a concise presentation of the analysis.

---

## 🔍 Key Insights

- **Crime frequency peaks at noon (12 PM).**
- **Central** records the highest frequency of crimes during the project's defined nighttime window.
- The **26–34** victim age group has the highest recorded crime frequency among the age brackets analyzed.
- Time, location, and victim-demographic patterns can help guide more targeted resource allocation and prevention strategies.

> These findings describe patterns in the supplied dataset and should not, on their own, be interpreted as causal relationships or individual-level risk predictions.

---

## 📊 Sample Visualizations

| Crimes by Hour | Top Areas with Night Crimes | Victim Age Groups |
|---|---|---|
| <img width="1023" height="545" alt="Crime frequency by hour" src="https://github.com/user-attachments/assets/94e1bb92-034e-4bd9-974e-4fdf3e74404e" /> | <img width="704" height="520" alt="Top areas with night crimes" src="https://github.com/user-attachments/assets/c4855c75-d355-473e-a01a-abddda45988e" /> | <img width="713" height="493" alt="Victim age groups" src="https://github.com/user-attachments/assets/7efd1071-3c6e-42f5-864b-ce05dc6b3a7f" /> |

---

## 🚀 How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/UCJPENIEL/Analyzing-Crime-in-Los-Angeles.git
cd Analyzing-Crime-in-Los-Angeles
```

### 2. Install the main dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter reportlab
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
Los_Angeles_Crimes_Analysis_RECOVERED.ipynb
```

Then run the notebook cells in order to reproduce the analysis.

---

## 📁 Repository Contents

```text
Analyzing-Crime-in-Los-Angeles/
├── crimes.csv
├── Los_Angeles_Crimes_Analysis_RECOVERED.ipynb
├── LAPD_Crime_Analysis_Report (1).pdf
├── la_skyline.jpg
└── README.md
```

---

## 🎯 Project Skills Demonstrated

This project demonstrates practical experience with:

- exploratory data analysis
- data cleaning and validation
- feature extraction from time data
- categorical binning with `pd.cut()`
- grouping and aggregation with Pandas
- analytical visualization
- interpreting business/public-safety questions with data
- documenting analysis for reproducibility

---

## 📌 Author

**Ugochukwu Joshua Toluwaleke**

- [GitHub](https://github.com/UCJPENIEL)
- [LinkedIn](https://www.linkedin.com/in/joshuaugochukwu/)
