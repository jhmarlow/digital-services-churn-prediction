# churn-prediction-with-apache-spark

## Overview

This repository contains the code required to deploy a Gradient Boosting (GBT) Machine Learning model to predict user churn in a digital music service. The project structure was created by Quantam black's, Kedro. Apache Spark was implemented to handle the large dataset and deploy analytics and ML at scale. The project was then deployed to AWS EMR service to leverage the infrastructure. The project followed the CRISP-DM principles.


Model Overview:
- Percentage predicted correct (%): 99.9
- Churned users predicted (%): 99.5
- f1 score from MulticlassClassificationEvaluator: [0: 0.750557583960012, 1: 0.7155496453152247]

## Quick Start

The project contains four notebooks:
1. **Sparkify_EDA**: initial look at the data provided pulling out some stats and seeing data available.
2. **Sparkify_DataWrangling**: cleaning any problems found from initial exploration
3. **Sparkify_FeatureEngineering**: used to create features to be used in ML model
4. **Sparkify_MachineLearning**: used to evaluate and optimise ML models
5. **Sparkify_deploy**: deployable notebook to AWS EMR foor Big Data Analytics and ML

## Tools:
IBM Watson - used to host development of code
AWS EMR - used to deploy code
Kedro - The project structure was generated using `Kedro 0.16.2` (Quantam Black)
Apache Spark - used for Big DataAnalytics

## Dataset

From Exploratory Data Analysis (EDA):
- *location*: location of user, seems to append each new state (location, state)
- *gender*: user gender (M/F/None)
- *page*: what page the user is on during event (pages)
- *level*: subscription level check uniqueness (free or paid)
- *auth*: authenication (logged in/out)
- *length*: time spent on page, max 50 mins on NextSong (if song paused??)
- *registration*: unknown (registration unixtime)
- *ts*: timestamp of event in ms (event unixtime)
- *userId*: unique (userId val)
- *sessionId*: unique sessionId per user?
- *itemInSession*: lcounter for the number of items in a single session (item listened to in session)
- *firstName*: users first name (not important, remove)
- *lastName*: users lastname
- *artist*: song artist
- *song*: songname
- *userAgent*: device/browser (not important for us, remove)
- *method*: API PUT/GET http request (not important for us, remove)
- *status*: http status

## Machine Learning
Logistic Regression, RandomForestClassifier and GBT models were evaluated. Then cross validation was used to tune the hyperparameters of the GBT model to achieve the best performance. Features where developed to replicate user behaviour.


**Features**:
- Gender
- Location
- Avg time spent in a session
- Avg items listened to in session
- Positive user interactions
- Negative user interactions
- Service Error events


## Todo:
- Deploy to Kedro pipeline

## References
Project completed as part of Udacity DataScience Nanodegree. 
Data provided is from fictional Digital Music Service provider "Sparkify"





