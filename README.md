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

### Conference Distribution
In addition to the numerical distributions, we explored the dataset’s categorical variable: **conference**.  

- A countplot visualization shows how many entries each NCAA conference has in the dataset (2015–2025).  
- Observations:  
  - Power conferences (e.g., ACC, SEC, Big Ten) are heavily represented.  
  - Some mid-major conferences contribute fewer rows, which can lead to more variability in results.  
  - This context is important for interpreting comparisons later in the analysis.  


### Comparative Analyses

#### 1. Conference Efficiency Differential
We compared **net efficiency (offense – defense)** across NCAA conferences (2015–2025).  
- A **boxplot** visualization showed the distribution of performance.  
- Observations: Power conferences (e.g., ACC, Big Ten, SEC) tend to dominate net efficiency, while mid-majors cluster much lower.  

#### 2. Tempo vs Efficiency Differential
We explored the relationship between **pace of play (adjusted tempo)** and **efficiency differential**.  
- A **scatterplot** was generated, colored by conference.  
- Observations: No clear linear trend exists. Some fast-paced conferences achieve positive efficiency, but many do not—suggesting that tempo alone does not drive success.  

#### 3. Trends Over Time (2015–2025)
We tracked **median net efficiency differential by conference** over time.  
- A **lineplot** visualization highlighted how conference-level performance has shifted year to year.  
- Observations: Power conferences remain consistently above average, but mid-major conferences show volatility, with some improving and others declining.  

---

### Spotlight Analysis: Top 5 Conferences by Net Efficiency
To highlight the strongest performers, we calculated the **median efficiency differential** for each conference across 2015–2025.  
- A **bar chart** showcased the Top 5 conferences.  
- Observations: These conferences stand out with sustained competitive advantage, likely driven by stronger recruiting, coaching, and resources.  

### Correlation Heatmap of Key Metrics
To better understand how the main efficiency metrics relate to each other,  
a correlation heatmap was generated.

Key findings:
- **Adjusted Offensive Efficiency** and **Efficiency Differential** are **strongly positively correlated** (r ≈ 0.88).  
- **Adjusted Defensive Efficiency** and **Efficiency Differential** are **strongly negatively correlated** (r ≈ -0.85).  
- **Tempo** shows almost no correlation with performance (r ≈ -0.06).  

This confirms that **two-way efficiency (offense + defense)** is the driving factor in sustained conference success,  
while pace of play has little direct effect on outcomes.

---

### Final Storytelling & Conclusion
This exploratory data analysis (EDA) examined NCAA conference performance (2015–2025)  
through adjusted offense, adjusted defense, tempo, and a derived efficiency differential.  

**Key takeaways:**
- Balance matters: Conferences that maintain strong offense **and** defense achieve the highest net efficiency.  
- Tempo ≠ success: Style of play (fast vs. slow pace) is not a predictor of results.  
- Stability vs. volatility: Some conferences show consistent efficiency year-to-year, while others swing widely.  

**Overall insight:**  
The most successful conferences are those that sustain high offensive output **while limiting opponent efficiency**,  
not those that simply play faster.
