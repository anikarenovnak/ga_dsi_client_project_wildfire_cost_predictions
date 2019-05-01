# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Client Project: California Wildfire Damage Projection

## Problem Statement

Wildfires cause substantial damage each year to the state of California. The goal for this project is to predict the dollar amount of damage done to specific counties within the state of California due to wildfires.


---

## Table of Contents

1. Data Collection & Cleaning

2. EDA & Visualization

3. Problem Statement, Data Acquisition, and Discussion of Feature Engineering

4. Modeling, Hyperparameter Tuning, & Model Evaluation

5. Final Model Selection, Conclusion, & Recommendations


---

## Data Acquisition & Cleaning

#### The primary source of data came from [Cal Fire Red books](https://www.fire.ca.gov/fire_protection/fire_protection_fire_info_redbooks). 
They had PDFs containing detailed statistics concerning fires within several (but not all counties). At a high level, the statistics that came from here are the dollar damage, dollar damage by cause, acreage burned and the causes, fire sizes and vegetation burned. Each file was in a pdf format and there was an individual PDF file for each data categories above, for each year and for each region of the state (northern/southern). In summary, there were a total of 84 PDF data files that were combined together to create a dataset with the relevant statistics for all counties in Caliofornia for the years 2010-2016 inclusive. 

#### Secondary sources of data: 

1. Weather data
- [National Oceanic and Atmospheric Administration(NOAA)](https://www.ncdc.noaa.gov/cdo-web/search)
Historical weather data was gathered from the National Oceanic and Atmospheric Administration (NOAA). The data that was usable from here was average wind speed, precipitation, snowfall, average temperature, maximum temperature.

2. County details 
- [National Census Bureau/Wikipedia](https://en.wikipedia.org/wiki/List_of_counties_in_California)
- [Bureau of Economic Analyses/Department of Commerce](https://www.bea.gov/data/gdp/gdp-county)
County details include value per square foot, population and area size. Affluence data is also gathered, including GDP per capita, median house income, median family income. This was gathered from Wikipedia which in turn was gathered from the United States Census Bureau.  The number of campgrounds and forests were also gathered up since it is believed that a good amount of fires originate from campgrounds. This information was gathered from Yelp.

3. Number of Campsites/RV Parks per County
- [Yelp](https://www.yelp.com/search?find_desc=RV%20Parks&find_loc=Yolo%20County%2C%20CA&cflt=rvparks%2Ccampgrounds)

4. Median house value per sq ft
- [Zillow](https://www.zillow.com/research/data/)

5. Percentages of wilderness vs developed land in a given county 
- [CalLands](https://callands.ucanr.edu/data.html)


---

## Executive Summary

California has a notorious reputation for rising wildfire incidents in recent years. This rise is coincided with a huge increase in spending and damage to structures. Settlements in at risk areas continue to grow, putting structures and lives more at risk as they creep closer to wilderness areas. This creates a need to predict damages to structures and infrastructure as wildfires grow larger and more frequent each year. This allows California as a whole to rethink carefully on which areas it wants to develop and how to protect those investments from destruction.

This need for a prediction creates a need for a model to project damages in different parts of the states. Right now, a granularity on a county level is sufficient to make some base estimations in where the state can expect high amounts of destruction. The dataset that was created for the model included wildfire statistics from 2010 to 2016 from Cal Fire. This included dollar damage, causes, number of fires, size of fires and more. However it was found that this was not sufficient, and more data was required. Campgrounds and RV parks were added from Yelp, weather data was added from the National Oceanic and Atmospheric Administration,  population data from the National Census Bureau and developed/wilderness ratio per county was also gathered. Through this data we were able to generate a model score of 0.49. While not very accurate, it gives us a baseline to work with to improve in the future as we start bringing in more data. 

---

## Conclusions and Recommendations

While the average test score of meta-models are higher than the average test scores of both the base case and the grid searched models, we choose not to select our best model from the meta-models because the meta-models on average suffer from error due to very high variance, therefore they will not hold good generalizability to unseen data. 

The best set of models to choose from is the set of grid searched models. These models have a relatively high average testing score as compared to the base case models, and significantly reduced variance overall. 

The best model candidate is therefore the one among the grid searched models which best satisfies the evaluation criterian mentioned above. 

**The best model** is the grid-searched lasso regularized model with the following scores: 
- cv score:0.43
- train score: 0.50
- test score: 0.49


#### Our recommendations to FEMA are as follows: 
    
- If possible, create guidlines or create a standardized process for states/counties and local governments to collect data on wildfires on a more granular level to bridge the massive gap in the data that makes predictions of damage cost forecasting so dfficult. 

- If possible mandate and enforce these data reporting/collection guidlines to ensure that states/counties and local governments are actually fulfilling these requirements. 

- If possible, such data should be entered into a standardized/centralized data base for easy and quick access as a large amount of time and a massive amount of human effort may be neceesary to collect and combined the data. 

- Wildfire and more generally natural disaster data collection should be enforced by law because it can help save lives of individuals and families, and it can help reduce an overall economic impact to the nation's whole economy if assistance, mitigation of disasters, management of disaster supression where possible and post-disaster resource allocation can be done more efficiently and quickly thanks to in-advance projections of damages before they happen. 


---

## Software Requirements

- Pandas
- Numpy
- Matplotlib
- Seaborn
- Scikit-learn
- Pactools
- StatsModels


---

## Team Members

Egan Bailey, Sean Gu, Ani Karenovna K. Douglas Nguyen, Amanda Jo Russell