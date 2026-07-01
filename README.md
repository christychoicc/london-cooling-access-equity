# Assessing Equitable Multimodal Accessibility to Cooling Effective Urban Green Spaces: A Case Study of London

## Data Sources
|Data Type|Name|Description|Source|Purpose|
|---|---|---|---|---|
|Remote Sensing Data|Landsat 8/9 Collection 2 Level 2|Relevant bands will be used to derive LST for summer periods|[View Link](https://developers.google.com/earth-engine/datasets/catalog/LANDSAT_LC08_C02_T1_L2)|Obtain Land Surface Temperature (LST), SUHII and PCI|
|GTFS (Timetable) Data|Bus Open Data Service|Ready-made GTFS feed for bus timetable|[View Link](https://data.bus-data.dft.gov.uk/timetable/download/)|Bus timetable GTFS for r5r|
|Rail Timetable Data|National Rail Timetable Data|Train timetable data to be used alongside bus services, including Elizabeth Line and London Overgrounds|[View Link](https://opendata.nationalrail.co.uk/)|Train timetable to convert to GTFS for r5r|
|Road Network Data|OpenStreetMap, Greater London|Road network data in .pbf format|[View Link](https://download.geofabrik.de/europe/united-kingdom/england/greater-london.html)|Road network for r5r|
|Polygons/ Points|OS Open Greenspace|Accessible greenspace and its access points (parks, playing fields, etc.)|[View Link](https://www.ordnancesurvey.co.uk/products/os-open-greenspace)|Identify greenspace polygons for GEE, accessibility routing destination of greenspace access points|
|Points|Lower layer Super Output Areas (December 2021) EW Population Weighted Centroids|LSOA population weighted centroids points|[View Link](https://geoportal.statistics.gov.uk/search?tags=population%2520weighted%2520centroid)|London LSOA centroids for origins for accessibility analysis|
|Polygons|Greater London Boundary|Greater London Boundary|[View Link](https://data.london.gov.uk/dataset/statistical-gis-boundary-files-for-london-20od9/)|Filter/ clip boundaries to London|
|Polygons|Lower layer Super Output Areas (December 2021) EW |LSOA Boundaries|[View Link]()|Filtered for London LSOAs only|
|Socioeconomic data|Indicies of Multiple Depriviation (IMD 2025)|LSOA-level deprivation indicies for England|[View Link](https://www.gov.uk/government/statistics/english-indices-of-deprivation-2025)|Socioeconomic vulnerability and compare accessibility to cool greenspace across more/ less deprived neighbourhoods|
|Socioeconomic data|Census Data||||

## Repository Structure
```
london-cooling-access-equity/
├── 1_Data_Filter_London.Rmd                 # Markdown code for filtering data sets to London study area only for preprocessing in Google Earth Engine 
├── 2_GoogleEarthEngine_LST_UHI              # Google Earth Engine code script for London LST; London LSOAs LST; SUHII
├── 3_GoogleEarthEngine_greenspace_LST_PCI   # Google Earth Engine code script
├── data/  
├── figures/
|   ├── 
```

## Data Availability
Large data files exceeding GitHub's recommended file size limits (50 MB) are not included in this repository.

The full project data can be downloaded from the following: [Download Project Data](https://liveuclac-my.sharepoint.com/:f:/g/personal/ucfncc0_ucl_ac_uk/IgDHGUhBBPvyQJA3EktcxJIAAWQMLlG2khmJH0eewUCtqys?e=4hTciO)

After downloading, place it in the project directory using the following structure:
```
data/
├── raw_data/                                # Markdown code for filtering data sets to London study area only for preprocessing in Google Earth Engine 
├── greenspace_london/                       # Greenspace polygons shapefile filtered to London only (large file - gitignored)
├── greenspace_london_2ha/                   # Greenspace polygons shapefile filtered to >2ha and London only (large file - gitignored)
├── lsoa_london/                             # LSOA boundary shapefile filtered to London only (large file - gitignored)
├── London_LSOA_LST_UHI/                     # Google Earth Engine retreived LST and SUHII data (large file - gitignored)
├── London_LST_median.tif                    # Google Earth Engine retrieved median LST raster data for Greater London
└── r5r/                                     # Data folder for r5r (large file - gitignored)
    ├── greater-london-260414.osm.pbf        # Road network data
    ├── gtfs_rail.zip                        # Rail GTFS data
    └── itm_london_gtfs.zip                  # Bus GTFS data
```

The analysis and preprocessing code scripts are to be stored locally under *the data/* directory