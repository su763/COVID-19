 COVID-19
This dataset collection tracks the early 2020 COVID-19 pandemic. It contains files covering global daily totals, country-specific daily time series, a detailed country snapshot with population/testing data, and a granular file for US counties. It's ideal for time-series, predictive, and geographical analysis.
# COVID-19 Global Analysis & Death Toll Prediction

This data science project analyzes the global spread of the COVID-19 pandemic (using data from early 2020) and builds a machine learning model to identify and predict the key factors contributing to a country's total death toll.

The analysis is broken into three parts:
1.  **Global Time-Series Analysis: Visualizing the pandemic's growth over time.
2.  **Predictive Modeling & EDA: Using country-level data to predict `TotalDeaths` and find the most important contributing factors.
3.  **Geographical Analysis:** Creating an interactive world map to show pandemic hotspots.

![Correlation Heatmap](correlation_heatmap.png)
*(This README assumes you have saved the output images like `correlation_heatmap.png` in the same repository)*

## Datasets Used

This project analyzes a collection of 6 CSV files. The three primary files used for the analysis are:

* `worldometer_data.csv`: The main dataset for the predictive model. This is a snapshot of country-level statistics, including key features like `Population`, `TotalCases`, `TotalTests`, and `Serious,Critical` cases.
* `day_wise.csv`: A global time-series file. Each row represents one day's total `Confirmed`, `Deaths`, and `Recovered` cases for the entire world.
* `covid_19_clean_complete.csv`:** A detailed daily time-series file for each country/region. Its most important feature is the `Lat` and `Long` coordinates, which are used for the geographical map.
* **Other Files: `country_wise_latest.csv`, `full_grouped.csv`, and `usa_county_wise.csv` provide supplementary or more granular data (e.g., US counties) that can be used for further exploration.

## Project Analysis & Structure

### Part 1: Global Time-Series Analysis
* Analyzed the `day_wise.csv` dataset to visualize the cumulative growth of global confirmed cases, deaths, and recoveries over time.
* Plotted the daily new cases to identify the pandemic's waves.

### Part 2: Exploratory Data Analysis (EDA) & Predictive Modeling
This part used the `worldometer_data.csv` file to predict `TotalDeaths`.

* Preprocessing:
    * Handled missing values using median (for numerical features) and most-frequent (for categorical features) imputation.
    * Encoded categorical features (`Continent`, `WHO Region`) using Scikit-learn's `OneHotEncoder`.
* Exploratory Data Analysis (EDA):
    * Created a histogram of `TotalDeaths` (both normal and log-transformed) to understand its distribution.
    * Generated a bar chart of the Top 15 countries by total deaths.
    * Plotted a correlation heatmap to identify multicollinearity and relationships between features.
* **Predictive Modeling:**
    * Built a **Random Forest Regressor** model to predict `TotalDeaths`.
    * The dataset was split into an 80% training set and a 20% testing set.

### Part 3: Geographical Analysis
* Used the `covid_19_clean_complete.csv` dataset to get the latest case numbers for each country.
* Created an interactive **Plotly scatter-geo map** to visualize the number of confirmed cases (by dot size) and total deaths (by dot color) across the world.

## Key Findings & Results

* Model Performance: The Random Forest model performed well, achieving an **R-squared ($R^2$) of 0.747**. This indicates that the model was able to explain ~74.7% of the variance in total deaths using the features provided.
* **Most Contributing Factors:** The model's feature importance analysis revealed the **Top 5 factors** for predicting COVID-19 deaths:
    1.  `TotalCases` (29.2% importance)
    2.  `TotalRecovered` (16.0% importance)
    3.  `Serious,Critical` (15.5% importance)
    4.  `ActiveCases` (14.6% importance)
    5.  `TotalTests` (13.4% importance)

![Feature Importance](feature_importance.png)


## Libraries Used

* **Data Manipulation:`pandas`, `numpy`
* **Visualization: `matplotlib`, `seaborn`, `plotly.express`
* **Machine Learning: `scikit-learn` (sklearn)
