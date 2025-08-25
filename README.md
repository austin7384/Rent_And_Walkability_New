# The Causal Effect of Neighborhood Walkability on Rental Prices

## Project Overview
This repository contains the code and data for an econometric analysis investigating the causal effect of neighborhood walkability on rental prices. The project uses EPA Walkability Index data, US Census ACS data, and merged crime data to estimate a hedonic pricing model. The primary identification strategy relies on census tract fixed effects and interaction terms to control for unobserved heterogeneity and omitted variable bias.

## Research Question
What is the causal effect of walkability on rental prices, and what happens to that causal effect when there is high crime in the neighborhood?

## Data Sources
1.  **Walkability:** U.S. EPA National Walkability Index (Census Block Group Level)
2.  **Rental Prices:** American Community Survey (ACS) 5-Year Estimates (Table B25064: Median Gross Rent)
3.  **Crime Data:** Gathered from individual city/county sources - Geocoded and aggregated to block groups using the Google Maps API.
4.  **Demographics:** Other relevant tables from the ACS (e.g., income, education, population density).

Most data not in repository due to file being too large.

## Key Steps and Code
1.  **Data Acquisition & Cleaning:** (All notebooks)
    *   Downloaded EPA, ACS, and crime data.
    *   Cleaned column names, handled missing values, and ensured FIPS codes were properly formatted for merging.
2.  **Feature Engineering & Geocoding:** ('01_crime_data_notebooks')
    *   Used the Google Maps API to geocode crime incident addresses and aggregate counts to census block groups.
    *   Merged walkability, rent, crime, and demographic data on Block Group FIPS codes.
3.  **Econometric Analysis:** (`04_Rent_Walk_Analysis.ipynb`)
    *   Estimated OLS models with progressively complex fixed effects (none, state, county).
    *   Added interaction terms to test for causal effect (e.g., walkability * crime_rate).
    *   Conducted robustness checks.

## Results Summary
A positive and statistically significant correlation was found between walkability and median rent. This relationship was attenuated but remained significant after including census tract fixed effects, suggesting that while a causal premium exists, a portion of the raw correlation is driven by unobserved neighborhood characteristics. Rent premium decreased for counties with high violent cirme and high motor vehicle crime. The full results and discussion are available in the final paper.

## How to Reproduce
1.  Clone this repo.
2.  Install dependencies:
3.  Due to file size, ACS data must be acquired manually from the Census Bureau website.
4.  Run the Jupyter notebooks in order.

## Limitations
- The analysis relies on median rent at the block group level, which is an aggregate measure.
- Causality is inferred based on a quasi-experimental design (fixed effects), but unobserved time-varying confounders may remain.
- Limitations discussed heavily in paper and powerpoint
