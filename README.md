# Project 6 - Exploratory Data Analysis (EDA)

## Author
Brendon McNulty

## Repository Setup
- Created new GitHub repo `datafun-06-eda` with default README.md
- Cloned repo to local machine into Documents folder
- Added `.gitignore` file (based on instructor’s example)

## Commands Used
```bash
git clone https://github.com/yourusername/datafun-06-eda.git
cd datafun-06-eda
```

## Requirements

This project uses external packages not included in the Python Standard Library.  
They are listed in the `requirements.txt` file:

```
jupyterlab
pandas
pyarrow
matplotlib
seaborn
```

To install all requirements into your active virtual environment, run:

```bash
pip install -r requirements.txt
```

## Notebook Setup

- Created new Jupyter Notebook file `brendon_eda.ipynb`.
- Selected the project-specific kernel: `.venv (3.13.7)`.
- Added an introduction Markdown cell with project title, author, date, and purpose.
- Added an import cell with pandas, seaborn, and matplotlib.

## Data Acquisition

- Downloaded dataset from Kaggle: [March Madness Statistical Analysis (2002–2025)](https://www.kaggle.com/datasets/jonathanpilafas/2024-march-madness-statistical-analysis)  
- Saved the full dataset (`march_madness_2002_2025.csv`) in `data/raw/` (ignored by GitHub for size).  
- Added a `.gitkeep` file so the `raw` folder is still tracked in GitHub.  
- Created a **processed dataset** (`march_madness_2015_2025.csv`) stored in `data/processed/` for analysis.  
  - Includes **season**, **conference**, **adjusted offense efficiency (AdjOE)**,  
    **adjusted defense efficiency (AdjDE)**, **adjusted tempo**,  
    and a new column **eff_diff** (AdjOE − AdjDE).  

### Dataset Description
The dataset contains historical NCAA March Madness statistics for all major conferences from **2002–2025**.  
The processed dataset trims this to **2015–2025** and focuses on key efficiency metrics.  

Key columns in the processed file:  
- **season** → Year of the season (2015–2025).  
- **conference** → NCAA conference (e.g., SEC, ACC, Big Ten).  
- **adj_off_eff** → Adjusted Offensive Efficiency (points scored per 100 possessions, adjusted).  
- **adj_def_eff** → Adjusted Defensive Efficiency (points allowed per 100 possessions, adjusted).  
- **adj_tempo** → Adjusted Tempo (average possessions per game).  
- **eff_diff** → Net efficiency = offense − defense.  

### Notes  
- Analysis will focus on **offense vs. defense balance**, **tempo differences**, and **conference-level trends over time**.  

## Exploratory Data Analysis Progress

### Data Processing
- Slimmed raw dataset (165 columns) to focus on key metrics:
  - `season`, `conference`, `adj_off_eff`, `adj_def_eff`, `adj_tempo`, and `eff_diff`
- Filtered dataset to include seasons 2015–2025 only
- Saved to `data/processed/march_madness_2015_2025.csv`

### Initial Data Inspection
- Viewed first 10 rows of the processed dataset
- Checked shape, data types, and summary statistics
- Confirmed dataset contains meaningful variation across conferences and seasons

### Initial Distributions
- Created histograms for:
  - Adjusted Offensive Efficiency (`adj_off_eff`)
  - Adjusted Defensive Efficiency (`adj_def_eff`)
  - Adjusted Tempo (`adj_tempo`)
  - Efficiency Differential (`eff_diff`)
- Added observations:
  - Offense generally ranges 100–115, with some >120 outliers
  - Defense mostly 95–110, with weaker conferences >115
  - Tempo clustered around 65–70 possessions per game
  - Efficiency Differential centered near 0, with both positive and negative extremes
