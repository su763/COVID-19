# COVID-19 Global Data Analysis

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.0+-orange.svg)](https://scikit-learn.org)
[![Plotly](https://img.shields.io/badge/Plotly-Express-blue.svg)](https://plotly.com)

**Comprehensive Exploratory Data Analysis & Predictive Modeling of Early Pandemic Data**

</div>

---

## 📋 Project Overview

This project performs in-depth analysis of the **early 2020 COVID-19 pandemic** using multiple data sources. It combines **exploratory data analysis (EDA)**, **predictive modeling**, and **geospatial visualization** to understand transmission patterns and predict outcomes.

### Analysis Components

| Component | Description | Tools Used |
|-----------|-------------|------------|
| **Exploratory Analysis** | Global trends, country comparisons, growth patterns | Pandas, Matplotlib, Seaborn |
| **Predictive Modeling** | Random Forest death toll prediction | Scikit-learn |
| **Geospatial Visualization** | Interactive world maps | Plotly Express |
| **Time Series Analysis** | Daily case/death trajectories | Pandas, NumPy |

---

## 🎯 Key Questions Answered

1. **Which countries had the highest case fatality rates?**
2. **What factors best predict COVID-19 deaths?**
3. **How did the pandemic spread geographically over time?**
4. **Can we predict death tolls from country-level indicators?**

---

## 📊 Dataset Description

### Data Sources

| Dataset | Records | Key Variables |
|---------|---------|---------------|
| **Worldometer Data** | ~210 countries | TotalCases, TotalDeaths, Population, Tests |
| **Day-wise Time Series** | Daily snapshots | Date, Confirmed, Deaths, Recovered |
| **US County Data** | 3,000+ counties | State, County, Cases, Deaths |

### Data Files

```
COVID-19/
├── covid_19.ipynb              # Main analysis notebook
├── Untitled5.ipynb             # Exploratory analysis
├── Untitled7.ipynb             # Time series visualization
├── Untitled8.ipynb             # Predictive modeling
├── Untitled9.ipynb             # Geospatial analysis
└── Untitled10.ipynb            # Additional analysis
```

---

## 🔬 Methodology

### Phase 1: Data Preprocessing

```python
# Data cleaning steps
- Handle missing values (interpolation for time series)
- Standardize country names
- Calculate derived metrics:
  - Case Fatality Rate = (Deaths / Cases) * 100
  - Tests per Million = (Tests / Population) * 1,000,000
  - Cases per Million = (Cases / Population) * 1,000,000
```

### Phase 2: Exploratory Data Analysis

```python
# Visualizations created
1. Global cumulative growth curves (log scale)
2. Country-wise comparison bar charts
3. Testing rate vs. case detection scatter plots
4. Mortality rate by age demographics (where available)
5. Heatmaps of correlation between variables
```

### Phase 3: Predictive Modeling

**Target Variable:** `TotalDeaths`

**Features:**
- TotalCases
- Population
- TotalTests
- TestsPerMillion
- CasesPerMillion
- DeathsPerMillion
- Continent (encoded)

**Model:** Random Forest Regressor

```python
from sklearn.ensemble import RandomForestRegressor
from sklearn.model_selection import train_test_split
from sklearn.metrics import r2_score, mean_squared_error

# Train-test split
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# Model training
rf = RandomForestRegressor(
    n_estimators=100,
    max_depth=10,
    random_state=42
)
rf.fit(X_train, y_train)

# Predictions
y_pred = rf.predict(X_test)
```

### Phase 4: Geospatial Visualization

```python
import plotly.express as px

# Interactive choropleth map
fig = px.choropleth(
    df,
    locations="Country/Region",
    locationmode="country names",
    color="Confirmed",
    hover_name="Country/Region",
    animation_frame="Date",
    color_continuous_scale="Reds",
    title="COVID-19 Global Spread Over Time"
)
```

---

## 📈 Results

### Model Performance

| Metric | Score | Interpretation |
|--------|-------|----------------|
| **R² Score** | 0.747 | Model explains 74.7% of variance in deaths |
| **RMSE** | ~850 | Average prediction error in deaths |
| **MAE** | ~320 | Mean absolute error |

### Feature Importance (Top 5)

```
Predicting COVID-19 Deaths:

1. TotalCases          ████████████████████ 29.2%
   └─ Higher cases → More deaths (expected)

2. Population          ██████████████ 18.5%
   └─ Larger populations → Higher absolute deaths

3. TotalTests          ██████████ 12.3%
   └─ Testing capacity correlates with healthcare infrastructure

4. CasesPerMillion     ████████ 9.8%
   └─ Infection rate per capita

5. DeathsPerMillion    ██████ 8.1%
   └─ Baseline mortality indicator
```

### Key Insights

1. **Case Volume Dominates:** Total cases is the strongest predictor (29.2% importance)
2. **Testing Bias:** Countries with higher testing show different detection patterns
3. **Population Effect:** Absolute deaths strongly correlated with population size
4. **Geographic Patterns:** Early hotspots visible in Europe and North America

---

## 🗺️ Visualizations Created

### 1. Global Growth Curve (Log Scale)
```
Confirmed Cases Over Time (Log Scale)

China ━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Italy ━━━━━━━━━━━━━━━━━━━━━━━━
USA   ━━━━━━━━━━━━━━━━━━━━━━
Spain ━━━━━━━━━━━━━━━━━━━━
...
```

### 2. Case Fatality Rate by Country
```
CFR (%) - Top 10 Countries

Belgium     ████████ 14.2%
Italy       ████████ 13.8%
UK          ███████ 12.5%
France      ███████ 11.9%
...
```

### 3. Interactive Map
- Color intensity shows case count
- Animation shows spread over time
- Hover reveals country statistics

---

## 🚀 How to Use This Repository

### Prerequisites

```bash
Python 3.8+
Jupyter Notebook/Lab
```

### Installation

```bash
# Clone repository
git clone https://github.com/su763/COVID-19.git
cd COVID-19

# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn plotly jupyter
```

### Run Notebooks

```bash
# Start Jupyter
jupyter notebook

# Open notebooks in order:
1. Untitled5.ipynb    → Exploratory analysis
2. Untitled7.ipynb    → Time series viz
3. Untitled8.ipynb    → Predictive modeling
4. Untitled9.ipynb    → Geospatial analysis
5. covid_19.ipynb     → Complete analysis
```

---

## 📁 File Structure

```
COVID-19/
├── covid_19.ipynb              # Main comprehensive analysis
├── Untitled5.ipynb             # Initial EDA
├── Untitled7.ipynb             # Time series analysis
├── Untitled8.ipynb             # ML modeling (Random Forest)
├── Untitled9.ipynb             # Plotly visualizations
├── Untitled10.ipynb            # Additional analysis
├── Welcome_To_Colab.ipynb      # Colab-compatible version
└── README.md
```

---

## 📊 Sample Code Snippets

### Load and Explore Data

```python
import pandas as pd
import numpy as np

# Load dataset
df = pd.read_csv('data/worldometer_data.csv')

# Basic statistics
print(f"Total Countries: {df.shape[0]}")
print(f"Total Cases: {df['TotalCases'].sum():,}")
print(f"Total Deaths: {df['TotalDeaths'].sum():,}")
print(f"Global CFR: {(df['TotalDeaths'].sum() / df['TotalCases'].sum() * 100):.2f}%")

# Top 10 by cases
top_10 = df.nlargest(10, 'TotalCases')[['Country/Other', 'TotalCases', 'TotalDeaths']]
print(top_10)
```

### Train Prediction Model

```python
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import r2_score

# Prepare data
X = df[['TotalCases', 'Population', 'TotalTests', 'CasesPerMillion']]
y = df['TotalDeaths']

# Split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train
model = RandomForestRegressor(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

# Evaluate
y_pred = model.predict(X_test)
print(f"R² Score: {r2_score(y_test, y_pred):.3f}")

# Feature importance
for feature, importance in zip(X.columns, model.feature_importances_):
    print(f"{feature}: {importance:.2%}")
```

---

## 🎓 Key Learnings

1. **Data Quality Matters:** Inconsistent reporting across countries affects analysis
2. **Log Scales Essential:** Exponential growth requires log visualization
3. **Per-Capita Metrics:** Raw numbers misleading without population context
4. **Model Limitations:** R² of 0.75 means 25% variance unexplained — other factors matter

---

## 📝 Data Sources

1. **Worldometer** — https://www.worldometers.info/coronavirus/
2. **Johns Hopkins CSSE** — https://github.com/CSSEGISandData/COVID-19
3. **Our World in Data** — https://ourworldindata.org/coronavirus

---

## ⚠️ Disclaimer

This analysis is based on **early 2020 data** and reflects the understanding and data quality of that period. COVID-19 knowledge has evolved significantly since then. This project is for **educational purposes** demonstrating data science techniques.

---

## 🤝 Potential Extensions

- [ ] SEIR epidemiological modeling
- [ ] Vaccination impact analysis
- [ ] Variant tracking and comparison
- [ ] Economic impact correlation
- [ ] Real-time dashboard with API integration

---

## 📄 License

MIT License — Educational/Research Use

---

## 👤 Author

**MD Suhayl Sekander**  
Data Scientist | Computer Science Student, Taylor's University

[![GitHub](https://img.shields.io/badge/GitHub-su763-black?style=flat&logo=github)](https://github.com/su763)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-MD%20Suhayl%20Sekander-blue?style=flat&logo=linkedin)](https://linkedin.com/in/su763)
[![Email](https://img.shields.io/badge/Email-suhayl.sekander27@gmail.com-red?style=flat&logo=gmail)](mailto:suhayl.sekander27@gmail.com)

---

<div align="center">

**Stay safe. Trust the science. ⚕️🔬**

</div>
