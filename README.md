# Hong Kong Public Transport and Commuting Analysis
## Data-Driven Insights into Urban Mobility and Transit Patterns

This project analyzes bus commuting flows and transit accessibility across Hong Kong's 18 administrative districts. By integrating census socio-economic data with Origin-Destination (OD) bus matrices, the project identifies key drivers of public transport usage and predicts commuting patterns using machine learning models.

## Project Overview
The analysis is conducted in two primary technical phases:

1. **Exploratory Data Analysis (EDA):** Includes coordinate transformations, spatial joins of bus stops into administrative districts, and visualization of inter-district commuting flows via heatmaps.
2. **Feature Engineering and Modeling:** Generation of advanced spatial features and socio-economic predictors to model commuting behavior using CatBoost and Random Forest algorithms.

## Key Data Sources
* **Transit Data:** Bus route sequences, fare structures, and stop locations (`FARE.csv`).
* **Census Data:** District-level population density, working population, and median income (`Centaline_Dataset_All.csv`, `DC_21C.CSV`).
* **Commuting Matrices:** Origin-Destination flows representing movement between districts (`OD_Matrix_New.csv`).
* **Geospatial Data:** HKSAR 18-district boundary polygons for spatial mapping and stop-to-district assignment.

## Technical Workflow

### 1. Geospatial Processing
* **Coordinate Conversion:** Transformation of HK1980 Grid coordinates to WGS84 for compatibility with standard mapping libraries.
* **Point-in-Polygon Joins:** Used `geopandas` to programmatically assign bus stops to their respective districts based on boundary data.

### 2. Feature Engineering
* **Distance Metrics:** Calculation of shortest driving distances between districts using `OSMnx` and `networkx` graph theory.
* **Economic Indicators:** Derivation of income differentials and population density to evaluate correlations between economic status and transit routes.
* **CBD Analysis:** Classification of destinations to analyze the influence of Central Business Districts (e.g., Central, Wan Chai) on the transit network.

### 3. Machine Learning and Interpretability
* **Models:** Implementation of **CatBoost** (optimized for categorical district data) and **Random Forest**.
* **Model Interpretation:** Utilization of **SHAP (SHapley Additive exPlanations)** values to interpret model decisions, identifying that distance and bus operator codes are the most significant predictors.

## Installation and Usage

### Prerequisites
The following Python packages are required:

```bash
pip install pandas geopandas shapely pyproj matplotlib seaborn osmnx networkx catboost shap
