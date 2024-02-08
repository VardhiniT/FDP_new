# Flight Delay Prediction - T Giri Vardhini

### Introduction About the Data :

**The dataset** The goal is to predict `delay` of flight with given details about it (Regression Analysis).

There are 8 independent variables :

* `Temperature at departure` : Temperature (°C) at the departure airport is one of the weather factors affecting the flight schedules. 
* `Temperature at arrival` : Temperature (°C) at the departure airport is one of the weather factors affecting the flight schedules. 
* `Wind at departure` : The magnitude of wind (mph) at the departure is also one of the factor affecting the flight schedules.
*`Wind at arrival` : The magnitude of wind (mph) at the arrival is also one of the factor affecting the flight schedules.
* `Precipitation` : The effect of precipitation is categorised as either 0 (no effect) or 1, depending on the type and magnitude of precipitation.
* `Delay in departure` : The delay of aircraft (min) in its previous journey which may effect its immediate take-off.
* `Aircraft maintainance` : Unexpected mechanical issues that require immediate attention may lead to delay in its next journey. 
* `Air route traffic` : Air route congestion may implement delays to manage traffic flow, such as holding patterns or ground stops.

Target variable:
* `Delay in arrival`: The delay in arrival (min) is predicted taking into account the above factors.

<!-- Dataset Source Link :
[https://www.kaggle.com/competitions/playground-series-s3e8/data?select=train.csv](https://www.kaggle.com/competitions/playground-series-s3e8/data?select=train.csv) -->

### It is observed that the variables in the dataset are all numerical in nature (the downloaded dataset is thoroughly pre-processed before it is released). 

<!-- # AWS Deployment Link :

 [http://gemstonepriceutkarshgaikwad-env.eba-7zp3wapg.ap-south-1.elasticbeanstalk.com/](http://gemstonepriceutkarshgaikwad-env.eba-7zp3wapg.ap-south-1.elasticbeanstalk.com/)

# Screenshot of UI

![HomepageUI](./Webpage_UI/Screenshot%202318.jpg) -->

## End to End MAchine Learning Project

1. Docker Build checked
2. Github Workflow
3. Iam User In AWS

## Docker Setup In EC2 commands to be Executed

#optinal

sudo apt-get update -y

sudo apt-get upgrade

#required

curl -fsSL https://get.docker.com -o get-docker.sh

sudo sh get-docker.sh

sudo usermod -aG docker ubuntu

newgrp docker

## Configure EC2 as self-hosted runner:

## Setup github secrets:

AWS_ACCESS_KEY_ID=

AWS_SECRET_ACCESS_KEY=

AWS_REGION = us-east-1

AWS_ECR_LOGIN_URI = demo>>  566373416292.dkr.ecr.ap-south-1.amazonaws.com

ECR_REPOSITORY_NAME = simple-app

# Approach for the project 

1. Data Ingestion : 
    * In Data Ingestion phase the data is first read as csv. 
    * Then the data is split into training and testing and saved as csv file.

2. Data Transformation : 
    * In this phase a ColumnTransformer Pipeline is created.
    * for Numeric Variables first SimpleImputer is applied with strategy median , then Standard Scaling is performed on numeric data.
    * for Categorical Variables SimpleImputer is applied with most frequent strategy, then ordinal encoding performed , after this data is scaled with Standard Scaler.
    * This preprocessor is saved as pickle file.

3. Model Training : 
    * In this phase base model is tested . The best model found.
    * After this hyperparameter tuning is performed model.
    * A final VotingRegressor is created which will combine prediction of xgboost and RF models.
    * This model is saved as pickle file.

4. Prediction Pipeline : 
    * This pipeline converts given data into dataframe and has various functions to load pickle files and predict the final results in python.

5. Flask App creation : 
    * Flask app is created with User Interface to predict the Flight Delay Prediction inside a Web Application.

<!-- # Exploratory Data Analysis Notebook -->

<!-- Link : [EDA Notebook](./notebook/1_EDA_Gemstone_price.ipynb) -->

<!-- # Model Training Approach Notebook

Link : [Model Training Notebook](./notebook/2_Model_Training_Gemstone.ipynb) -->

<!-- # Model Interpretation with LIME 

Link : [LIME Interpretation](./notebook/3_Explainability_with_LIME.ipynb) -->


