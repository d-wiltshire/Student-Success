# Student-Success

## Overview

This repository is meant to demonstrate my contributions to the group project "NYC-Student-Success-Predictions," which can be found in its unedited form here: https://github.com/divish16/NYC-Student-Success-Predictions

The goal of the overall project was **to identify and visualize correlations between student demographic data and student success metrics in NYC high schools.**

My role in this project was fourfold:
- Sole responsibility for extracting, cleaning, and transforming the datasets for use in visualizations and machine learning (using Python/Pandas in Jupyter Notebook)
- Creating all visualizations in Tableau
- Creating the first machine learning model as a template (a multiple linear regression model using RandomForestRegressor)
- Writing content and providing some minor styling for the group Heroku website, available here: https://nyc-success-predictions.herokuapp.com/


## Data Cleaning and Transformation

### Datasets

Four datasets were used and joined to 
create the data used for visualizations 
and machine learning:

1. 2006 - 2012 School Demographics and Accountability Snapshot (Demographic information for NYC cohorts and schools)

2. 2016-2017 Graduation Outcomes School (Success metrics like graduation rates and diploma types)

3. 2017-18 - 2021-22 Demographic Snapshot (Demographic information, notably % of students living in poverty and Economic Need Index)

4. Average SAT Scores for NYC Public Schools (2014-2015) (Success metrics as well as school latitude and longitude, for visualizations)

These four datasets are included in the Resources folder.

The four datasets above contained information regarding cohorts over multiple years and included different age groups of students. Our goal was to correlate demographic information and high school success metrics. In order to compare the information school by school, I took the following steps:

1. Reduced the datasets to include only schools that had students in 9th, 10th, 11th, and/or 12th grades

2. Cleaned the data, including: dropping unnecessary columns, converting non-numeric datatypes to numeric datatypes, and using regular expressions where needed to remove unnecessary non-numeric characters

3. For each dataset, using groupby in Pandas based on the DBN (an identifying code unique to each school) to average all the schools' rows of information on a given feature, thus creating new "averaged" dataframes with one row per school

4. Joining these averaged dataframes together on the DBN column to create a larger, merged dataframe that contains all needed demographic and success metric information


### Cleaning Challenges




### Transformation



## Visualizations 

My focus was to visualize relationships between poverty metrics and student success metrics like graduation rates. The visualizations suggest that there may be correlations between these two groups, but correlation is not causation. 

Our group's overall conclusion was that student success is likely affected by a number of factors not in our dataset, and demographic information cannot be considered predictive of student success. However, the correlations are striking and may describe trends that could be clarified with future research. 

Screenshots of sample visualizations can be found below. **Please visit our Heroku site ([https://nyc-success-predictions.herokuapp.com/](https://nyc-success-predictions.herokuapp.com/visualizations.html)) to view additional visualizations and interact with the data.**


### Sample Visualizations



![SampleVisual3](https://user-images.githubusercontent.com/100863488/184498666-a1aac5d9-2045-4e3b-ba0a-17ae9642f596.png)

In the visualization above, each dot represents a school. The size of the dot represents the percentage of graduates receiving an advanced honors diploma. The color of the dot represents the percentage of students receiving free or reduced-price lunch, which can be considered as a general metric of the average socioeconomic status at a school. The darker the dot, the more students are receiving free or reduced-price lunch. Generally, in the visualization above, the larger dots with higher advanced diplomas are lighter in color, indicating fewer students receiving free or reduced-price lunch.


![SampleVisual2](https://user-images.githubusercontent.com/100863488/184498697-4bada34e-f41e-4e47-a3eb-abd7cabfe85a.png)

In the visualization above, each dot represents a school. The y-axis represents the percentage of students in each cohort at that school who drop out before graduation. The x-axis represents the Economic Need Index of that school. The schools with the higher dropout rates tend to be among the schools with a high Economic Need Index.
