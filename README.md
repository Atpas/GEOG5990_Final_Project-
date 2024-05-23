# GEOG5995_Final_Project-
Yuting Liu 201775283

Do neighbourhoods with high numbers of unhealthy people in Leeds have fewer resources to live in?
==

The background of the project: 
-
Health is now a global issue, and countries are finding ways to actively address it. Data studies have found significant differences in health outcomes across communities. A variety of factors influence health disparities, including socioeconomic status, access to health care, educational opportunities and living conditions. According to Chrisman et al. (2015), some communities have lower intensity of physical activity due to fewer activity facilities; while some communities have lower average incomes, which may lead to residents not being able to afford healthcare (Augusto et al., 2017). These may represent a relationship between health and quality of life.

The aim of this project is to explore the relationship between health status and the ability to gain resources for living (LSOA) in different neighbourhoods within Leeds. By using 2011 Census health data and 2015 Index of Multiple Deprivation (IMD) data to define the correlation between poorer health neighbourhoods and deprivation indices, and to make clusters of LSOA areas within the range, to determine what features the groups of clusters have, to provide informational support for decision-making and resource allocation to solve the needs of the most vulnerable populations in the city of Leeds.

Data in the GitHub repository:
-
Health and provision of unpaid care data from the 2011 Census. The data covers the LSOA (Lower Layer Super Output Areas) wards in the city of Leeds and is taken from the 2011 Census conducted on 27 March 2011 in the UK. The data resource is at Nomis under the address https://www.nomisweb.co.uk/default.asp. The dataset contains the percentage of people with each health condition included in the LSOA in Leeds, which includes a general health classification, a restriction of daily activities classification and a need for care classification, for the purposes of this project only the general health classification is required.

The second dataset is the 2015 Index of Multiple Deprivation (IMD) for England.
Data contains an index of deprivation (where a high index represents deprivation) and rankings, with areas ranked from the most deprived (rank 1) to the least deprived. The dataset has a wide range of categories including income, employment, education, health, crime, barriers to housing and services, and living environment. The data is sourced from the CDRC and can be downloaded at https://data.cdrc.ac.uk/dataset/index-multiple-deprivation-imd.

The third data is Geojson data from Leeds LSOA. This includes the UK National Grid eastward (BNG_E) and northward coordinates (BNG_N), longitude (LONG) and latitude (LAT). GlobalID, which is a unique identifier assigned to the database. Geometry which describes the geometry of the geographic object, in this dataset is a polygon, representing the area boundary.

Although the Index of Deprivation data is from 2015 and is some time different from the 2011 Census data. it is still reasonable to use both datasets for analysis. Firstly, because of the slow change in socio-economic factors, some socio-economic factors may be slow to change over a relatively long period of time, such as levels of deprivation, unemployment, and levels of education. Moreover, deprivation indexes are usually more recent than census data because deprivation indexes will rely on data from government reports and other sources which may not be available until a later point in time, so the timeliness of the data will be affected. Therefore, it is still useful to compare census data from 2011 with deprivation index data from 2015.

Visualisation options and code aims:
-
After importing the required packages first, the data processing operations are started. For health data, what needs to be done is to keep only the useful data columns such as general health status and LSOA codes and names. The variable to be studied in this project is 'unhealthy group', so the two columns 'Bad health' and 'Very bad health' need to be added together to get a new column 'bad health %'. After which the null values are checked and deleted. For IMD data, the data needs to be filtered ('Local Authority District name'] == 'Leeds') by keeping only the Leeds data. And rename the column names (columns= {'LSOA code': 'lsoacd') for the ease with which the two datasets can be joined afterwards. 
After that the two datasets need to be matched using the ‘. merge' method and the public variable 'lsoacd'. And the merged dataset can be used to generate non-spatial visualisation charts.

For the selection of non-spatial visualisation charts, scatter plots were selected and paired with regression lines and confidence intervals. Scatter plots are used to show the relationship between two variables, enabling the observation of correlations and trends between two quantities. Whereas the regression line shows more of a trend between the variables, the confidence interval shows the range of uncertainty in the prediction. As for the choice of colours, I chose a combination of blue, orange, and green. According to Lee et al. (2020), these colours belong to complementary colour pairs, a combination that is easy to distinguish for colour blind people.

After that import the geojson file, align it with the health data, remove mismatched rows, and check for duplicate rows. Then merge it with the previous merged dataset continue to merge it into the new dataset and then keep only the useful columns. In terms of selecting the data, besides health, I chose deprivation indices for barriers to employment, education, and housing services, all variables that are clearly related to quality of life. The next step was to decide how many clusters needed to be created, this can be done by using the Elbow method and tuning the number of iterations to decide the number of clusters (Syakur et al., 2018). 
