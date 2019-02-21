# Project2-ETL

ETL Project Report

Extract:
I wanted to create a database that would allow analysis of NYC graffiti data and NYC demographic data. The original data sources are a CSV file and a JSON file. The CSV file comprises demographic data per NYC zip code, which was downloaded from Kaggle. The JSON file containing graffiti data per NYC zip code was extracted from Data.gov. Work was accomplished using Python and Pandas.

Transform: 
I imported the csv file and transformed it into a Pandas dataframe. I elected to rename the "zip_code" column to a uniform name that will match the column name of the second dataframe (from JSON) for easier merging. 

The JSON file stored column names in a separate place from their corresponding data, so I needed first to extract the column names. I located the column names path and extracted the column names into a list using the ijson package. From this list, I chose the names I wished to work with and filtered out the rest. 

I then extracted data from the JSON file by running 'for loops' to iterate through the data filtering by desired column names, which takes only the data of interest and stores it in a list of lists called "data", whereby each interior list represents one row. I then converted "data" into a Pandas dataframe, which allows for transformation of a list of lists. The values of the JSON file needed to be converted from objects into floats. I then performed an inner merge on the two dataframes on their shared column "zip_code" into one combined dataframe. 

Load:
I exported the dataframe to an SQLite Database. I also exported the dataframe into a CSV file. CSV is a useful format if the data needs to be re-imported in the future for further analysis.