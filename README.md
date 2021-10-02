# Salary Prediction Portfolio
## Introduction

This project aims to train and deploy machine learning model that predict salary based on their job type, location, years of experience and education level. This model over looks over 1000000 inputs. This model provides useful salary estimates that can help people negotiate and maximize their salary based on their market value and job location. This model also gives information about the most common, high paying jobs na d in-demand career paths. This model enables us to determine the key features that drives the salary.
## Data
The data folder of this repository consists of three csv files
- 'train_features'
- 'train_salaries': This file contains the target variable 'salary'
- 'test_features'

## Jupiter Notebooks:

- Salary_Prediction_EDA: contains code for Data Wrangling, Exploratory Data Analysis(EDA) and Baseline creation
- SalaryPrediction_Modelling: contains the code for model training, hyper parameter tuning, Principal Component Analysis(PCA), Model Evaluation and Model Deployment.

## Other repository content
'modelpredicition.csv' contains the salaries predicted by the model from the test dataset.

## Data Wrangling 
1. Load all the train and test data files into pandas data frame.

2. Merge the files - train_features and train_salaries into a single dataframe called train_df

3. Clean the data
- Check for data duplicates
	- no data duplicates were found
- Check for missing values
	- no missing values were found in the dataset
- Check for outliers
	-  we used the IQR rule to find the outliers. We found some lower bound outlier and removed them from the training set. Upper bound outliers were detected but we did not remove them because they seem to be legitimate data.

## Exploratory Data Analysis
Exploring every features
1. CompanyID
	- The number of employess per company ranges from 15635 to 16114. We can conclude that this dataset contains data of all the large companies. This means that our predictive model might not be able to predict the salaries of mid size or small organizations.
	- All the companies seem to have similar average salary, and similar distribution across the dataset.
2. Job Type
	- All jobtypes have the same count
	- There are some Vice Presidents, CEO, CFO and Managers without 	degree. 	- Either this is the case of missing data or we can assume that we dont necesserily need a degree to have a C-suite role.
3. Degree
	- There are more anount of High School and Non degree holders in the dataset.
4. Major
	- There are 9 majors listed in the dataset
	- Majority of the people in the dataset do not have theie major listed
5. Industry
	- There are 7 types of industies in this dataset and all of them have the same count
6. Years Experience
	- Years of experience is evenly distributed in the dataset
7. Miles from metropolis


### Target variable - salary
	- The target variable "Salary" has a Normal Distribution
![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/target_variable.png?raw=true)
