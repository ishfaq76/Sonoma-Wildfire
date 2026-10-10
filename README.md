# Urban Energy HW 2: Sonoma County Wildfire Risk Exploration

Partnered assignment for Urban Energy (USF, Fall 2026).

**Collaborators:** [@EnOnl1ne](https://github.com/EnOnl1ne), [@ishfaq76](https://github.com/ishfaq76)

## Contents
- `wildfire_risk_explore.ipynb`: notebook exploring California wildfire risk and expected loss to housing (Open Climate Risk / CarbonPlan data, merged with ACS owner-occupied housing data).

## Setup
The notebook expects the following in the same directory. They are gitignored and not stored in this repo:
- `inputdata/stats.csv` and `inputdata/cb_2025_06_tract_500k/` (CA tract shapefile)
- `census_helper.py` (course-provided module)
- A personal Census API key (https://api.census.gov/data/key_signup.html). Never commit it.

## Workflow
1. `git pull` before you start working.
2. Work on a branch (`git checkout -b your-name/topic`) and open a pull request, or commit small, frequent changes to `main`.
3. Use descriptive commit messages so contributions are easy to follow.
4. Clear or restart-and-run-all notebook outputs before committing to keep diffs readable.
## Steps: Wildfire Risk and Expected Housing Loss, Sonoma County-California
## 1. Introduction
   **Sonoma County**, located in Northern California, faces a significant risk of wildfires due to its mixture of developed communities, wildland areas, and vulnerability to wildfire hazards. Wildfires can lead to considerable losses for residential buildings and other structures, presenting financial risks for homeowners and property owners. Therefore, understanding how wildfire risk varies geographically and how it may change under future climate conditions is essential for climate adaptation, land-use planning, property protection, and insurance planning.

This analysis examines wildfire risk in **Sonoma County** using **parcel-level** wildfire risk estimates aggregated at the **census tract level**. It utilizes data from **CarbonPlan's Open Climate Risk** dataset, which provides estimates of the average annual risk of building loss under both historical and future climate conditions. The dataset includes **census tract identifiers**, **building counts**, and **wildfire risk** estimates that can be integrated with **geographic** and **housing information** to assess the potential financial exposure of properties in different parts of **Sonoma County**.

The analysis will focus on comparing wildfire risk under historical climate conditions with projected risk for the year **2047**. In particular, the variables **rps_2011_mean** and **rps_2047_mean** represent the **tract-level** mean annual risk of loss per structure for the respective climate conditions. The **2047** estimates are associated with an **RCP8.5** scenario, which reflects a **high-end** future climate condition.

The analysis will proceed through four main steps:
1. Load and clean the wildfire risk data while examining the distribution of wildfire risk across census tracts.
2. Map wildfire risk across **Sonoma County** by combining the risk data with the geographic boundaries of census tracts.
3. Integrate wildfire risk with housing characteristics, including **owner-occupied homes** and **median home values** from the American Community Survey.
4. Estimate financial exposure and insurance implications, including the potential value of properties exposed to wildfire risk and the minimum insurance premium required to cover expected losses.

The objective is to identify geographic patterns in wildfire risk within **Sonoma County** and evaluate how future wildfire risk could impact homeowners and property values. The results will provide a quantitative basis for understanding the potential financial consequences of wildfire exposure and for developing climate adaptation and risk management strategies.
## 2. Data and Methodology
## Data Sources
This analysis combines data on wildfire risk, geography, and housing to evaluate wildfire exposure in Sonoma County. The primary dataset for wildfire risk is the **Open Climate Risk (OCR)** dataset developed by **CarbonPlan**. While this dataset provides **parcel-level** estimates of wildfire risk for buildings, this analysis uses the corresponding mean risk estimates at the census ***tract level** to ensure a consistent geographic unit for comparison across Sonoma County. Each observation is identified by an **11-digit** census tract **GEOID** and includes building counts as well as estimates of the annual risk of building loss under both historical and future climate conditions.

The key wildfire risk variables are **rps_2011_mean** and **rps_2047_mean**, which represent the **tract-average** annual risk of building loss under the historical climate of **2011** and the projected climate for **2047**, respectively. The **2047** estimate is based on the **RCP8.5** scenario. Since the risk variables are initially expressed as percentages, they are converted to dimensionless annual probabilities by dividing them by **100**.

Housing and socioeconomic characteristics are derived from the **American Community Survey (ACS)**. This analysis utilizes information on owner-occupied homes and median home values to translate wildfire risk into potential financial exposure for homeowners. Geographic boundaries of census tracts are used to map and spatially analyze wildfire risk across Sonoma County.

## Geographic Selection 
The **OCR** dataset covers the entire United States. The original analysis first converts the census tract GEOID into a standardized 11-digit string and identifies California tracts using the state’s **FIPS code (06)**. 

For this study, the same method is applied to **Sonoma County**, which is identified using its county **FIPS code, 097**, within California's state FIPS code, **06**. Thus, census tracts in **Sonoma County** can be recognized using **GEOIDs** beginning with **06097**. This filtering step produces the subset of census tracts used for analysis in **Sonoma County**.

## Data Cleaning and Processing 
The wildfire risk data is provided in a **CSV** file named *stats.csv*. The first seven rows of this file contain metadata comments and are skipped when importing the data into Python. The analysis uses the pandas library to load and process the dataset.

The following key variables are retained for analysis:  
- **GEOID** — Census tract geographic identifier  
- **building_count** — Number of buildings represented in the tract  
- **rps_2011_mean** — Mean annual wildfire risk under historical climate conditions  
- **rps_2047_mean** — Mean annual wildfire risk under projected climate conditions for 2047  

The risk variables are converted from percentage values into annual probability values, enabling direct use in calculations of expected annual losses.

## Spatial Analysis 
After cleaning the wildfire risk data, the tract-level risk estimates are aligned with census geographic boundaries. Geographic information system **(GIS)** functionality is utilized with GeoPandas, allowing for a spatial visualization of wildfire risk across **Sonoma County**.

Maps are created to compare the spatial distribution of historical wildfire risk with projected wildfire risk for **2047**. This helps identify areas of concentrated wildfire exposure and reveals where anticipated climate conditions may increase the risk of building loss.

## Financial Exposure Analysis  
The final stage integrates wildfire risk data with housing characteristics from the **ACS**. Owner-occupied housing and median home values are analyzed to estimate the financial value of residential properties exposed to wildfire risk.

The analysis focuses on two principal outcomes:  
- **Total Financial Exposure** — An estimate of the value of housing potentially vulnerable to wildfire-related losses.
- **Minimum Required Insurance Premium** — An estimate of the annual premium necessary to cover expected wildfire losses, based on the assessed annual probability of loss and the value of the at-risk property.  

These measures provide a quantitative assessment of the potential economic consequences of wildfire risk for **Sonoma County** homeowners and support discussions on climate adaptation, insurance, and property risk management. This aligns with the stated objective of exploring descriptive statistics that are useful for climate adaptation planning, particularly regarding total financial exposure and minimum required insurance premiums.
## 3. Historical Wildfire Risk
## 4. Future Wildfire Risk
## 5. Geographic Distribution
## 6. Housing Exposure
## 7. 30-Year Compounded Risk
## 8. Highest-Risk Census Tracts
## 9. Insurance Premium Estimate
## 10. Total Financial Exposure
## 11. Home Value vs. Wildfire Risk
## 12. Key Findings and Conclusion
