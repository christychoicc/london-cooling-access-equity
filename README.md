# Multimodal Accessibility and Spatial Inequality in Cooling-Effective Urban Green Space: A Case Study of London

---

## Overview
This is a code repository for the dissertation submitted in part requirement for the MSc in the Centre for Advanced Spatial Analysis, Bartlett Faculty of the Built Environment, UCL.


## Repository Structure
```
london-cooling-access-equity/
├── 1_Data_Filter_London.Rmd                              # Markdown code for filtering data sets to London study area only for preprocessing in Google Earth Engine 
├── 1a_Map_Study_Area.Rmd                                 # Mapping Study Area
├── 2_GoogleEarthEngine_LST_UHI                           # Google Earth Engine code script for London LST; London LSOAs LST; SUHII
├── 3_GoogleEarthEngine_greenspace_buffer_LST             # Google Earth Engine code script for LST of greenspaces > 2ha and its corresponding buffer rings (30m, 0-900m) 
├── 4_Quantify_Urban_Heat_Park_Cooling.Rmd                # Urban Heat and Park Cooling Metrics; Identify Cooling Effective UGS
├── 5_Multimodal_Travel_Time_r5r.Rmd                      # r5r Travel Time Matrices; Minimum travel time and cumulative opportunity accessibility scores
├── 5a_Map_Travel_Time_Cummulative_Accessibility.Rmd      # Mapping accessibility indicators derived from 5_Multimodal_Travel_Time_r5r.Rmd 
├── 6_Statistical_Analyses.Rmd                            # Statistical Analyses Performing Regression Modelling and Spatial Clustering Analysis
├── data/                                                 # Folder containing all data files used for this study, available to download below under Data Availability
├── figures/                                              # Figures presented in the dissertation document
|   ├── Fig1_Study_Area.png
|   ├── Fig2_Methodology_Workflow.jpg
|   ├── Fig3_Mean_LST_Greenspace_2ha_map.png
|   ├── Fig4_Buffer_Schematic_Diagram.png
|   ├── Fig5_Illustration_of_LST_change_curve_of_park_cooling_process_Peng_et_al_2021.jpg
|   ├── Fig6_Origin_Destinations.png
|   ├── Fig7_Spearman_Heatmap.png
|   ├── Fig8_LSOA_SUHII.png
|   ├── Fig9_Cooling_Effective_UGS_PCI_map.png
|   ├── Fig10_Minimum_Travel_Time_by_Mode.png
|   ├── Fig11_Cummulative_Opportunity_Map.png
|   ├── Fig12_BiLISA_15_min_Combined.png
|   ├── Fig13_BiLISA_60_min_Combined.png
|   ├── Fig_Appendix_BiLISA_15_min_Combined.png
|   └── Fig_Appendix_BiLISA_60_min_Combined.png
```

## Data Availability

Large data files exceeding GitHub's recommended file size limits (50 MB) are not included in this repository.

