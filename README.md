# Analyzing-Crime-in-Los-Angeles
# 🚓 LAPD Crime Data Analysis  

![Python](https://img.shields.io/badge/Python-3.9-blue)  
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-yellowgreen)  
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange)  
![Seaborn](https://img.shields.io/badge/Seaborn-Charts-blueviolet)  
![ReportLab](https://img.shields.io/badge/ReportLab-PDF%20Reports-lightgrey)  
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)  

---

## 📊 Overview  

Los Angeles, California, is one of the most vibrant and diverse cities in the world — but with its size and activity comes crime.  
This project analyzes **crime data from the Los Angeles Police Department (LAPD)** to identify **patterns in criminal behavior** and provide **data-driven recommendations for resource allocation**.  

### Key Questions Answered:
- ⏰ What time of day do crimes peak?  
- 🌃 Which areas have the highest crime rates at night?  
- 👥 Which age groups are most vulnerable?  

---

## 📂 Dataset  

- **Source:** Modified version of [Los Angeles Open Data – Crime Data](https://data.lacity.org/)  
- **File:** `crimes.csv`  
- **Size:** ~ 100,000 × 12 (rows × columns)  
- **Key Columns:**  
  - `DATE OCC` → Date of occurrence  
  - `TIME OCC` → Time (24-hour format)  
  - `AREA NAME` → Geographic patrol area  
  - `Crm Cd Desc` → Crime description  
  - `Vict Age` → Victim age  
  - `Vict Sex` → Victim gender  
  - `LOCATION` → Street address of the crime  

---

## 🛠️ Tools & Libraries Used  

- **Python** → Data cleaning & analysis  
- **Pandas, NumPy** → Data wrangling & transformation  
- **Matplotlib, Seaborn** → Data visualization  
- **ReportLab** → Automated PDF reporting  
- **Jupyter Notebook** → Interactive exploration  

---

## 📈 Methodology  

1. **Data Preparation**  
   - Cleaned raw dataset  
   - Extracted time features from `TIME OCC`  
   - Created victim age groups  

2. **Exploratory Data Analysis (EDA)**  
   - Visualized crime frequencies by **hour, area, and age group**  
   - Identified **nighttime hotspots**  

3. **Findings & Insights**  
   - Peak crime hour occurs at **12 PM (noon)**  
   - Night crimes (8 PM – 5 AM) cluster in specific areas such as **Downtown Los Angeles**  
   - Most vulnerable victims are **young adults (18–44 years old)**  

4. **Report Generation**  
   - Summarized findings in a **professional PDF report** with charts  

---

## 🔍 Key Insights  

✔️ **Crimes peak at noon** → Suggests reallocating daytime patrols.  
✔️ **Top night crime hotspots** → Downtown & nearby areas, requiring focused patrols.  
✔️ **Young adults (18–44)** are most targeted → Awareness campaigns should focus on them.  

---

## 📊 Sample Visualizations  

| Crimes by Hour | Top 5 Areas with Night Crimes | Victim Age Groups |
|----------------|-------------------------------|------------------|
| ![Crimes by Hour](./images/crimes_by_hour.png) | ![Night Crimes](./images/night_crimes_top5.png) | ![Victim Age Groups](./images/victim_age_groups.png) |

---

## 🚀 How to Run the Project  

1. Clone the repository:  

   ```bash
   git clone https://github.com/YourUsername/lapd-crime-analysis.git
   cd lapd-crime-analysis
