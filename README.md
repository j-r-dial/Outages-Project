

# Outages Project
<p style="text-align: center; font-size: 1.1em;">
  By Hannah Huang and Julia Dial
</p>

## Introduction
Power outages are disruptive events that affect millions of people across 
the United States every year. Beyond just inconvenience, long electrical 
outages can impact emergency services, hospitals, economic activity, and 
public safety. It is important to understand power outages so that individuals
can navigate around them. Coincidentally, Hannah and Julia are both from the same hometown
in Virginia, where we experience regular power outages as a result of weather
events as a result of what we believe to be living in a coastal state. We wanted
to explore and understand where outages occur and why some areas experience longer
disruptions than others. Our question of focus is: 

**Do coastal states experience longer power outages than inland states? Additionally,
can outage duration be accurately predicted using information about outage cause, 
climate conditions, and regional characteristics?**

This outages dataset contains information about 1534 different power outages (rows) from 2000-2016 defined
by 57 different features (columns). The data contain information on outage duration, location, 
people affected, characterics of area of outage occurence, etc. Specifically, the 
features essential to our model were POPPCT_URBAN, OUTAGE.DURATION, CAUSE.CATEGORY, 
NERC.REGION, CLIMATE.REGION, ANOMALY.LEVEL, PCT_WATER_TOT, and MONTH. Descriptions of the following columns are as follows: 

**POPPCT_URBAN:** Percentage of the total population of the U.S. state represented by the urban population (in %)

**OUTAGE.DURATION:** Duration of outage events (in minutes)

**CAUSE.CATEGORY:** Categories of all the events causing the major power outages ('severe weather', 'intentional attack','system operability disruption', 'equipment failure','public appeal', 'fuel supply emergency', 'islanding').

**NERC.REGION:** The North American Electric Reliability Corporation (NERC) regions involved in the outage event ('MRO', 'SERC', 'RFC', 'ECAR', 'TRE', 'WECC', 'SPP', 'FRCC', 'NPCC','FRCC, SERC', 'HI', 'PR', 'HECO', 'ASCC').

**CLIMATE.REGION:** U.S. Climate regions as specified by National Centers for Environmental Information ('East North Central', 'Central', 'South', 'Southeast', 'Northwest','Southwest', 'Northeast', 'West North Central', 'West',)

**ANOMALY.LEVEL:** This represents the oceanic El Niño/La Niña (ONI) index referring to the cold and warm episodes by season. It is estimated as a 3-month running mean of ERSST.v4 SST anomalies in the Niño 3.4 region (5°N to 5°S, 120–170°W)

**MONTH:** 	Indicates the month when the outage event occurred (as integers)

**PCT_WATER_TOT:** Percentage of water area in the U.S. state as compared to the overall water area in the continental U.S. (in %)

## Data Cleaning and Exploratory Data Analysis
In order to clean our data, we intially we converted the excel file to a csv format and removed unnecessary headers and rows before converting it to csv. After this, we used the following steps:

1) Converted the OUTAGE.DURATION, PCT_WATER_TOT, ANOMALY.LEVEL, POPPCT_URBAN, and MONTH columns from strings to float values in order to avoid type inconsistencies. 

2) Dropped null rows from the data set if any of these columns had nan values.

3) Removed rows with outage durations less than or equal to 0 through filtering, as these values are physically impossible. 

4) Created a column, REGION_TYPE to classify whether the outage occured in a coastal or inland region based on the threshold of the median PCT_WATER_TOT.

5) Got rid of columns that we didn't need by filtering them out.

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



**Plot for Univariate Data Analysis of the distribution of the CAUSE.CATEGORY column**

<iframe
  src="assets/outage_causes.html"
  width="590"
  height="395"
  frameborder="0"
></iframe>

This bar chart depicts the that the causes of severe weather and intentional attack caused significantly more outages from 2000-2016 in comparison to the other outage causes. The causes associated with number of outages in ascending order is fuel supply emergency, islanding, equipment failure, public appeal, system operability distruption, intentional attack, then severe weather.
## Assessment of Missingness
NMAR missingness relates to missing values in the data where the missingness is related to the value itself. We believe the CUSTOMERS.AFFECTED column, that has the number of customers affected by an outage, contains null values that are Not Missing At Random because the values in this column being missing could be due to the value itself: for example, a very small number of customers affected may go unreported. Therfore, since the probability of the missingness could be related to the value itself, the missing data in this column could be classified as NMAR. Additional data we might want to obtain to explain this missingness, and make it MAR, is the radius of how far the outage impacted.

## Hypothesis Testing


## Framing a Prediction Problem

## Baseline Model

## Final Model

## Fairness Analysis
