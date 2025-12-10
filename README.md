# Outages Project

## Step 1: Introduction
Power outages are disruptive events that affect millions of people across 
the United States every year. Beyond just inconvenience, long electrical 
outages can impact emergency services, hospitals, economic activity, and 
public safety. It is important to understand power outages so that individuals
can navigate around them. Coincidentally, Hannah and Julia are both from the same hometown
in Virginia, where we experience regular power outages as a result of weather
events as a result of what we believe to be living in a coastal state. We wanted
to explore and understand where outages occur and why some areas experience longer
disruptions than others. Our question of focus is: 

**“Do coastal states experience longer power outages than inland states? Additionally,
can outage duration be accurately predicted using information about outage cause, 
climate conditions, and regional characteristics?”**

This outages dataset contains information about 1534 different power outages (rows) from 2000-2016 defined
by 57 different features (columns). The data contain information on outage duration, location, 
people affected, characterics of area of outage occurence, etc. Specifically, the 
features essential to our model were POPCT_URBAN, OUTAGE_DURATION, CAUSE.CATEGORY, 
NERC.REGION, CLIMATE.REGION, ANOMALY.LEVEL, and MONTH. Descriptions of the following columns are as follows: 

**POPCT_URBAN:** Percentage of the total population of the U.S. state represented by the urban population (in %)

**OUTAGE_DURATION:** Duration of outage events (in minutes)

**CAUSE.CATEGORY:** Categories of all the events causing the major power outages (severe weather, intentional attack, public appeal, fuel supply emergency, islanding, equipment failure).

**NERC.REGION:** The North American Electric Reliability Corporation (NERC) regions involved in the outage event

**CLIMATE.REGION:** U.S. Climate regions as specified by National Centers for Environmental Information (nine climatically consistent regions in continental U.S.A.)

**ANOMALY.LEVEL:** This represents the oceanic El Niño/La Niña (ONI) index referring to the cold and warm episodes by season. It is estimated as a 3-month running mean of ERSST.v4 SST anomalies in the Niño 3.4 region (5°N to 5°S, 120–170°W)

**MONTH:** 	Indicates the month when the outage event occurred (as integers)


We will explain why these features are nessecary in later steps.

## Step 2: Data Cleaning and Exploratory Data Analysis

## Step 3: Assessment of Missingness

## Step 4: Hypothesis Testing

## Step 5: Framing a Prediction Problem

## Step 6: Baseline Model

## Step 7: Final Model

## Step 8: Fairness Analysis
