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

## Requirements

This project uses external packages not included in the Python Standard Library.  
They are listed in the `requirements.txt` file:

jupyterlab
pandas
pyarrow
matplotlib
seaborn

To install all requirements into your active virtual environment, run:

```bash
pip install -r requirements.txt

## Notebook Setup

- Created new Jupyter Notebook file `brendon_eda.ipynb`.
- Selected the project-specific kernel: `.venv (3.13.7)`.
- Added an introduction Markdown cell with project title, author, date, and purpose.
- Added an import cell with pandas, seaborn, and matplotlib.

## Data Acquisition

- Downloaded dataset from Kaggle: [March Madness Statistical Analysis (2002–2025)](https://www.kaggle.com/datasets/jonathanpilafas/2024-march-madness-statistical-analysis)
- Saved the full dataset (`march_madness_2002_2025.csv`) in `data/raw/` (ignored by GitHub for size).
- Added a `.gitkeep` file so the `raw` folder is still tracked in GitHub.
- Plan to create a smaller processed dataset (`march_madness_2015_2025.csv`) stored in `data/processed/` for analysis.

### Dataset Description
The dataset contains historical NCAA March Madness statistics for all major conferences from **2002–2025**.  
Each record summarizes conference-level performance metrics for a given season.  

Key columns include:
- **Season** → Year of the season (2002–2025).  
- **Conference** → NCAA conference (e.g., SEC, ACC, Big Ten).  
- **Adjusted Offense** → Offensive efficiency rating (points scored per 100 possessions, adjusted for opponent strength).  
- **Adjusted Defense** → Defensive efficiency rating (points allowed per 100 possessions, adjusted).  
- **Adjusted Tempo** → Average possessions per game (pace of play). 

### Links
- [Kaggle Dataset: March Madness Statistical Analysis (2002–2025)](https://www.kaggle.com/datasets/jonathanpilafas/2024-march-madness-statistical-analysis)

### Notes
- This dataset does not include win/loss records.  
- Analysis will focus on **offense vs. defense balance**, **tempo differences**, and **conference-level trends over time**.  
