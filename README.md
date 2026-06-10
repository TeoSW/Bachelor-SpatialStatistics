# Spatial Statistics Project — Marriage Rate Analysis in Post-Pandemic Belgium

**Course:** Spatial Statistics
**Author:** Constantin Teodor-Vasile
**Group:** 1067, Series F — ASE Bucharest, ASDS Master's Program

**File:** `ConstantinTeodorVasile_-_Proiect_Statistica_Spatiala.docx`

---

## Overview

This project investigates what caused the marriage rate in Belgium — which had been declining before 2020 — to recover and grow steadily in the post-pandemic years. The analysis is conducted at the **NUTS 3 regional level** for Belgium, for the year **2021**.

> "In 2020, the marriage rate dropped to 5.1 per 1,000 persons. By 2022, it had risen to 6.2 per 1,000." — Madeline Holcombe, CNN (2024)

## Research Question

Did pandemic-induced changes in key demographic variables have a statistically significant **spatial** influence on the marriage rate at NUTS 3 level in Belgium?

## Variables

| Variable | Role | Description |
|---|---|---|
| `rataCasat` — Marriage rate | Dependent (Y) | Marriages per 1,000 inhabitants |
| Fertility rate | Independent | Average children per woman |
| Median age of women at first birth | Independent | Proxy for family planning behavior |
| Population density | Independent | Inhabitants per km² |
| Mortality rate (ages 20–50) | Independent | Deaths per 1,000 in the pandemic-relevant age group |

## Methods & Results

**Moran's I — Spatial Autocorrelation**

All variables show positive spatial autocorrelation (Moran's I > 0):

- `rataCasat` — strong spatial clustering
- Median maternal age — moderate clustering
- Remaining variables — weak clustering

**Model Selection**

OLS regression was tested first. The Robust LM (lag) test returned p = 0.00391 < 0.05, indicating the presence of **spatial lag** — the OLS model is insufficient.

**Final Model: Spatial Lag Regression**

The spatial lag model outperforms OLS with a higher log-likelihood and lower AIC/BIC.

**Key findings:**

- **Population density** and **median maternal age** are the most significant predictors of the marriage rate.
- Median maternal age has a **negative** coefficient — higher median age at first birth is associated with a lower marriage rate.
- Fertility rate and mortality rate contribute very little to explaining the marriage rate.
- Central Belgium (Brussels, Charleroi, Ghent, Antwerp) exhibits high population density and high median maternal age, but a low mortality rate — contrasting with surrounding NUTS 3 regions.
- Where the fertility rate is high, the marriage rate tends to be low, and vice versa (visible in quantile maps).

## Conclusions

Not all pandemic-affected variables directly determine the marriage rate. Population density and median maternal age at birth are the dominant spatial predictors. Despite expectations based on the literature, the mortality rate shows minimal influence. Spatial neighborhood effects are present but vary across indicators.

## Data Sources

| Variable | Source |
|---|---|
| Population density | Eurostat — `demo_r_d3dens` |
| Fertility indicators | Eurostat — `DEMO_R_FIND3` |
| Maternal age at birth | Eurostat — `demo_r_magec3` |
| Marriage statistics | Eurostat — `cens_11ms_r3` |

## References

- Holcombe, M. (2024). *Marriage and divorce rates in the US.* CNN Health.
- *Impact of the COVID-19 pandemic on marriage rates.* Nature Scientific Reports. https://doi.org/10.1038/s41598-024-54679-5