The required full project data can be downloaded here: [Download Project Data](https://liveuclac-my.sharepoint.com/:f:/g/personal/ucfncc0_ucl_ac_uk/IgDHGUhBBPvyQJA3EktcxJIAAWQMLlG2khmJH0eewUCtqys?e=4hTciO)

After downloading, place it in the project directory using the following structure:
```
data/
├── raw_data/                                             # Raw data for filtering data sets to London study area only for preprocessing in Google Earth Engine 
├── gla/                                                  # Greater London boundary shapefile 
├── lsoa_london/                                          # LSOA boundary shapefile filtered to London only (large file - gitignored)
├── London_LSOA_LST_SUHI/                                 # LST and SUHII data retreived from Google Earth Engine (large file - gitignored)
├── London_LST_median.tif                                 # Median LST raster data for Greater London retreived from Google Earth Engine
├── greenspace_london_2ha/                                # Greenspace polygons shapefile filtered to >2ha and London only (large file - gitignored)
├── greenspace_buffer_LST/                                # Green space LST and Green space Buffer LST (30m, 0-900m) retreived from Google Earth Engine (large file - gitignored)
├── cooling_effective_UGS/                                # 
├── london_lsoa_pop_weighted_centroids/                   # Population weighted centroids for LSOAs
├── origins_destinations/                                 # Origins and Destinations for r5r routing
├── r5r/                                                  # Data folder for r5r (large file - gitignored)
|   ├── greater-london-260414.osm.pbf                     # Road network data
|   ├── gtfs_rail.zip                                     # Rail GTFS data
|   └── itm_london_gtfs.zip                               # Bus GTFS data
├── r5r_TTM/                                              # r5r raw travel time matrices
|   ├── r5r_TTM_PT_raw.rds                                # r5r Public Transit raw travel time matrices
|   ├── r5r_TTM_walk_raw.rds                              # r5r Walking raw travel time matrices
|   └── r5r_TTM_cycle_raw.rds                             # r5r Cycling raw travel time matrices
├── multimodal_accessibility_lsoa.gpkg/                   # Minimum travel time and cummulative accessibility scores
├── census2021/                                           # Census 2021 raw dataset for population density, age, ethnic groups 
├── IMD_2025.csv                                          # IMD 2025 scores raw dataset
└── map.graph                                             # Adjacency graph for Bayesian BYM2 spatial regression model
```

The project data are to be stored locally under the *data/* directory

### Data Sources
Original sources of data used to produce this study is listed as below: 
|Name|Description|Source|Purpose|
|---|---|---|---|
|Greater London Boundary|Greater London Boundary|[Greater London Authority (2018)](https://data.london.gov.uk/dataset/statistical-gis-boundary-files-for-london-20od9/)|Filter/ clip boundaries to London|
|Lower layer Super Output Areas (December 2021) EW |LSOA Boundaries|[Office for National Statistics (2024)](https://geoportal.statistics.gov.uk/datasets/2bbaef5230694f3abae4f9145a3a9800_0/explore?location=52.837550%2C-2.489483%2C6)|Filtered for London LSOAs only|
|Landsat 8/9 Collection 2 Level 2|Relevant bands will be used to derive LST for summer periods|[Earth Resources Observation and Science (EROS) Center. (2020)](https://developers.google.com/earth-engine/datasets/catalog/LANDSAT_LC08_C02_T1_L2)|Obtain Land Surface Temperature (LST), SUHII and PCI|
|OS Open Greenspace|Accessible greenspace and its access points (parks, playing fields, etc.)|[Ordnance Survey (2026)](https://www.ordnancesurvey.co.uk/products/os-open-greenspace)|Identify greenspace polygons for GEE, accessibility routing destination of greenspace access points|
|OpenStreetMap, Greater London|Road network data in .pbf format|[Geofabrik and OSM Contributors (2025)](https://download.geofabrik.de/europe/united-kingdom/england/greater-london.html)|Road network for r5r|
|Bus Open Data Service|GTFS feed for bus timetable|[Department for Transport (2026)](https://data.bus-data.dft.gov.uk/timetable/download/)|Bus timetable GTFS for r5r|
|National Rail Timetable Data|Train timetable data to be used alongside bus services, including Elizabeth Line and London Overgrounds|[Rail Delivery Group (2026)](https://opendata.nationalrail.co.uk/)|Train timetable to convert to GTFS for r5r|
|Lower layer Super Output Areas (December 2021) EW Population Weighted Centroids|LSOA population weighted centroids points|[Office for National Statistics (2026)](https://geoportal.statistics.gov.uk/search?tags=population%2520weighted%2520centroid)|London LSOA centroids for origins for accessibility analysis|
|Indicies of Multiple Depriviation (IMD 2025)|LSOA-level deprivation indicies for England|[Ministry of Housing, Communities and Local Government (2025)](https://www.gov.uk/government/statistics/english-indices-of-deprivation-2025)|Socioeconomic vulnerability and compare accessibility to cool greenspace across more/ less deprived neighbourhoods|
|Census 2021||[Office for National Statistics (2021)](https://www.nomisweb.co.uk/sources/census_2021)||