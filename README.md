# Outages Project
<p style="text-align: center; font-size: 1.1em;">
  By Hannah Huang and Julia Dial
</p>

## Introduction
Power outages are disruptive events that affect millions of people across the United States every year. Beyond just inconvenience, long electrical outages can impact emergency services, hospitals, economic activity, and public safety. It is important to understand power outages so that individuals can navigate around them and anticipate which ares may need better power outage preparedness. 

Coincidentally, Hannah and Julia are both from the same hometown in Virginia, where we experience regular power outages due to weather events as a result of what we believe to be living in a coastal state. We wanted to explore and understand where outages occur and why some areas experience longer disruptions than others. 

Our question of focus is **do coastal states experience longer power outages than inland states? Additionally, can outage duration be accurately predicted using information about outage cause, climate conditions, and regional characteristics?** This question is important because coastal states often experience hurricanes, flooding, and servere storms while inland states are more prominent to drought and extreme heat stress. We want to identify if there could be any possible correlation between these events.

This outages dataset contains information about 1534 different power outages (rows) from 2000-2016 defined by 57 different features (columns). The data contain information on outage duration, location, people affected, characterics of area of outage occurence, etc. The features we believe are specifically essential to our project were POPPCT_URBAN, OUTAGE.DURATION, CAUSE.CATEGORY,  NERC.REGION, CLIMATE.REGION, ANOMALY.LEVEL, PCT_WATER_TOT, and MONTH. We also feature engineered a "REGION_TYPE" column for future use. Descriptions of the following columns are as follows: 

**1) POPPCT_URBAN:** Percentage of the total population of the U.S. state represented by the urban population (in %)

**2) OUTAGE.DURATION:** Total duration of each individual outage event (in minutes)

**3) CAUSE.CATEGORY:** Categories of all the events causing the major power outages ('severe weather', 'intentional attack','system operability disruption', 'equipment failure','public appeal', 'fuel supply emergency', 'islanding').

**4) NERC.REGION:** The North American Electric Reliability Corporation (NERC) regions involved in the outage event ('MRO', 'SERC', 'RFC', 'ECAR', 'TRE', 'WECC', 'SPP', 'FRCC', 'NPCC','FRCC, SERC', 'HI', 'PR', 'HECO', 'ASCC').

**5) CLIMATE.REGION:** U.S. Climate regions as specified by National Centers for Environmental Information ('East North Central', 'Central', 'South', 'Southeast', 'Northwest','Southwest', 'Northeast', 'West North Central', 'West',)

**6) ANOMALY.LEVEL:** This represents the oceanic El Niño/La Niña (ONI) index referring to the cold and warm episodes by season. It is estimated as a 3-month running mean of ERSST.v4 SST anomalies in the Niño 3.4 region (5°N to 5°S, 120–170°W)

**7) MONTH:** Indicates the month when the outage event occurred (as integers)

**8) PCT_WATER_TOT:** Percentage of state area covered by water (in %). This will later be used to classify inland vs coastal states.

**9) REGION_TYPE:** A derived feature whether states with above-median water coverage are labeled as coastal states and inland if below the median threshold

## Data Cleaning and Exploratory Data Analysis
In order to clean our data, we intially we converted the excel file to a csv format and removed unnecessary headers, and rows before converting it to csv. After this, we used the following steps:

1) Removed the "variables" column
  
2) Converted the OUTAGE.DURATION, PCT_WATER_TOT, ANOMALY.LEVEL, POPPCT_URBAN, and MONTH columns from strings to float values in order to avoid type inconsistencies.

3) Dropped null rows from the data set if any of these columns had nan values.

4) Removed rows with outage durations less than or equal to 0 through filtering, as these values are physically impossible.

5) Created a column, REGION_TYPE to classify whether the outage occured in a coastal or inland region based on the threshold of the median PCT_WATER_TOT.

6) Got rid of columns that we didn't need by filtering them out.

This left us with a dataset of 1398 different outages (rows) and 9 different features (columns).

**Our cleaned dataset below:**

