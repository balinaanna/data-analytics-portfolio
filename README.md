# NYC Traffic Accidents (Jan-Aug 2020)

![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?logo=microsoftexcel&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?logo=pandas&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-3F4F75?logo=plotly&logoColor=white)

The pet project was developed to practice **end-to-end data analysis** using real-world open data. It identifies trends, patterns, and potential risk factors in NYC motor vehicle collisions reported between January and August 2020.

## Dataset

**Source**: [NYC OpenData](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95) - Motor Vehicle Collisions  
**Format**: CSV  
**Rows:** 74,881  
**Columns:** 29  
**Time Period:** January - August 2020  
**Features include:** date/time, location (borough, zip code, lat/lon), street names, vehicles involved, injuries/fatalities, contributing factors

## Excel Analysis

#### 🔗 [View Excel Implementation](./excel_analysis/README.md)

##### Skills Demonstrated

- **Data cleaning** and **wrangling** (formatting, handling missing values)
- **Feature engineering** using **formulas** and **helper columns**
- Aggregation and analysis with **Pivot Tables** and **conditional formatting**
- **Visualization** with combo charts, bar charts, and heatmaps
- **Analytical storytelling** and insight communication through data

## Python Analysis

##### Skills Demonstrated

- **Pandas**-based data cleaning and preparation
- **Feature engineering** for time-based and severity analysis
- **Plotly** interactive visualizations
- **Jupyter** workflow for reproducible analysis
- **Data storytelling** through programmatic EDA

This **Python implementation** transforms static Excel analysis into a **scalable**, **reusable**, and **reproducible** analytics workflow - a critical skillset for modern data roles.

#### 🔗 [01_data_preparation.ipynb](./python_analysis/notebooks/01_data_preparation.ipynb) - Data Cleaning and Feature Engineering

This notebook prepares the dataset for analysis:
**Output** - [nyc_traffic_accidents_clean.csv](./python_analysis/data/nyc_traffic_accidents_clean.csv)

#### 🔗 [02_eda.ipynb](https://balinaanna.github.io/nyc-traffic-accidents/02_eda.html) - Exploratory Data Analysis

This notebook performs the full exploratory analysis on the cleaned dataset.

All visuals are built with **Plotly**, providing interactive charts suitable for screenshots and reports.
