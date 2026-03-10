# Prediction of 1 MeV Electron Fluxes in Low Earth Orbit

This repository contains the implementation of a data-driven pipeline developed for the IPSA course **SP-519 – Space Data Processing**.

The objective of the project is to **predict high-energy electron fluxes (1 MeV) in Low Earth Orbit** using satellite observations and solar wind parameters.

The analysis combines **space environment data processing, statistical analysis, and machine learning modelling**.

## Authors

Gabriel Casarotto  
Andre Hippolyte  

IPSA – Institut Polytechnique des Sciences Avancées  
Academic year 2025–2026

## Scientific Context

Energetic electrons trapped in the **Van Allen radiation belts** can damage satellites through radiation effects such as single-event upsets.

Forecasting electron flux variations is therefore an important problem in **space weather prediction** and satellite risk mitigation. :contentReference[oaicite:1]{index=1}

## Project Objectives

The project aims to:

- Analyse **1 MeV electron flux measurements** from the NOAA-15 satellite.
- Identify high-flux events through statistical analysis.
- Develop predictive models using solar wind parameters.
- Evaluate forecasting performance for short-term horizons.

The prediction horizon studied is **+12 hours**.

## Data Sources

Two main datasets are used:

### NOAA-15 SEM-2

Measurements of **1 MeV electron fluxes** from the SEM-2 instrument.

Variables used:

- Electron flux (P6 channel)
- L-shell magnetic coordinate

Period: **2020–2024**

### OMNI Solar Wind Dataset

Solar and geomagnetic parameters obtained via **SunPy**:

- Solar wind speed (V)
- Interplanetary magnetic field component (Bz)
- Solar radio flux (F10.7)

## Methodology

The project follows several main steps.

### 1. Data Acquisition and Preprocessing

- Automated retrieval of NOAA-15 NetCDF data
- Timestamp reconstruction
- Removal of invalid and outlier values
- Physical filtering of OMNI data
- Aggregation over **12-hour intervals**
- Binning of magnetic L-shell values

### 2. Exploratory Data Analysis

Several visualizations were produced:

- Electron flux time series
- Satellite L-shell trajectory
- L-time diagrams showing radiation belt structure

High-flux events are defined using the **95th percentile threshold** of the flux distribution.

### 3. Machine Learning Modelling

The prediction task focuses on estimating **log10 electron flux at +12h**.

Features used:

- Solar wind speed (V)
- IMF Bz component
- Solar radio flux (F10.7)
- Previous electron flux value

A **Linear Regression model** is trained separately for each L-shell.

## Results

The model performance varies depending on the L-shell.

The best performance is obtained near **L ≈ 4**, corresponding to the core of the outer radiation belt.

Example performance:

R² ≈ **0.86** for L = 4.0

This indicates strong temporal persistence of electron fluxes and demonstrates the predictive value of combining solar wind data with satellite observations.

## Repository Structure
- Notebook_Casarotto_Andre.ipynb # Full analysis and modelling pipeline
- report.pdf # Project report
- README.md

## Tools and Libraries

Python ecosystem:

- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- SunPy

## Future Improvements

Possible extensions include:

- Non-linear models (Random Forest, Gradient Boosting)
- Longer prediction horizons (+24h / +48h)
- Integration of geomagnetic indices (Kp, Dst)
- Development of classification models for event detection

## Academic Project

This project was completed as part of the **SP-519: Space Data Processing course at IPSA**.
