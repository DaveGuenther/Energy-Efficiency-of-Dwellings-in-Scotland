# Energy-Efficiency-of-Dwellings-in-Scotland

This dashboard explores heating methods and fuel types used for detached domestic dwellings in Scotland.  It is built on data from Energy Performance Certificates (ECP), which are assessment reports issued upon transfer of a property or before it is rented.

Tableau Public Dashboard Link: https://public.tableau.com/views/EnergyEfficiencyofHomesinScotland/EnergyPerformanceofScotlandHomes?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link

## Cardinality:
Each row in the visual's underlying dataset represents metadata from the most recent Energy Performance Certificate (EPC) document/inspection of a single detached domestic dwelling.  The property's Unique Property Reference Number (UPRN) was used to capture the most recent assessment and avoid duplicate counting.

## Data Source:
Data for this dashboard was extracted primarily from Domestic Energy Performance Certificates at STATISTICS.GOV.SCOT and includes data through CY2022Q3.  Geospacial data came from GeoNames.org.

## Source Code:
See source code for full details on preprocessing activities.  The main datasets are not included in the code repository due to their size, but can be downloaded from the sources cited in the notebook to recreate the analysis.  If recreating the analysis, don't use .csv files from STATISTICS.GOV.SCOT beyond 2022Q3.csv

## Preprocessing Details:
Lat and Log coordinates were determined by joining the main dataset with a companion dataset from GeoNames.org that uses the outward postal code as a primary key.  There were 3881 rows where the outward postal code was not matched in the GeoNames.org dataset.  These rows were filtered out.

Main heating methods and fuel types both have a large number of dimensions.  Main heating methods and fuel types were both grouped by their frequency in the dataset to reduce the number of dimensions displayed while still retaining the closest frequency shape of the original categories.  Of note, mineral and wood (including wood pellet fuels) were combined into one category.

Imputations were made where possible in the original dataset.  This included imputing an "Unknown Date" for the date built where no information was available.  Additionally, looking through the data, there were several areas where Electricity was able to be imputed as the fuel type based on the identified heating method.
