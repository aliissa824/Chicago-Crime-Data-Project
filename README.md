# Chicago Crime Analysis (2012-2016)

This repository contains a comprehensive spatio-temporal analysis and predictive modeling of crime patterns in Chicago using **R**.

## Project Objectives
* **Temporal Trends**: Identify major time-based patterns in criminal activity.
* **Hotspot Detection**: Map persistent crime locations and evaluate spatial consistency.
* **Categorical Variation**: Analyze spatial distributions across distinct crime categories.
* **Predictive Modeling**: Develop and validate an ARIMA time-series model to predict short-term crime counts.

## Statistical Workflow
* **Data Cleaning**: Formatting timestamps, handling missing coordinates, and filtering out incomplete years (2017).
* **Normality & Distribution**: Evaluated using Q-Q plots, Shapiro-Wilk tests, Skewness, and Kurtosis.
* **Comparative Analysis**: Utilized t-tests for time-block differences and One-Way ANOVA for weekday variance.
* **Spatial Correlation**: Pearson correlation analysis used to verify hotspot persistence between 2012 and 2016.
* **Categorical Testing**: Chi-squared test for independence between crime types and community areas.
* **Forecasting**: ARIMA modeling with MAPE (Mean Absolute Percentage Error) validation.

## Technologies
* **Language**: R
* **Key Libraries**: `tidyverse`, `sf`, `forecast`, `ggpubr`, `moments`, `lubridate`.

## How to Use
1.  **Download the Data**: Obtain the `Chicago_Crimes_2012_to_2017.csv` and Chicago GeoJSON map files from [Kaggle](https://www.kaggle.com/datasets/currie32/crimes-in-chicago).
2.  **Set Paths**: Update the `file_path` in the notebook to point to your local dataset location.
3.  **Run Notebook**: Open `chicago-crime-data-project-in-r.ipynb` in any Jupyter environment with an R kernel.

## Results Preview
The project includes several visualizations:
* Crime Heatmaps (Weekday vs. Hour)
* Spatial Distribution Maps (Community Area analysis)
* ARIMA Forecast vs. Actual 2016 Data plots
