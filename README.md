# Salary Prediction Portfolio
## Introduction
- This project aims to develop and deploy a salary prediction model that provides salary estimates which business' HR and talent functions can use to optimize their compensation strategy, acquire the best talent and improve the company retention rate in the competitive labor markets.

- This model also provides useful information that job seeker can use to maximize their salary as well as determine the most common, highest paying jobs and in demand career paths.

- This model will be trained on **1+ million training data set with 8 features**. 

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

	![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/jobtype.png?raw=true)
	- All jobtypes have the same count
	- There are some Vice Presidents, CEO, CFO and Managers without degree. 	
	- Either this is the case of missing data or we can assume that we dont necesserily need a degree to have a C-suite role.
3. Degree

	![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/degreetype.png?raw=true)
	- There are more anount of High School and Non degree holders in the dataset.
4. Major

	![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/majortypes.png?raw=true)
	- There are 9 majors listed in the dataset
	- Majority of the people in the dataset do not have theie major listed
5. Industry

	![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/industrytype.png?raw=true)
	- There are 7 types of industies in this dataset and all of them have the same count
6. Years Experience
	- Years of experience is evenly distributed in the dataset
7. Miles from metropolis


### Target variable - salary
	- The target variable "Salary" has a Normal Distribution
![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/targetvar_dist.png?raw=true)

### Correlartion with the Target Variable
**i. yearsExperience and salary**

	![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/yearsExperienceandsalary.png?raw=true)
	- We can see a positive correlation between Salary and years of experince.
	- Higher the years of job experience, higher the salary.
	
 **ii. milesFromMetropolis and salary**
 
 ![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/milesandsalary.png?raw=true)
	- We can see a negative correlation between salary and milesFromMetropolis.
	- So, the futher away you are from the metropolitian city, the lower your salary will be.
	
**iii. companyId and salary**

![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/comanyidandsalary.png?raw=true)
	- There is no correlation between salary and companiId.
	- We can see a flat cure which means all the companies have the same average salaries.

**iv. jobType and salary**

![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/jobtypeandsalary.png?raw=true)
	- We can see a positive correlation between salary and jobType.
	- The higher the job position, the higher the salary.
	
**v. degree and salary**

![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/degreeandsalary.png?raw=true)
	- More advanced degrees like Doctorate and Masters tend to correspond to higher salaries.
	- Surpringly, even non degree holders have a decent salary. by looking at this plot we can conclude that a degree is not always required to have a good salary.
	
**vi. major and salary**

![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/majorandsalary.png?raw=true)
	- People with Engineering, Business and Math majors have the highest salaries.
	- Surprisingly, even people with no major have a decent salary. This might possibly be the case of missing data.
	
**vii. industry and salary**

![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/industryandsalary.png?raw=true)
	- The lowest paying industries - Education and Services can have upper bound salary if the have 15+ years of experice.
	
#### Multivariate Analysis

![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/correlation_matrix.png?raw=true)
Based on the correlation heatmap above, we can note the following things. 
	- jobType is the most strongly correlated to salary, followed by degree, major, yearsExperience
	- milesFromMetropolis has a negative correlation with salary 
	
## Baseline
For our model performance baseline, a linear regression model using negative MeanSquaredError(MSE) scoring, has been selected. The average MSE score using a five-fold cross-validation on the training dataset is 400.02.

Our goal is to train and deploy a model boasting an MSE score of less than 360.

## Hypothesizing solutions
Given the information we have about our data.

**These are the models I propose to predict the salary are:**

- **Linear Regression**: From the EDA, we have seen that both the numerical and most of the categorical variable have a liner correlation with the target variable 'salary'. Based on those factors a liner modle would be suitable for this dataset.
- **Random Forest**: Random Forest would be a good model for this dataset because it would be able to handle the categorical data well. This model also reduces overfitting and helps to improve the accuracy. Random forest is also a flexible model for both classifiaction and regression problems.
- **Gradient-boost**: Gradient boosting has lots of flexibility. It can optimize on different loss functions and provides several hyper parameter tuning options that make the function fit very flexible.

**The step I am planning to take to improve the model accuracy and decrease the MSE are:**

	- Apply feature engineering like one-hot encoding for categorical variabes
	- Normalize the numerical to scale the data
	- Hypertune the parameters to enhance the accuracy
	
## Feature Engineering
	- Encode the categorical variables using one-hot encode feature
	- Normalizing the numerical features

## Model Training
We performed a 5 fold cross-validation with negative MSE scoring on each of the selected models.

**Results**

![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/mse.png?raw=true)

Clearly the GradientBoosting outperformed all the other models with the lowest neg-MSE.

![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/modle_mse.png?raw=true)

We achived the goal of reducing the MSE(Mean Squared Error) < 360.

The plot below visualizes actual salaries versus predicted on the training dataset.
![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/GradientBoot_Training_AVsF.png?raw=true)

### Top 10 Important Features of the Model (GradientBoosting)
![alt text](https://github.com/shreyashrestha07/SalaryPrediction/blob/main/images/Feature_importance.png?raw=true)
	
- We can see that the most important feature is the jobType

## Deployment
Finally we can deploy our model by making salary predictions on the test dataset. The predictions made have been saved in the file 'predictions.csv' which can be found in the repository. 

