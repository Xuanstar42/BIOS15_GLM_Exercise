# Modeling the Abundance of *Eulaema nigrita* in the Atlantic Forest

This repository contains the full analysis pipeline used to examine how climatic and 
land-use gradients influence the abundance of the orchid bee *Eulaema nigrita*.

## Project Overview

We analyze how temperature, precipitation, seasonality, forest cover, and land-use 
heterogeneity shape bee abundance across sites in the Brazilian Atlantic Forest.  
Because abundance data were strongly overdispersed, we used a negative binomial GLM with 
sampling effort included as an offset.

## Data

Input file: **Eulaema.csv**

Variables include:

- **Response**  
  - `Eulaema_nigrita` — bee abundance  

- **Climate predictors**  
  - `MAT`, `MAP`, `Tseason`, `Pseason`

- **Land-use predictors**  
  - `forest.`, `lu_het`

- **Sampling method**  
  - `method`

- **Effort**  
  - `effort` (log sampling hours, used as offset)

## Workflow Summary

1. **Initial Poisson GLM**  
   - Overdispersion detected using Pearson residuals  

2. **Negative Binomial GLM**  
   - Fit with `glm.nb()`  
   - Offset term: `log(effort)`  

3. **Environmental Effect Plots**  
   - Generated with `ggeffects` and `ggplot2`  

4. **Land-use Effect Plots**  
   - Forest cover and land-use heterogeneity  

5. **Collinearity Check**  
   - All GVIF values low (1.09–1.27)  

6. **Model Diagnostics**  
   - Residuals vs fitted, Q–Q, leverage plots  
   - No issues detected  

## Repository Contents

- `Eulaema.csv` — raw data  
- Analysis script (formatted R script)  
- `GLM_Plot1.png` — environmental marginal effects  
- `GLM_Plot2.png` — land-use marginal effects  
- `GLM_Plot3.png` — diagonostic plots 

## Required R Packages

```
MASS
ggeffects
ggplot2
patchwork
car
```

## How to Run

1. Place `Eulaema.csv` in the working directory  
2. Run the main R script  
3. Output figures and plots will be generated automatically

---
