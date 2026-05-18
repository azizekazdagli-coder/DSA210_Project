# DSA210_Project
DSA210 Term Project / Spring 2025-2026

# DSA 210 Project Proposal: Analysis of European Air Traffic Drivers

## Motivation

Air traffic is one of the clearest indicators of international mobility, economic activity, and travel demand. In Europe, countries differ in population size, income level, travel demand, and visa-related mobility conditions. These differences may help explain why some European countries have higher inbound and outbound flight activity than others.

I chose this topic because air travel connects data science with real-world economic and social mobility patterns. By combining flight traffic data with GDP per capita, population, and Schengen visa statistics, this project aims to understand whether socio-economic indicators can explain or predict air traffic differences across European countries.

---

## Overview

This project explores the relationship between European air traffic and socio-economic indicators. The main focus is outbound flights per capita, which allows countries with different population sizes to be compared more fairly. The project uses data processing, visualization, hypothesis interpretation, and machine learning to examine whether population, year, visa acceptance rate, and GDP-based economic tiers are related to air traffic activity.

The final machine learning results show that the Random Forest model performed best, achieving an R-squared score of approximately 0.81. Feature importance analysis shows that population is the strongest predictor of outbound flights per capita, followed by year and visa acceptance rate.

---

## Data to be Used

### European Air Traffic Data

* Data: Inbound and outbound flight traffic data for European countries.
* Features: country, year, inbound flights, outbound flights, population, GDP per capita, inbound flights per capita, outbound flights per capita.
* Purpose: This dataset provides the main air traffic variables used in the analysis.

### Schengen Visa Statistics

* Data: Annual Schengen visa application and issued visa statistics from 2016 to 2024.
* Features: Schengen state/country, visa applications, visas issued.
* Purpose: These files were used to calculate visa acceptance rates and examine whether visa-related mobility indicators are associated with flight traffic.

### Economic and Demographic Data

* Data: GDP per capita and population data.
* Purpose: GDP per capita was used to create economic tiers, while population was used as a predictor and to normalize flight traffic indicators.

---

## Methodology

# Data Cleaning & Integration

* I processed multiple Schengen visa Excel files from 2016 to 2024.
* I extracted the relevant country, visa application, and issued visa columns from each file.
* I calculated the visa acceptance rate using the formula: `Visa Acceptance Rate = (Visas Issued / Visa Applications) × 100`.
* I standardized country names to improve merging accuracy, such as mapping `Czech Republic` to `Czechia` and `Slovak Republic` to `Slovakia`.
* I merged the visa statistics with the main European air traffic dataset using `Country` and `Year`.
* I created a final enriched dataset containing flight traffic, population, GDP per capita, and visa acceptance rate.

# Feature Engineering

* I used per capita flight traffic variables to make countries more comparable.
* I grouped countries into four GDP-based economic clusters using GDP per capita quartiles:
  * Lowest 25%
  * Higher Low 25-50%
  * Lower High 50-75%
  * Highest 25%

# Visualization

* I created a scatter plot showing visa acceptance rate vs. outbound flights per capita by GDP tier.
* I created a timeline visualization showing outbound traffic, inbound traffic, visa acceptance rate, and average population by economic tier.
* I created machine learning plots for model comparison and feature importance.

# Hypothesis Interpretation

* Null Hypothesis: Socio-economic and visa-related indicators do not have a meaningful relationship with outbound flights per capita.
* Alternative Hypothesis: Socio-economic and visa-related indicators are related to outbound flights per capita.
* The exploratory analysis suggests that visa acceptance rate alone does not fully explain air traffic, but GDP-based tiers and population provide important context.

---

## Machine Learning (ML)

In the final phase of the project, I applied machine learning models to test whether socio-economic and visa-related variables can predict outbound flights per capita.

### 1. Mean Baseline

* Goal: Provide a basic comparison point for the other models.
* Result: The baseline model performed poorly, showing that simple average prediction is not sufficient.

### 2. Linear Regression

* Goal: Model a linear relationship between the selected features and outbound flights per capita.
* Result: The model performed moderately, but it could not capture more complex patterns in the data.

### 3. K-Nearest Neighbors Regressor

* Goal: Predict outbound flights per capita based on similarity between country-year observations.
* Result: KNN performed moderately but did not outperform Random Forest.

### 4. Random Forest Regressor

* Goal: Capture non-linear relationships between population, year, visa acceptance rate, GDP tier, and outbound flights per capita.
* Result: The Random Forest model achieved the best performance, with an R-squared score of approximately 0.81.
* Interpretation: The selected features contain meaningful predictive information for estimating outbound flights per capita.

### 5. Feature Importance

* Finding: Population was the most important predictor in the Random Forest model.
* Interpretation: Demographic size strongly influences flight traffic patterns, while year and visa acceptance rate also contribute to the model. GDP clusters are useful for interpretation but less influential in the predictive model.

---

## Limitations & Future Work

* Aggregated Data: The analysis is based on country-level data, so it does not capture airport-level differences or individual travel behavior.
* Visa Statistics: Schengen visa acceptance rates do not represent all travel demand, because many European citizens and residents can travel without applying for a Schengen visa.
* COVID-19 Impact: The years 2020 and 2021 were strongly affected by pandemic-related travel restrictions, which may distort long-term air traffic patterns.
* Missing Variables: The dataset does not include factors such as tourism intensity, ticket prices, airline hub status, airport capacity, geographic location, or business travel demand.
* Future Work: Future versions of the project could include airport-level data, tourism statistics, airline route networks, ticket price indicators, and longer time series data to improve prediction and interpretation.

---

## Project Structure

* `Plots/`: Contains static image files of the visualizations generated during the analysis.
* `data_process.ipynb`: Processes Schengen visa files, calculates visa acceptance rates, merges data, and creates GDP clusters.
* `data_visualization.ipynb`: Generates exploratory visualizations for visa acceptance rate, traffic per capita, and GDP tiers.
* `machine_learning.ipynb`: Builds and evaluates machine learning models for predicting outbound flights per capita.
* `master_dataset_EU_only.csv`: Main dataset containing European air traffic, population, and GDP information.
* `Enriched_Flight_Visa_Data.csv`: Final processed dataset created after merging air traffic data with Schengen visa acceptance rates.
* `requirements.txt`: List of dependencies required to run the notebooks.
* `Report.md`: Final project report containing methodology, results, machine learning analysis, limitations, and conclusion.

---

## AI Usage Disclaimer

In this project, I used AI tools to assist with:

* Coding Support: Debugging Python errors, package installation issues, and notebook path problems.
* Writing Support: Improving the structure and clarity of the README and final report.
* Project Organization: Organizing documentation and preparing GitHub submission files.

All data processing, visualizations, machine learning outputs, and final interpretations were reviewed and validated manually.
