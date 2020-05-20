# drought-tracker
Jupyter-based python project for tracking and describing agricultural droughts.

### Project description
- Purpose: to facilitate tracking of droughted areas based on agronomic metrics.
- Goals: to help non-experts develop evidence-based recommendations for preparing for and mitigating the effects of droughts.
- Desired contribution: Studies, including one by [Diaz et al., 2020](https://www.sciencedirect.com/science/article/pii/S0309170819306542) have demonstrated robust methods to characterize drought dynamics. However, these methods require complex imputs and significant expertise to successfully implement. The deliverable of this project will attempt to simplify the process of describing drought dynamics by using a reproducible workflow in a Jupyter notebook.
- Why use this code? This project will allow for a non-expert (someone familiar with python code) to measure the extent of a drought and how it has moved in a specified time period. The user may be an agronomist, spatial analyst, farmer, or emergency manager for a local government. 

### Workflow
_Note: this workflow will be continuously updated as the project progresses_:
#### Tools/packages
1. [aWhere API (header.py) and account](https://www.awhere.com/)
2. numpy
3. matplotlib
4. geopandas
5. rasterio
6. earthpy
7. pandas
8. requests

### How to run (ea_python_presentation directory)
There are 2 directories required to run all files:
1. data 
 - contains all downloaded data
2. ea_python_presentation
 - contains all Jupyter notebooks and accessory scripts

**Fig 1: Overview Map**
- Obtain state, county, and area of interest vector files
- [Obtain Landsat 8 imagery for area of interest](www.earthexplorer.com)
- In script, correct paths to files (above) if necessary
- Run script to generate overview map; no analysis is performed 

**Fig 2: Drought Monitor Graphs**
-  Download tabular data from [United States Drought Monitor](https://droughtmonitor.unl.edu/)  by selecting region and exporting statistics as a csv file
- In script, correct paths to file (above) if necessary
- Change graph title to reflect selected analysis period
- Run script to generate graph; no analysis is performed 

**Figs 3 and 4: P/PET Trends**
- Register with aWhere to obtain API key, API "secret", and header.py file
- Create a file named secretcodes.py with variables API_KEY and API_SECRET set to the appropriate values
- In cell 6, specify date range for desired month (historical norms)
- In cell 8, specify date range for desired month (recent data)
- Run cells through 10 to generate graph with daily average (2010-2019) and recent (2020) P/PET values 
- Run cells though 11 to generate graph with daily average (2010-2019) and recent (2020) accumulated P/PET values

**Fig 5: aWhere Grid with 2020 Accumulated P/PET**
- Register with aWhere to obtain API key, API "secret", and header.py file 
- Create a file named secretcodes.py with variables API_KEY and API_SECRET set to the appropriate values
- Use GIS of choice to generate grid over area of interest with 9km x 9km square polygons
- Correct paths to gridded area of interest file (above) if necessary
- Modify cell 5 to reflect date range desired
- Run remaining cells to obtain graph of accumulated P/PET values for desired month

### Example usage
To run all scripts, the following datasets are required:
1. state, county, and area of interest vector shapefiles
2. Landsat 8 GeoTIFF (with at least 3 files corresponding to red, green, blue bands)
3. CSV from United States Drought Monitor
4. GeoJSON of grid with 9km x 9km cells over area of interest

Other appropriate data:
Geopandas will read a wide range of vector-based geospatial data via the read_file method; change paths in script to point to other file types (state, country, area of interest, gridded area of interest) 
