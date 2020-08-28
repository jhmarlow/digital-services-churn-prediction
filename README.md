# Digital Services User Churn Prediction with Apache Spark

## Overview
This repository contains the code used to build Machine Learning model to predict user churn in a digital music service. Apache Spark (PySpark) was implemented to handle the large dataset and deploy analytics and ML at scale. The project was then deployed was developed in IBM Watson distributed computing platform. The project followed the CRISP-DM principles.

![features](/readme_images/features.png)

## Quick Start
### Prerequisites
- Python 3.7.6
- PySpark Local 3.0.0
- PySpark IBM  2.3.4
- PySpark AWS 2.4.5
- Jupyter Notebooks
- Python packages see requirements.txt

### Project Structure
The project contains four notebooks:
1. **Sparkify_EDA**: initial look at the data provided pulling out some stats and seeing data available.
2. **Sparkify_DataWrangling**: cleaning any problems found from initial exploration
3. **Sparkify_FeatureEngineering**: used to create features to be used in ML model
4. **Sparkify_MachineLearning**: used to evaluate and optimise ML models
5. **Sparkify_deploy**: deployable notebook to AWS EMR foor Big Data Analytics and ML

## Tools:
IBM Watson - used to host development of code
AWS EMR - used to deploy code
Apache Spark - used for Big DataAnalytics

## Introduction
The digital music service industry is a highly competitive sector, with the likes of Spotify, Apple Music, Pandora, TIDAL and more, all competing in a market where it's difficult to get an edge. To make the digital subscription model work it is vital to retain a strong customer base. However, due to the nature of a digital music subscription model, customers changing services is inevitable, and this is where customer churn comes in. In this project an optimised machine learning algorithm was developed to predict user churn.

## Dataset
Available from Udacity DataSceince Nanodegree Public AWS S3 Bucket.

2 datasets:
1. mini_sparkify_event_data.json - small dataset, used for initial analysis and visualistion (123MB)
2. medium-sparkify-event-data.json - medium size dataset to run on IBM watson
3. sparkify_event_data.json - larger dataset used to train ML model on AWS EMR (12GB)

![eda1](/readme_images/user_subscriptions.png)

![eda2](/readme_images/event_subscriptions.png)


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

![features](/readme_images/sns_plot.png)

## Issues:
- IBM watson notebook timeout and fail to connect to kernel
- AWS EMR keyerror when using GBT model see stack similar stackoverflow question [here](https://stackoverflow.com/questions/58910023/keyerror-when-training-a-model-with-pyspark-ml-on-aws-emr-with-data-from-s3-buck_).

## References
Project completed as part of Udacity DataScience Nanodegree.
Data provided is from fictional Digital Music Service provider "Sparkify"





