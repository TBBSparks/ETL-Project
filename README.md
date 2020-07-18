:sob: :rotating_light: :house: 

# ETL-Project

For this project, a group of us joined together to work on ETL concepts (**E**xtract; **T**ransform; **L**oad) using PostGreSQL (an open source object-relational database system) and SQLite (a C-language library that implements a small, fast, self-contained, high-reliability, full-featured, SQL database engine). Interesting fact: SQLite is the most used database engine in the world.  It was helpful to use in conjunction with our project as we expected our database to accumilate a large volume of data as we for use to launch us into a more complex and visually interesting collaboration. 

# Project Conceptualization
In looking at open data sources on Kaggle, we found data sets for Chicago crime that interested us.  However, we wanted it to be relevant to our community, so we located similar data for our city at https://data.kcmo.org/. We used the crime data by zip code for each year from 2014-current.  The second source of data we originally planned to use was not available at the time we started the project however.  We were able to find Cenus data by zip code at http://zipatlas.com/.  We also agreed that with this amount of data, we needed to use SQLite in order to be more efficient and make sharing between our GitHubs easier.

# Extract

The following sources were used to extract the data we wanted to work with:

<http://zipatlas.com/us/mo/kansas-city/zip-code-comparison/population-density.htm>

2014: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2014/yu5f-iqbp>

2015: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2015/kbzx-7ehe>

2016: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2016/wbz8-pdv7>

2017: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2017/98is-shjt>

2018: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2018/dmjw-d28i>

2019: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2019/pxaa-ahcm>

2020: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2020/vsgj-uufz>

# Transform
In order to transform the public data and use it in our project, we did the following:
______________________________________________________________________________________________________
To transform this data into a usable form, Pandas, a popular software library written for the Python programming language, was utilized. Pandas proved to be very effective here due to its ability to easily load data from a file into a pandas dataframe, where data can be manipulated into a form the user finds relevant to their analysis. First, the property sale CSV file was read into a pandas dataframe. The NYC property sales data only contained a borough ID and was missing the borough name. Therefore, a borough id dataframe was created and merged with a borough name dataframe in order to replace the id numbers with the corresponding names. Next, the tree census JSON file in its raw form is a series of nested dictionaries, and therefore a quick look through the raw file was required. The file was broken down into two sections: “meta” and “data.” The data could be easily loaded into the pandas dataframe, however column titles proved to be less straight-forward. An empty list was created, followed by a for loop that would cycle through the meta data and grab all the column titles and populate the list with them. This yielded the dataframe with the correct corresponding columns titles.
Not all the columns are relevant at this time. Therefore the next step in the cleaning was to drop any columns that will not be used later. After dropping irrelevant columns, the dataset we refer to as “property sales,” contained the following columns: id (primary key), borough id, borough, neighborhood, address, and sale price. In the dataset we refer to as “tree census,” the columns that are present include tree id (primary key), tree health, zip code, borough, and address. It was recognized that the two datasets related to each other via information such as boroughs and address. As a result, the loading stage would greatly benefit from a relational database program, i.e. PostgreSQL. In order for the data to be placed in SQL tables (in the hopes of performing a join later), the columns needed to be renamed to match the column names of tables that will eventually be made using PostgreSQL. Additionally, as a precaution, any null values in our dataframes were dropped.


* Created a CSV from the Excel file off the ZipAtlas website (had we been willing to pay a subscrition fee or had a live website to use, there was an option to download the zipped CSV straight from the website, but neither of those were viable options for us at this time), then created a table with this CSV file in Jupyter Notebook

* Using Jupyter Notebook, merged the crime data into one table, stacking by year.  As this required multiple sources being merged at once, we had to locate what code would allow us to do this in the fewest steps possible.  Using the 

* Removed columns that contained data that was not relevant to the focus of this project (longitude, latitude, rank of population for the zip code as it was for national ranking and we were focused on our city alone)

*

# Load
After we were satisfied with the format of our dataframes, they were loaded into tables in Postgres (pgAdmin4) by forming a connection to the jupyter notebook through the creation of an engine (ORM). This involved creating tables in PostgreSQL that we can load our data into using Pandas. Each table is assigned a primary key (typically id) for relational purposes. We created tables with the number and names of columns present in the dataframes we previously created.
_______________________________________________________________________
# Conclusion
The goal(s) of the project were completed successfully. The objective was not to perform an analysis on the data itself, but rather to prepare said data in such a way that an analysis would not be limited by any inconsistencies or formatting errors based on how the data is stored. With these datasets having gone through the ETL process, they are potentially ready for an analysis. We specifically chose datasets relevant to our city instead of the data readily available on Kaggle as we do plan to use it in a future collaboration together!  The most challenging part of this process was finding data that was going to be viable for this project as well as the future project that would require a significant amount of data so that visualizations and correlations could be used.  