|   OUTAGE.DURATION |   PCT_WATER_TOT | REGION_TYPE   | CAUSE.CATEGORY     |   POPPCT_URBAN | NERC.REGION   | CLIMATE.REGION     |   ANOMALY.LEVEL |   MONTH |
|------------------:|----------------:|:--------------|:-------------------|---------------:|:--------------|:-------------------|----------------:|--------:|
|              3060 |         8.40733 | coastal       | severe weather     |          73.27 | MRO           | East North Central |            -0.3 |       7 |
|                 1 |         8.40733 | coastal       | intentional attack |          73.27 | MRO           | East North Central |            -0.1 |       5 |
|              3000 |         8.40733 | coastal       | severe weather     |          73.27 | MRO           | East North Central |            -1.5 |      10 |
|              2550 |         8.40733 | coastal       | severe weather     |          73.27 | MRO           | East North Central |            -0.1 |       6 |
|              1740 |         8.40733 | coastal       | severe weather     |          73.27 | MRO           | East North Central |             1.2 |       7 |
|              1860 |         8.40733 | coastal       | severe weather     |          73.27 | MRO           | East North Central |            -1.4 |      11 |
|              2970 |         8.40733 | coastal       | severe weather     |          73.27 | MRO           | East North Central |            -0.9 |       7 |
|              3960 |         8.40733 | coastal       | severe weather     |          73.27 | MRO           | East North Central |             0.2 |       6 |
|               155 |         8.40733 | coastal       | intentional attack |          73.27 | MRO           | East North Central |             0.6 |       3 |
|              3621 |         8.40733 | coastal       | severe weather     |          73.27 | MRO           | East North Central |            -0.2 |       6 |



**Bar Chart for Univariate Data Analysis of the distribution of the CAUSE.CATEGORY column**

<iframe
  src="assets/outage_causes.html"
  width="595"
  height="397"
  frameborder="0"
></iframe>

This bar chart depicts that the causes of severe weather and intentional attack caused significantly more outages from 2000-2016 in comparison to the other outage causes. The causes associated with number of outages in ascending order is fuel supply emergency, islanding, equipment failure, public appeal, system operability distruption, intentional attack, then severe weather.

**Histogram for Univariate Data Analysis of distribution of Outage Duration**
<iframe
  src="assets/outage_duration_hist.html"
  width="595"
  height="397"
  frameborder="0"
></iframe>

This histogram depicts that the distribution of outage duration in minutes from 0 to the max duration which corresponds to the bin 1950-1999 minutes. This histogram is right skewed with the highest density of duration length clustered between 0 to 500 minutes. The bin that contains the most frequent length of duration is the first bin with width 0-49 minutes, which means that the outages in this dataset were relatively short.

**Bar Graph for Bivariate Data Analysis of distribution of mean outage duration given the cause category**

<iframe 
    src="assets/mean_outage_duration.html" 
    width="595" 
    height="397" 
    frameborder="0">
</iframe>

This bar chart depicts the average outer times given the inland and coastal states. This bar chart takes information from both the OUTAGE.DURATION column and the REGION_type column. It initially separates the outages by the different region types, and then works to calculate the average outage duration given the region types.

**Bar Graph for Bivariate Data Analysis of distribution of mean outage duration given the month**
<iframe 
    src="assets/mean_outage_by_month.html" 
    width="595" 
    height="397" 
    frameborder="0">
</iframe>

The bar chart above displays the relationship between the columns OUTAGE.DURATION and MONTH, where the x axis is month number and the y axis is the mean duration for a specific month. A pattern illustrated in this graph is that spring into summer months (April through August) have lower mean outage durations in comparison to fall and winter months (September to February). 


**Full Grouping Dataframe Below**

| REGION_TYPE   | CAUSE.CATEGORY                |      mean |   median |   count |
|:--------------|:------------------------------|----------:|---------:|--------:|
| coastal       | equipment failure             |  2713.74  |    269   |      35 |
| coastal       | fuel supply emergency         | 14347.2   |   3960   |      30 |
| coastal       | intentional attack            |   522.901 |    113   |     171 |
| coastal       | islanding                     |   215.697 |    122   |      33 |
| coastal       | public appeal                 |  1826.94  |    557   |      35 |
| coastal       | severe weather                |  4024.76  |   2775   |     452 |
| coastal       | system operability disruption |   576.101 |    199   |      79 |
| inland        | equipment failure             |   260.474 |    149   |      19 |
| inland        | fuel supply emergency         | 10247.1   |   7500.5 |       8 |
| inland        | intentional attack            |   520.907 |     87   |     161 |
| inland        | islanding                     |   155.091 |     56   |      11 |
| inland        | public appeal                 |  1099.41  |    398   |      34 |
| inland        | severe weather                |  3704.13  |   1865   |     289 |
| inland        | system operability disruption |  1076.56  |    245   |      41 |

For this dataframe, we grouped by REGION_TYPE, and then continued by grouping together different cause categories in order to allow us to understand how different types of outages behave across different geographic environments. Outage duration is influenced not only by the outage location, but also the cause of the outage. Later in our project, we intend to explore whether or not there is a different between outage duration in coastal vs. inland states. We wanted to look into the different features by grouping together nuanced variables and then calculate statistical values that would not appear if we analyzed the values separately.

We also chose to calculate 3 different statistical values given our groupings:

**1) Mean outage duration:** captures the overall average severity in length of power outages

**2) Median outage duration:** describes the typical outage duration while successfully dealing with outliers

**3) Count:** shows how many outages fall into each pair of region × category, helping us understand reliability of the comparison.

