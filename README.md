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


