# What drives the price of a car?

## Overview
This used car dataset has been retrieved from Kaggle. The original dataset had over 3 million entries. 
For the sake of processing, only 426k entries were selected. 
The goal is determining what factors make a car more or less expensive. 

This is a Kaggle dataset : https://www.kaggle.com/austinreese/craigslist-carstrucks-data

I am following the CISP-DM Framework for this analysis. 

<p align="center">
  <img src=“images/“crisp.png>
</p>

### 1 - Business Understanding
**1.0 - Data problem definition** <br>
    The goal of this problem is to develop a predictive model that will correctly predict the prices of used cars based on various features
    such as Odometer readings, Size, make/model and so on. 
    We would need to employ various Regression models to identify patterns, and important features that contribute to the price determination
    based on the historic data and accurately predict any future car sale prices.
    In summary, the objective is to create a robust predictive model that accurately predicts the prices of used cars
    and identified the most significant factors contributing to their valuation.

### 2 - Data Understanding
    **2.1 Data Collection** <br>

    **2.2 Data Description** <br>
          The cursory overview of the data
	⁃	Total 426880 Samples and 18 Features
	⁃	Categorical data - region, model, manufacturer, condition, 
           cylinders, fuel, title_status, transmission, VIN, drive, size
           type, paint_color, state
	⁃	Numerical data - id, price, year, odometer

    **2.3 Data Exploration** <br>
	⁃	Check the describe function to identify the mean and standard deviation
	⁃	Identify missing values from the dataset
	⁃	Identify unique values for Categorical 
    **2.4 Data Quality Assessment* <br>	



### 3 - Data Preparation
    **3.1 Data Cleaning** <br>
    **3.2 Feature Engineering** <br>
    **3.3 Data Encoding** <br>

### 4 - Modeling
 **4.1 Random Forest Regression ** <br>
 **4.2 Ridge Regression* <br>
### 5 - Evaluation

### 6 - Deployment

