:sob: :rotating_light: :house: 

# ETL-Project

For this project, a group of us joined together to work on ETL concepts (**E**xtract; **T**ransform; **L**oad) using PostGreSQL (an open source object-relational database system) and SQLite (a C-language library that implements a small, fast, self-contained, high-reliability, full-featured, SQL database engine). Interesting fact: SQLite is the most used database engine in the world.  It was helpful to use in conjunction with our project as we expected our database to accumulate a large volume of data as we for use to launch us into a more complex and visually interesting collaboration. 

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
In order to transform the public data into workable data for our project, we created a CSV from the Excel file off the ZipAtlas website (had we been willing to pay a subscrition fee or had a live website to use, there was an option to download the zipped CSV straight from the website, but neither of those were viable options for us at this time), then created a table with this CSV file in Jupyter Notebook.  Next, we imported using Pandas.  We did the same with each year of crime data that we took from the Data.KCMO website.  For this, we wanted to merge the files into one dataframe, stacking by zipcodes as it was our intent to hinge the two sets of data for comparisons at a later date using zip codes. This was achieved using Jupyter Notebook. As this required multiple sources being merged at once, we had to locate what code would allow us to do this in the fewest steps possible, while maintaining the integrity of our data.

We continued to clean our tables by removing data that we did not feel would be able to add value to our data or would not be useable for our intended analysis, such as NAN values for zip codes or incomplete/mistyped zip codes. We also ensured all columns had clear titles for the data being reported in them.  This was particularly important for the ZipAtlas CSV as it was lacking headers entirely, so it would have been difficult to determine what data each column was reflecting.  At this time, we also decided we could drop the national ranking number column from that table as we were not going to be reporting national crime, rendering it unnecessary data.  We also dropped longitude and latitude since it was a redundancy and we already had the zip codes to determine the area of the crime. This yielded the dataframe with the correct corresponding columns titles and fully usable data.  

At this point we were ready to connect our databases.  

# Load
After we were satisfied with the format of our dataframes, they were loaded into SQLite.  Due to the volume of data, SQLite was ideal for it's convienience and speed with larger datasets over PGAdmin.  As this was a new process for us, we ran a query to ensure it was functioning as we intended it to. The data was successfully connected, so we felt confident our data is ready to be used for our future analysis.

# Conclusion
The goal(s) of the project were completed successfully. The objective was not to perform an analysis on the data itself, but rather to prepare said data in such a way that an analysis would not be limited by any inconsistencies or formatting errors based on how the data is stored. With these datasets having gone through the ETL process, they are potentially ready for an analysis. We specifically chose datasets relevant to our city instead of the data readily available on Kaggle as we do plan to use it in a future collaboration together!  The most challenging part of this process was finding data that was going to be viable for this project as well as the future project that would require a significant amount of data so that visualizations and correlations could be used.  

We did try to include screenshots of the databases we created to show our progress, however, when pushing the data, it exceeded the Github file limit (ours was 196, limit is 100, so it was not possible to get screenshots to share in this process write up).

