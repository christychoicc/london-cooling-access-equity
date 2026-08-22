# Assessing Spatial Equity in Multimodal Accessibility to Cooling-Effective Urban Green Space: A Case Study of London

## Overview
This repository contains the code used for the dissertation submitted in part requirement for the MSc in the Centre for Advanced Spatial Analysis, Bartlett Faculty of the Built Environment, UCL.



## Repository Structure
```
london-cooling-access-equity/
├── 1_Data_Filter_London.Rmd                              # Markdown code for filtering data sets to London study area only for preprocessing in Google Earth Engine 
├── 1a_Map_Study_Area.Rmd                                 # Mapping Study Area
├── 2_GoogleEarthEngine_LST_Urban_Heat                    # Google Earth Engine code script for London LST; London LSOAs LST; Quantify urban heat (SUHII)
├── 3_GoogleEarthEngine_Greenspace_Buffer_LST             # Google Earth Engine code script for LST of greenspaces > 2ha and its corresponding buffer rings (30m, 0-900m) 
├── 4_Quantify_Park_Cooling.Rmd                           # Park Cooling Indicators; Identify Cooling Effective UGS
├── 5_Multimodal_Travel_Time_r5r.Rmd                      # r5r Travel Time Matrices; Minimum travel time and cumulative opportunity accessibility scores
├── 5a_Map_Travel_Time_Cummulative_Accessibility.Rmd      # Mapping accessibility indicators derived from 5_Multimodal_Travel_Time_r5r.Rmd 
├── 6_Statistical_Analyses.Rmd                            # Statistical Analyses Performing Regression Modelling and Spatial Clustering Analysis
├── Adobe_Illustrator_Buffer_Schematic_Diagram.ai         # Adobe Illustrator file for green space buffer visualisation
├── data/                                                 # Folder containing all data files used for this study, available to download below under Data Availability
├── figures/                                              # Figures presented in the dissertation document
|   ├── Fig1_Study_Area.png
|   ├── Fig2_Methodology_Workflow.jpg
|   ├── Fig3_Spatial_Distribution_LST.png
|   ├── Fig4_Schematic_Diagram.png
|   ├── Fig5_Conceptual_Park_Cooling_Curve_Peng_et_al_2021.jpg
|   ├── Fig6_Origin_Destinations.png
|   ├── Fig7_Statistical_Analyses_Workflow.jpg
|   ├── Fig8_Spearman_Heatmap.png
|   ├── Fig9_Spatial_Distribution_SUHII.png
|   ├── Fig10_Spatial_Distribution_PCI.png
|   ├── Fig11_Minimum_Travel_Time.png
|   ├── Fig12_Cummulative_Opportunity_Accessibility.png
|   ├── Fig13_BiLISA_15_min_LH_Combined.png
|   ├── Fig14_BiLISA_60_min_LH_Combined.png
|   ├── FigC1_Adjusted_PIT_Histograms.png
|   ├── FigD1_BiLISA_15_min_LH.png
|   └── FigD2_BiLISA_60_min_LH.png
```

## Reproducibility

The code scripts are structured in the order in which the analysis was performed. 

### 1. Data Preparation
`1_Data_Preparation.Rmd` pre-process and filter datasets to the Greater London study area, and `1a_Map_Study_Area.Rmd`visualises the study area map and spatial context. 

### 2. Land Surface Temperature (LST) and Quantify Urban Heat
`2_GoogleEarthEngine_LST_Urban_Heat.txt` is a Google Earth Engine script retrieving Landsat-9 LST data and calculates ... and urban heat exposure


### 3. Urban Green Space and Buffer LST 
`3_GoogleEarthEngine_Greenspace_Buffer_LST.txt` is a Google Earth Engine script retrieving Landsat-9 LST data for urban green spaces and surrounding buffer rings for park cooling analysis

### 4. Quantify Park Cooling
`4_Quantify_Park_Cooling.Rmd` visualises spatial distribution of LST and urban heat exposure, calculates park cooling indicators and identifying cooling-effective urban green spaces

### 5. Multimodal Accessibility
`5_Multimodal_Accessibility_r5r.Rmd` computes multimodal travel time matrices and accessibility indicators to cooling-effective urban green spaces using `r5r`, the corresponding visualisations are in `5a_Map_Travel_Time_Cumulative_Accessibility.Rmd`

### 6. Statistical Analyses
`6_Statistical_Analyses.Rmd` performs statistical analyses for this study, including regression, spatial regression modelling and local indicators of spatial association analyses to assess accessibility equity. 


