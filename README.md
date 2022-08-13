# Student-Success

## Overview

This repository is meant to demonstrate my contributions to the group project "NYC-Student-Success-Predictions," which can be found in its unedited form here: https://github.com/divish16/NYC-Student-Success-Predictions

The goal of the overall project was **to identify and visualize correlations between student demographic data and student success metrics in NYC high schools.**

My role in this project was fourfold:
- Extracting, cleaning, and transforming the datasets for use in visualizations and machine learning (using Python/Pandas in Jupyter Notebook)
- Creating all visualizations in Tableau
- Creating the first machine learning model as a template (a multiple linear regression model using RandomForestRegressor)
- Writing content and providing some minor styling for the group Heroku website, available here: https://nyc-success-predictions.herokuapp.com/


## Data Cleaning and Transformation

### Datasets

### Cleaning

### Transformation



## Visualizations 

My focus was to visualize relationships between poverty metrics and student success metrics like graduation rates. The visualizations suggest that there may be correlations between these two groups, but correlation is not causation. 

Our group's overall conclusion was that student success is likely affected by a number of factors not in our dataset, and demographic information cannot be considered predictive of student success. However, the correlations are striking and may describe trends that could be clarified with future research. 

Screenshots of sample visualizations can be found below. **Please visit our Heroku site ([https://nyc-success-predictions.herokuapp.com/](https://nyc-success-predictions.herokuapp.com/visualizations.html)) to view additional visualizations and interact with the data.**


### Sample Visualizations



![SampleVisual3](https://user-images.githubusercontent.com/100863488/184498666-a1aac5d9-2045-4e3b-ba0a-17ae9642f596.png)

In the visualization above, each dot represents a school. The size of the dot represents the percentage of graduates receiving an advanced honors diploma. The color of the dot represents the percentage of students receiving free or reduced-price lunch, which can be considered as a general metric of the average socioeconomic status at a school. The darker the dot, the more students are receiving free or reduced-price lunch. Generally, in the visualization above, the larger dots with higher advanced diplomas are lighter in color, indicating fewer students receiving free or reduced-price lunch.


![SampleVisual2](https://user-images.githubusercontent.com/100863488/184498697-4bada34e-f41e-4e47-a3eb-abd7cabfe85a.png)

In the visualization above, each dot represents a school. The y-axis represents the percentage of cohorts at that school who drop out before graduation. The x-axis represents the Economic Need Index of that school. The schools with the higher dropout rates tend to be among the schools with the highest Economic Need Index.
