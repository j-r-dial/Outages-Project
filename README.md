# Outages Project

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
NERC.REGION, CLIMATE.REGION, ANOMALY.LEVEL, and MONTH. Descriptions of the following columns are as follows: 

**POPPCT_URBAN:** Percentage of the total population of the U.S. state represented by the urban population (in %)

**OUTAGE.DURATION:** Duration of outage events (in minutes)

**CAUSE.CATEGORY:** Categories of all the events causing the major power outages ('severe weather', 'intentional attack','system operability disruption', 'equipment failure','public appeal', 'fuel supply emergency', 'islanding').

**NERC.REGION:** The North American Electric Reliability Corporation (NERC) regions involved in the outage event ('MRO', 'SERC', 'RFC', 'ECAR', 'TRE', 'WECC', 'SPP', 'FRCC', 'NPCC','FRCC, SERC', 'HI', 'PR', 'HECO', 'ASCC').

**CLIMATE.REGION:** U.S. Climate regions as specified by National Centers for Environmental Information ('East North Central', 'Central', 'South', 'Southeast', 'Northwest','Southwest', 'Northeast', 'West North Central', 'West',)

**ANOMALY.LEVEL:** This represents the oceanic El Niño/La Niña (ONI) index referring to the cold and warm episodes by season. It is estimated as a 3-month running mean of ERSST.v4 SST anomalies in the Niño 3.4 region (5°N to 5°S, 120–170°W)

**MONTH:** 	Indicates the month when the outage event occurred (as integers)

We will explain why these features are nessecary in later steps.

## Data Cleaning and Exploratory Data Analysis
Intially, we converted the excel file to a csv format. We removed unnecessary headers and rows before converting it to csv. After that, to clean the data we converted the OUTAGE.DURATION column from strings to float values in order to avoid type inconsistencies. Then we dropped null rows from the data set if either the OUTAGE.DURATION or PCT_WATER_TOT columns had nan values, this was done because this information is necessary towards our classification of states as costal versus inland and for determining the strength of our model. Also, we removed rows with outage durations less than or equal to 0 through filtering, as these values are physically impossible. Next, we converted PCT_WATER_TOT to numeric to avoid formating issues and percentage signs. We created a column, REGION_TYPE to classify whether the outage occured in a coastal or inland region based on the threshold of the median PCT_WATER_TOT. Finally, we got rid of columns that we didn't need by filtering them out. This left us with a dataset of 1398 different outages (rows) and 11 different features (columns).

**Our cleaned dataset below:**


|   OUTAGE.DURATION |   PCT_WATER_TOT | REGION_TYPE   | CAUSE.CATEGORY     |   POPPCT_URBAN |   OUTAGE.DURATION | CAUSE.CATEGORY     | NERC.REGION   | CLIMATE.REGION     |   ANOMALY.LEVEL |   MONTH |
|------------------:|----------------:|:--------------|:-------------------|---------------:|------------------:|:-------------------|:--------------|:-------------------|----------------:|--------:|
|              3060 |         8.40733 | coastal       | severe weather     |          73.27 |              3060 | severe weather     | MRO           | East North Central |            -0.3 |       7 |
|                 1 |         8.40733 | coastal       | intentional attack |          73.27 |                 1 | intentional attack | MRO           | East North Central |            -0.1 |       5 |
|              3000 |         8.40733 | coastal       | severe weather     |          73.27 |              3000 | severe weather     | MRO           | East North Central |            -1.5 |      10 |
|              2550 |         8.40733 | coastal       | severe weather     |          73.27 |              2550 | severe weather     | MRO           | East North Central |            -0.1 |       6 |
|              1740 |         8.40733 | coastal       | severe weather     |          73.27 |              1740 | severe weather     | MRO           | East North Central |             1.2 |       7 |
|              1860 |         8.40733 | coastal       | severe weather     |          73.27 |              1860 | severe weather     | MRO           | East North Central |            -1.4 |      11 |
|              2970 |         8.40733 | coastal       | severe weather     |          73.27 |              2970 | severe weather     | MRO           | East North Central |            -0.9 |       7 |
|              3960 |         8.40733 | coastal       | severe weather     |          73.27 |              3960 | severe weather     | MRO           | East North Central |             0.2 |       6 |
|               155 |         8.40733 | coastal       | intentional attack |          73.27 |               155 | intentional attack | MRO           | East North Central |             0.6 |       3 |
|              3621 |         8.40733 | coastal       | severe weather     |          73.27 |              3621 | severe weather     | MRO           | East North Central |            -0.2 |       6 |

## Assessment of Missingness

## Hypothesis Testing

## Framing a Prediction Problem

## Baseline Model

## Final Model

## Fairness Analysis
