# Visualizing NYC Student Success

## Overview

This repository is meant to demonstrate my contributions to the project "NYC-Student-Success-Predictions," which can be found in its unedited form here: https://github.com/divish16/NYC-Student-Success-Predictions

The goal of the overall project was **to identify and visualize correlations between student demographic data and student success metrics in NYC high schools.**

My role in this project was fourfold:
- Sole responsibility for extracting, cleaning, and transforming the datasets for use in visualizations and machine learning (using Python/Pandas in Jupyter Notebook)
- Creating all visualizations in Tableau
- Creating the first machine learning model as a template (a multiple linear regression model using RandomForestRegressor)
- Writing content and providing some minor styling for the group Heroku website, available here: https://nyc-success-predictions.herokuapp.com/

In this repository I will focus on the extract and transform process as well as the visualizations in Tableau, since this pipeline is self-contained. 

![whitespace-large](https://user-images.githubusercontent.com/100863488/185760356-bcea3ba4-a0a5-4dbe-9631-bd473c0f0a51.png)



## Data Cleaning and Transformation

### Datasets

Four datasets were used and joined to 
create the data used for visualizations 
and machine learning:

1. <a href="https://data.cityofnewyork.us/Education/2006-2012-School-Demographics-and-Accountability-S/ihfw-zy9j">2006 - 2012 School Demographics and Accountability Snapshot</a> (Demographic information for NYC cohorts and schools)

2. <a href="https://data.cityofnewyork.us/Education/2016-2017-Graduation-Outcomes-School/nb39-jx2v">2016-2017 Graduation Outcomes School</a> (Success metrics like graduation rates and diploma types)

3. <a href="https://data.cityofnewyork.us/Education/2017-18-2021-22-Demographic-Snapshot/c7ru-d68s/data">2017-18 - 2021-22 Demographic Snapshot</a> (Demographic information, notably % of students living in poverty and Economic Need Index)

4. <a href="https://www.kaggle.com/datasets/nycopendata/high-schools?select=scores.csv">Average SAT Scores for NYC Public Schools (2014-2015)</a> (Success metrics as well as school latitude and longitude, for visualizations)

These four datasets are included in the Resources folder.

![whitespace-small](https://user-images.githubusercontent.com/100863488/185760361-d448a978-3a56-4b6e-995c-b8a285d262f5.png)

### Process

The four datasets contain information regarding cohorts over multiple years and include different groups of students. In order to compare the information school by school, I took the following steps:

1. Reduced the datasets to include only schools that had students in 9th, 10th, 11th, and/or 12th grades

2. Cleaned the data, including: dropping unnecessary columns, converting non-numeric datatypes to numeric datatypes, and using regular expressions where needed to remove unnecessary non-numeric characters

3. For each dataset, using groupby in Pandas based on the DBN (an identifying code unique to each school) to average all the schools' rows of information on a given feature, thus creating new "averaged" dataframes with one row per school

4. Joining these averaged dataframes together on the DBN column to create a larger, merged dataframe that contains all needed demographic and success metric information
![whitespace-small](https://user-images.githubusercontent.com/100863488/185760365-8a1bb577-c56e-4271-aa71-eec2c2c1d9d8.png)


### Cleaning Challenges

At several points in the cleaning process, simple measures were not enough to achieve the desired results. Examples follow below:

#### Removing elementary and middle schools from the datasets

Two of the datasets contained elementary and middle schools in the dataset in addition to the high schools needed for our project. These datasets contain many columns of students, representing pre-kindergarten levels through 12th grade, with numbers in each column at each row indicating the number of students in that grade per school. 

This process involved the following:
* Dropping the pre-K through 8th grade columns
* Converting all blank values in the 9th-12th columns to NaNs
* Converting all NaNs in the 9th-12th columns to zero to use for filtering
* Filtering the dataset to include only rows that included a positive number in at least one of the 9th-12th grade columns

An example:
![image](https://user-images.githubusercontent.com/100863488/185804111-b95b4115-24fb-493b-8627-aa8a1283fb2e.png)


#### Numeric columns stored as non-numeric datatypes

Since I would be averaging the numeric columns to create the summary datasets, it was necessary for numeric columns to be stored as numeric datatypes. Several columns were stored as string datatypes because they contained certain entries with the word "Above" and characters like commas or percentage signs. I used regular expressions and lambda functions to recreate these columns with numeric entries before casting the columns to numeric datatypes. Examples follow below:

![image](https://user-images.githubusercontent.com/100863488/185803950-2f9502f0-93f7-4f38-ad21-978da6770b55.png)


![image](https://user-images.githubusercontent.com/100863488/185803963-19e5f864-1b14-440b-a901-30867f12f6aa.png)

![whitespace-small](https://user-images.githubusercontent.com/100863488/185760375-4008996a-3446-484b-95e4-b8ae6cf2422f.png)

### Transformation to New Dataframes

After the data cleaning process was finished, the datasets were averaged by school in order to create dataframes with one row per school. The summary dataframes could then be joined together on the School ID ("DBN") column to combine the datasets with information regarding demographic information with information regarding success metrics.

![image](https://user-images.githubusercontent.com/100863488/185804265-9c08ea18-8d93-4a77-8063-d8044a60bed4.png)
![whitespace-large](https://user-images.githubusercontent.com/100863488/185760379-58efde8a-ee1f-41a6-8d57-f84415b4d725.png)

## Visualizations 

My focus was to visualize relationships between poverty metrics and student success metrics like graduation rates. The visualizations suggest that there may be correlations between these two groups, but correlation is not causation. 

Our group's overall conclusion was that student success is likely affected by a number of factors not in our dataset, and demographic information cannot be considered predictive of student success. However, the correlations are striking and may describe trends that could be clarified with future research. 

Screenshots of sample visualizations can be found below. **Please visit our Heroku site ([https://nyc-success-predictions.herokuapp.com/](https://nyc-success-predictions.herokuapp.com/visualizations.html)) to view additional visualizations and interact with the data.**


### Sample Visualizations



![SampleVisual3](https://user-images.githubusercontent.com/100863488/184498666-a1aac5d9-2045-4e3b-ba0a-17ae9642f596.png)

In the visualization above, each dot represents a school. The size of the dot represents the percentage of graduates receiving an advanced honors diploma. The color of the dot represents the percentage of students receiving free or reduced-price lunch, which can be considered as a general metric of the average socioeconomic status at a school. The darker the dot, the more students are receiving free or reduced-price lunch. Generally, in the visualization above, the larger dots with higher advanced diplomas are lighter in color, indicating fewer students receiving free or reduced-price lunch.


![SampleVisual2](https://user-images.githubusercontent.com/100863488/184498697-4bada34e-f41e-4e47-a3eb-abd7cabfe85a.png)

In the visualization above, each dot represents a school. The y-axis represents the percentage of students in each cohort at that school who drop out before graduation. The x-axis represents the Economic Need Index of that school. The schools with the higher dropout rates tend to be among the schools with a high Economic Need Index.
