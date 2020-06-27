# churn-prediction-with-apache-spark

## Overview

This repository contains the code required to deploy a Gradient Boosting (GBT) Machine Learning model to predict user churn in a digital music service. The project structure was created by Quantam black's, Kedro. Apache Spark was implemented to handle the large dataset and deploy analytics and ML at scale. The project was then deployed to AWS EMR service to leverage the infrastructure.

Model Overview:
Percentage predicted correct (%): 99.9
Churned users predicted (%): 99.5

## Quick Start
The project contains four notebooks:
1. Sparkify_EDA: initial look at the data provided pulling out some stats and seeing data available.
2. Sparkify_DataWrangling: cleaning any problems found from initial exploration
3. Sparkify_FeatureEngineering: used to create features to be used in ML model
4. Sparkify_MachineLearning: used to evaluate and optimise ML models
5. Sparkify_deploy: deployable notebook to AWS EMR foor Big Data Analytics and ML

## Tools:
IBM Watson - used to host development of code
AWS EMR - used to deploy code
Kedro - The project structure was generated using `Kedro 0.16.2` (Quantam Black)
Apache Spark - used for Big DataAnalytics

## Dataset

## Machine Learning
Logistic Regression, RandomForestClassifier and GBT models were evaluated. Then cross validation was used to tune the hyperparameters of the GBT model to achieve the best performance. Features where developed to replicate user behaviour.
Features:
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





