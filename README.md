:sob: :rotating_light: :house: 

# ETL-project
In looking at open data sources on Kaggle, we found data sets for Chicago crime that interested us.  However, we wanted it to be relevant to our community, so we located similar data for our city at https://data.kcmo.org/. We used the crime data by zip code for each year from 2014-current.  The second source of data we originally planned to use was not available at the time we started the project however.  We were able to find Cenus data by zip code at http://zipatlas.com/.  We also agreed that with this amount of data, we needed to use SQLite in order to be more efficient and make sharing between our GitHubs easier.

The following sources for our datasets were used:

<http://zipatlas.com/us/mo/kansas-city/zip-code-comparison/population-density.htm>

2014: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2014/yu5f-iqbp>

2015: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2015/kbzx-7ehe>

2016: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2016/wbz8-pdv7>

2017: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2017/98is-shjt>

2018: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2018/dmjw-d28i>

2019: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2019/pxaa-ahcm>

2020: <https://data.kcmo.org/Crime/KCPD-Crime-Data-2020/vsgj-uufz>

# Transformation
In order to transform the public data and use it in our project, we did the following:

* Created a CSV from the Excel file off the ZipAtlas website (had we been willing to pay a subscrition fee or had a live website to use, there was an option to download the zipped CSV straight from the website, but neither of those were viable options for us at this time), then created a table with this CSV file in Jupyter Notebook

* Using Jupyter Notebook, merged the crime data into one table, stacking by year.  As this required multiple sources being merged at once, we had to locate what code would allow us to do this in the fewest steps possible.  Using the 

* Removed columns that contained data that was not relevant to the focus of this project (longitude, latitude, rank of population for the zip code as it was for national ranking and we were focused on our city alone)

*
