# data-512-course-project
This repository contains the relevant notebooks and documents for the University of Washington's DATA 512 Course Project.

## Project Goal
The goal for the course project was to answer the question:
>(1) Are there any statistically significant associations between our smoke estimation and the 
> prevalence of asthma and high blood pressure for the communities in Rochester, New York 
> amongst all age groups? 

>(2) What is the projected prevalence of asthma and high blood pressure 
> for the next 10 years based on the smoke estimation for Rochester, New York 
> communities amongst all age groups?

In Part 1 we answer the question:
>What are the estimated wildfire smoke impacts on your assigned city each year for 
>the most recent 60 years of wildfire data? 


In addition to the goals for each specific part, the sub-goal of all projects in DATA 512 is to continue
to create code, repositories, and analysis which focus on implementing the best practices described in
["Assessing Reproducibility"](http://www.practicereproducibleresearch.org/core-chapters/2-assessment.html)
and ["The Basic Reproducible Workflow Template"](http://www.practicereproducibleresearch.org/core-chapters/3-basic.html).

## Data Source Information:
`USGS_Wildland_Fire_Combined.json`:

This file is sourced from [sciencebase.gov](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81) and
is one of the two data sets used in the project. This particular source provided the wildfire data which was used
to create a smoke impact estimate for our selected city.

`EPA AQS API`:

This [API](https://aqs.epa.gov/aqsweb/documents/data_api.html) is provided by the US Environmental Protection Agency (EPA) and offers an API which contains
Air Quality Index (AQI) data. The AQI data was used as a comparison point for our smoke impact estimate.

`BRFSS Data`:

For analyzing asthma and high blood pressure prevalence in New York, we utilized the
Behavioral Risk Factor Surveillance System (BRFSS) data which can be found [here](https://data.cdc.gov/Behavioral-Risk-Factors/Behavioral-Risk-Factor-Surveillance-System-BRFSS-P/y4ft-s73h/about_data)
and [here](https://data.cdc.gov/Behavioral-Risk-Factors/Behavioral-Risk-Factor-Surveillance-System-BRFSS-P/dttw-5yxu/about_data).


## Intermediary Files
The project generates multiple intermediary outputs.
- `rochester_daily_aqi_data_1961_2021.csv`: This file contains the daily AQI data for Rochester, NY which was pulled
from the EPA's AQS API. This file was assembled by taking the max AQI on the date.
- `usgs_rochester_processed.csv`: This file contains the wildfire data from the `USGS_Wildland_Fire_Combined.json` for Rochester, NY.
This file specifically is formatted such that each row is a unique fire along with its associated attributes such as
acres burned and the calculated smoke impact estimate.
- `usgs_rochester_impact_per_year.csv`: This file is also derived from the `USGS_Wildland_Fire_Combined.json` for Rochester, NY.
This file specifically is an aggregation of the processed version, where each row is a _Year_ and has a _Total Acres Burned_,
and _Average Smoke Impact_ field. In other words, it is an annual, aggregation, of the `usgs_rochester_processed.csv`.
- `usgs_rochester_impact_per_year_1800miles.csv`: This file is the same as the normal impact per year file, except
it includes fires that are a maximum of 1800 miles away from Rochester, NY rather than 650 miles which is the 
assignment default.
- `brfss_ny_outcomes.csv`: This file is derived from the raw BRFSS data and is filtered down for specifically asthma, high
blood pressure, and New York.

## Folder Structure:
```
data-512-course-project
├── processed_data
│   ├── brfss_ny_health_outcomes.csv
│   ├── rochester_daily_aqi_data_1961_2021.csv
│   ├── usgs_rochester_processed.csv
│   ├── usgs_rochester_impact_per_year.csv
│   └── usgs_rochester_impact_per_year_1800miles.csv
├── docs
├── ├── Part 1 - Common Analysis Visualizations and Reflection.pdf
│   ├── Part 2 - Extension Plan.docx
│   └── Part 4 - Report.docx
├── LICENSE
├── README.md
├── Part 1 - Common Analysis.ipynb
└── Part 2 - Extension Analysis.ipynb
```

