# Digital Services User Churn Prediction with Apache Spark

[Medium Article](https://medium.com/@jacobmarlow/using-apache-spark-to-predict-user-churn-in-the-digital-music-service-industry-2efe974547c5?source=friends_link&sk=dd2e14cafe268b5e9a81d655e365b34f)

## Overview
This repository contains the code used to build a machine learning model to predict user churn in a digital music service. Apache Spark (PySpark) was implemented to handle the feature engineering on a large dataset and deploy ML at scale. The project was developed locally, in IBM Watson and on a AWS EMR cluster. The project followed the CRISP-DM principles.

## Quick Start
### Prerequisites
- Python 3.7.6
- PySpark Local 3.0.0
- PySpark IBM  2.3.4
- PySpark AWS 2.4.5
- Jupyter Notebooks
- For Python packages see requirements.txt

### Project Structure
The project contains 3 directories:
1. **deployments**: contains notebooks used for deployment (local, IBM, AWS)
2. **development**: code used to develop deployment notebooks
3. **visualisations**: code used to create data visualisations

## Tools:
IBM Watson - used to host development of code
AWS EMR - used to deploy code
Apache Spark - used for big data analytics

## Introduction
The digital music service industry is a highly competitive sector, with the likes of Spotify, Apple Music, Pandora, TIDAL and more, all competing in a market where it's difficult to get an edge. To make the digital subscription model work it is vital to retain a strong customer base. However, due to the nature of a digital music subscription model, customers changing services is inevitable, and this is where customer churn comes in. In this project an optimised machine learning algorithm was developed to predict user churn.

## Dataset
Available from Udacity DataSceince Nanodegree Public AWS S3 Bucket.

2 datasets:
1. mini_sparkify_event_data.json - small dataset, used for initial analysis and visualistion (123MB)
2. medium-sparkify-event-data.json - medium size dataset to run on IBM watson
3. sparkify_event_data.json - larger dataset used to train ML model on AWS EMR (12GB)

![user subscription](/readme_images/user_subscription.png)

![event subscription](/readme_images/event_subscriptions.png)


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


## Results 

- Logistic regression: 55.6%
- RFC: 55.6%
- GBT: 60.5%

AUC was chosen as the most appropriate metric for this binary classification problem, because of the two key metrics of True Positive Rate (TPR) and False Positive Rate (FPR), which AUC allows us to quantify.
After reviewing the models it can be seen, that for our metric, the Gradient Boosting model is the best performing, with an AUC score of 60.5% indicating GBT performs the best in being able to distinguish between the two classes. The model is able to predict 85% of churned users, with only a 4% error rate. We can also look at feature importance using GBT models featureImportances method. We can see that the most important feature is `num_bad_recc` which relates to bad interactions with the service such as thumbs downs.

## Issues:
- IBM watson notebook timeout and fail to connect to kernel
- AWS EMR keyerror when using GBT model see stack similar stackoverflow question [here](https://stackoverflow.com/questions/58910023/keyerror-when-training-a-model-with-pyspark-ml-on-aws-emr-with-data-from-s3-buck_).

## References
Project completed as part of Udacity DataScience Nanodegree.
Data provided is from fictional Digital Music Service provider "Sparkify"





