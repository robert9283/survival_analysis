# Survival Analysis of a Car Racing Simulation

## Overview

This project demonstrates survival analysis techniques applied to data generated from a browser-based car racing simulation. In the simulation, cars drive along a track and are subject to random lightning strikes that may destroy them. The distance driven until destruction is treated as the survival time, allowing classical survival analysis methods to be applied and verified against known simulation parameters.

## Project Structure

| File | Description |
|------|-------------|
| `index.html` | Single-team racing simulation (up to 100 cars) |
| `teams.html` | Two-team racing simulation with configurable survival probabilities per team |
| `car_race.qmd` | Quarto notebook containing the full survival analysis |
| `race_results.csv` | Data exported from the single-team simulation |
| `race_results_teams.csv` | Data exported from the two-team simulation |

## Analysis

The Quarto notebook (`car_race.qmd`) is structured in two parts:

### Part 1 — Single Group
- Kaplan-Meier estimation of the survival function
- Fitting an exponential survival model using `flexsurv`
- Visual comparison of the KM curve and the exponential fit

### Part 2 — Two Teams
- Stratified Kaplan-Meier curves by team
- Cox Proportional Hazards model estimating the hazard ratio between teams
- Derivation of the relationship $S_1(t) = S_2(t)^{HR}$ and a survival-survival plot
- Verification of the proportional hazards assumption via Schoenfeld residuals
- Hypothesis test verifying the estimated $\hat{\beta}$ against the known simulation parameter $\beta = \log(1-p)$

Since the data is generated from a simulation with known parameters, the statistical results can be directly verified against the true underlying values, providing a built-in sanity check of the methodology.

## Dependencies

The analysis is written in R and requires the following packages:

```r
install.packages(c("survival", "dplyr", "ggplot2", "ggsurvfit", "flexsurv"))
```

## How to Run

1. Open `index.html` or `teams.html` in a browser to run the simulation and export a CSV
2. Place the exported CSV in the project root
3. Render `car_race.qmd` using [Quarto](https://quarto.org/)