## Data Availability

Large data files exceeding GitHub's recommended file size limits (50 MB) are not included in this repository.

The full project data can be downloaded here: [Download Project Data](https://liveuclac-my.sharepoint.com/:f:/r/personal/ucfncc0_ucl_ac_uk/Documents/data?d=wdf9102e4c20d400e956e7c03bff41fd0&csf=1&web=1&e=ZZgeIa),
or obtained directly from the below [Data Sources](https://github.com/christychoicc/london-cooling-access-equity#data-sources) section.

After downloading, the project data are to be stored locally under the *data/* directory in the following structure:  
```
data/
├── raw_data/                                             # Raw data for filtering data sets to London study area only for preprocessing in Google Earth Engine 
├── gla/                                                  # Greater London boundary shapefile 
├── lsoa_london/                                          # LSOA boundary shapefile filtered to London only 
├── London_LSOA_LST_SUHI/                                 # LST and SUHII data retreived from Google Earth Engine 
├── London_LST_median.tif                                 # Median LST raster data for Greater London retreived from Google Earth Engine
├── greenspace_london_2ha/                                # Greenspace polygons shapefile filtered to >2ha and London only 
├── greenspace_buffer_LST/                                # Green space LST and Green space Buffer LST (30m, 0-900m) retreived from Google Earth Engine
├── cooling_effective_UGS/                                # 
├── london_lsoa_pop_weighted_centroids/                   # Population weighted centroids for LSOAs
├── origins_destinations/                                 # Origins and Destinations for r5r routing
├── r5r/                                                  # Data folder for r5r 
|   ├── greater-london-260414.osm.pbf                     # Road network data
|   ├── gtfs_rail.zip                                     # Rail GTFS data
|   └── itm_london_gtfs.zip                               # Bus GTFS data
├── r5r_TTM/                                              # r5r raw travel time matrices
|   ├── r5r_TTM_PT_raw.rds                                # r5r computed Public Transit raw travel time matrices
|   ├── r5r_TTM_walk_raw.rds                              # r5r computed Walking raw travel time matrices
|   └── r5r_TTM_cycle_raw.rds                             # r5r computed Cycling raw travel time matrices
├── multimodal_accessibility_lsoa.gpkg/                   # Minimum travel time and cummulative accessibility scores
├── census2021/                                           # Census 2021 raw dataset for population density, age, ethnic groups 
├── IMD_2025.csv                                          # IMD 2025 scores raw dataset
└── map.graph                                             # Adjacency graph for Bayesian BYM2 spatial regression model
```

### Data Sources
Original sources of data used to produce this study are listed as below: 
|Dataset|Reference|
|---|---|
|Greater London Boundary|[Greater London Authority (2018)](https://data.london.gov.uk/dataset/statistical-gis-boundary-files-for-london-20od9/)|
|Lower layer Super Output Areas (December 2021) EW|[Office for National Statistics (2024)](https://geoportal.statistics.gov.uk/datasets/2bbaef5230694f3abae4f9145a3a9800_0/explore?location=52.837550%2C-2.489483%2C6)|
|Landsat 8/9 Collection 2 Level 2|[Earth Resources Observation and Science (EROS) Center. (2020)](https://developers.google.com/earth-engine/datasets/catalog/LANDSAT_LC08_C02_T1_L2)|
|OS Open Greenspace|[Ordnance Survey (2026)](https://www.ordnancesurvey.co.uk/products/os-open-greenspace)|
|OpenStreetMap, Greater London|[Geofabrik and OSM Contributors (2025)](https://download.geofabrik.de/europe/united-kingdom/england/greater-london.html)|
|Bus Open Data Service|[Department for Transport (2026)](https://data.bus-data.dft.gov.uk/timetable/download/)|
|National Rail Timetable Data|[Rail Delivery Group (2026)](https://opendata.nationalrail.co.uk/)|
|Lower layer Super Output Areas (December 2021) EW Population Weighted Centroids|[Office for National Statistics (2026)](https://geoportal.statistics.gov.uk/search?tags=population%2520weighted%2520centroid)|
|Indices of Multiple Deprivation (IMD 2025)|[Ministry of Housing, Communities and Local Government (2025)](https://www.gov.uk/government/statistics/english-indices-of-deprivation-2025)|
|Census 2021|[Office for National Statistics (2021)](https://www.nomisweb.co.uk/sources/census_2021)|