In our grouped data, we can see that there were a significantly higher amount of weather attacks on coastal regions than inland states. This is most likely due to the fact that they experience more rainfall, hurricanes, etc. We can also see that fuel supply emergencies resulted in the longest average outage durations in both coastal and inland states. However, looking at the median, we can see that the mean is extremely skewed most likely due to outliers of extremely servere emergencies. There is a lot of information that we can use this dataframe to determine, and these are just some of the examples! We also created a pivot table to futher and better display our means.


**Pivot Table Below**

| REGION_TYPE   |   equipment failure |   fuel supply emergency |   intentional attack |   islanding |   public appeal |   severe weather |   system operability disruption |
|:--------------|--------------------:|------------------------:|---------------------:|------------:|----------------:|-----------------:|--------------------------------:|
| coastal       |            2713.74  |                 14347.2 |              522.901 |     215.697 |         1826.94 |          4024.76 |                         576.101 |
| inland        |             260.474 |                 10247.1 |              520.907 |     155.091 |         1099.41 |          3704.13 |                        1076.56  |

This is our pivot table! It includes information about the average power outage duration given a specific cause and region type. We can also see this information in our grouped dataframe above, as this is just another format if displaying our information. The rows are separated by region type, and each column gives the cause category. 

## Assessment of Missingness
NMAR missingness relates to missing values in the data where the missingness is related to the value itself. There is no correlation between the missing values in the column with any other column in the dataset. We believe the CUSTOMERS.AFFECTED column - which has the number of customers affected by an outage - contains null values that are Not Missing At Random because the values in this column being missing could be due to the value itself. For example, a very small number of customers affected may go unreported. Therfore, since the probability of the missingness could be related to the value itself, the missing data in this column could be classified as NMAR. Additional data we might want to obtain to explain this missingness, and make it MAR, is the radius of how far the outage impacted.

## Hypothesis Testing
The two hypotheses we tested were:

**Null:** There is no difference in outage duration between coastal and inland states.

**Alternative:** The mean duration of coastal outages is longer than the mean duration of inland state outages.

The test statistic that we used to conduct our permuation test was the difference in means between the groups: coastal and inland. The result of our permutation test, was a p-value of 0.0164, so we would reject the null hypothesis in favor of the alternative, using an alpha=0.05 significance level. Meaning, we conclude our result is statistically significant and therefore there is evidence against the null and in favor of coastal states experiencing longer outages on average than inland states. 

The null and alternative hypotheses are helpful towards answering our intial question from above, do coastal states experience longer power outages than inland states, because it tests for if there exists a relationship between location of a state on the duration of the outage experienced. The alpha of 0.05 was choosen because we wanted the conclusion of our permutation test to indicate statisitically significant results to reduce the chance of false positives (falsely rejecting the null). Difference in means was a good choice towards answering our question because we could simulate and compare the mean outage duration for the two groups (coastal and inland) to be able to make a conclusion about if one group experiences longer outages not by random chance.

## Framing a Prediction Problem
Our prediction problem was a regression problem predicting the response variable **OUTAGE.DURATION**. We chose this response variable because we thought we could build a model that would be able to closely predict duration of outages because we thought it would be related to other features of the outages dataset. We also believe that it is one of the most important features in our dataset. 

The metric we are using to evaluate the quality of our model is Root Mean Squared Error (RMSE). We choose this metric because it:

**(a)** quantifies the closeness of our predictions to the actual values in the OUTAGE.DURATION column

**(b)** measures how far (on average) our predicted durations are from the true durations

**(c)** penalizes large errors more heavily, which is important because some outages last extremely long

**(d)** is standard for regression tasks involving continuous outcomes

At time of prediction, we can confidently assume we would know

**1) CAUSE.CATEGORY** — the general cause
  
**2) NERC.REGION** - the regional electrical reliability authority 

**3) CLIMATE.REGION** — the regional climate classification

**4) ANOMALY.LEVEL** — a numerical measure of temperature anomaly at the time of the outage
   
  
## Baseline Model
Our baseline model predicts outage duration trained using the quantitative feature: ANOMALY.LEVEL, as well as the three categorical features: CAUSE.CATEGORY, NERC.REGION, and CLIMATE.REGION. We encoded the categorical columns using OneHotEncoder. Additionally, we standarized the numerical column using StandardScaler. 

We calculated our model to have an RMSE of 5934.684873212793. Due to this high error, we believe our current model is not "good," in the sense that the error is high meaning our model is predicting values far from the actual data in the OUTAGE.DURATION column, and can be improved to lower the root mean squared error. 

## Final Model
A feature we added with the goal of improving our baseline model was MONTH, which will be helpful in our prediction task assuming that months are associated with different weather patterns.

Features that we engineered 

## Fairness Analysis
