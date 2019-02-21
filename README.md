# ETL Project Report

### Extract
The goal is to create a database that would allow analysis of NYC graffiti data and NYC demographic data. The original data sources are a CSV file and a JSON file. The CSV file comprises demographic data per NYC zip code, which was downloaded from [Kaggle](https://www.kaggle.com/new-york-city/ny-demographic-statistics-by-zip-code). The JSON file containing graffiti data per NYC zip code was extracted from [Data.gov](https://catalog.data.gov/dataset/dsny-graffiti-information-549b7). Work was accomplished using Python, Pandas, iJSON and SQLite.

### Transform
After importing the CSV file, transform into a Pandas dataframe. Rename the column on which dataframes will be merged to a uniform name for easier merging. 

Since the JSON file stores column names in a separate location from their corresponding data, the first step is to extract the column names. Upon locating the column names path, use the path and the iJSON package to extract the column names into a list. From this list, select desired the names filter out the rest. 

Extract data from the JSON file by running 'for loops' to iterate through the data, filtering by desired column names, which takes only the data of interest and stores it in a list of lists called "data", whereby each interior list represents one row. The values of the JSON file need to be converted from objects into floats for merging. Convert "data" into a Pandas dataframe, which allows for transformation of a list of lists. Perform an inner merge on the two dataframes on their shared column "zip_code" into one combined dataframe. 

### Load
Export the dataframe to an SQLite Database. This database includes information on gender, ethnicity, citizenship, public assistance in combination with graffiti incidences, dates, status and resolutions.

Additionally, exporting the dataframe into a CSV file could prove useful if the data needs to be re-imported in the future for further analysis.
