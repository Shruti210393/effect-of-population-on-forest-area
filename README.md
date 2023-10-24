## Effect-of-Population-on-forest-area

## Aim:- Analyze how the population explosion has affected the forest area in India.

## Description:- 
To analyze the effect of population explosion on Forest areas, I need data that can be trusted, also which have forest areas and population recorded at different time frames.

## Architecture:-

<img src="/Imags/Architechture of effect of Population on forest area Data Engineering Project.JPG" width="50%">

Data Source:- Found the World Bank Indicators page contains all relevant data.
Link to access the indicators - https://data.worldbank.org/indicator
3 files were finalized based on Forest area (in sq. km), Male population, and Female population.
I have the option to download a single file that contains a record of the total population, however, I still found using male and female populations could bring more learning curves in this project such as -
A more dynamic pipeline and data flow.
BI analyst can compare male and female population as well.

Azure Synapse:- Data is Extracted using a data pipeline that ingests the data directly from the website using an HTTP connector provided by Microsoft Azure.
Fully automatic Data pipeline using Lookup activity to fetch the relative URL and sink filename and pass it to for each iterator.
I created a robust and fully automatic pipeline, one JSON document is saved in a storage account which contains a web URL to access the files and sink file name.
Lookup activity fetched the web URL and sink filename and provide the data to For Each iterator which then pass the parameters to copy activity one by one.
The data is then stored in a data lake and ready to be used in further transformations.

Azure Data Lake Gen2 (for data storage): Connected Azure Synapse to an Azure Data Lake Gen2 for storage.

Azure Synapse:- Data transformations has been done by using different functions as below
1. Select data from 2010 to 2020 year.
2. Filter the data for India.
3. Unpivot the data.
4. Join operation to create 1 dataset.
5. Sink to target location.

Visualization:- For visualization,we can compare male and female population and analyse how the population explosion effected on Forest areas.
