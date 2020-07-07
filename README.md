# drought-tracker
Jupyter-based python project for quantifying agricultural drought extent and agronomic values.

### Project description
This project was created to answer the question

> How can we accurately describe the spatial extent of a droughted region to on a local scale?

Josephine County has been experiencing a severe drought since April 2020 according to the U.S. Drought Monitor. However, this source describes approximate areas affected, and the methods used to derive these areas are opaque. In fact, the U.S. Drought Monitor website itself does not recommend its use to infer specifics about local conditions.

On the other hand, the code in this repo allows the user to provide a custom time period and a custom drought definition to describe droughts; it is an alternative to the "all-encompasing" nature of U.S. Drought Tracker findings. The user may explore drought extent and severity according to variables that are most important to them. For example, agronomists and farmers can use this information to inform crop placement and rotation based on historical drought extent. Foresters and land management agents can infer forest and land health. Climate data exploration is available to local decisionmakers and stakeholders.



The metric used to determine drought is the ratio of precipitation over potential evapotranspiration, P/PET. A value of close to 1 indicates that most of the water that has left a system has returned to recharge the groundwater in that system. Threshold values of P/PET are as follows. At and below these values, evidence of water stress becomes apparent:

| P/PET | What is affected| 
| ------|---------------|
|  0.4  | Forests and rangeland | 
| 0.6 - 0.8 | Many crops | 
| 0.5 | This study | 

### Organization
>drought_tracker/
> --> project_nb: contains script and required files
>    --> drought_tracker.ipynb: Jupyter notebook of main script
>    --> drought_tracker.html
>    --> header.py: Script containing methods to use aWhere's API. Obtained from aWhere
>    --> josephine_4326.geojson: sample Area of Interest, Josephine County


### Workflow

#### Tools/packages
1. [aWhere API (header.py) and account](https://www.awhere.com/)
2. numpy
3. matplotlib
4. geopandas (includes shapely)
5. requests

### How to run (project_nb/drought_tracker.ipynb)
This repo contains the files necessary to determine droughted extent and P/PET values for Josephine County, OR. The best way to obtain the desired area of interest is to download [TIGER/line shapefiles](https://www.census.gov/cgi-bin/geo/shapefiles/index.php) and place them in the "data" directory.

The user must obtain a unique API key and secret by registering through aWhere. This info is contained in a file called "secret_codes.py" which must be present in the project_nb directory. Once these requirements are met, thdrought_tracker will run and produce outputs for sample data. Comments in code allow user to customize and indicate where user's input is required. Otherwise code will return drought extent and proportional P/PET values for area of interest.

### Example usage
An agronomist wants to determine if the crops in her area of interest are still suited for that region. She knows that the P/PET of this crop is 0.8, meaning it requires wet growing conditions, and the approximate growing window. She obtains a GeoJSON of her area of interest and runs the script. She sees that the area with a P/PET of lower than 0.8 has grown since 2017 and now consistently covers the cropland in the area of interest. Using this finding, she begins to prepare a recommendation to alter crop type and growing variables for the next growing season. 
