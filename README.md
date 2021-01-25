# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
The dataset contains data about bankmarketing and we seek to predict if the customer subscribes to a fixed term deposit.

The best performing model scored 91.12%
* Regulisation rate 4
* Number of iterrations 100

## Scikit-learn Pipeline
There were multiple steps involved which started off loading Data from the web and they cleaning the data and then breaking up the data into X and Y. Then the data needed to be cleaned. After this the data was broken into train and test. Hyperparameter tuning was then processed to find the best model. The best model was then selected and saved.

The decided to choose a parameter selector which was based defined range using "choice" so I would understand the predefined parameters and would train for shorter period

The BanditPolicy was used as the early stopping policy which takes into account the slack factor and evaluation_interval. 

## AutoML
After the AutoML was run, prefittedsoftvotingclassifier model was the best run and it produced an accuracy of 91.7%. 

The AutoMLConfig was used to set
* experiment_timeout_minutes=30
* task="classification"
* primary_metric="accuracy"
* label_column_name="y"
* n_cross_validations=5
* training_data.

The hyperparameters used by the AutoML
* min_samples_split= 0.244
* min_weight_fraction_leaf=0.0
* n_estimators=10
* n_jobs=1

## Pipeline comparison

The Model performance of Hyperdrive was 91.12% which was lower than AUTO ML of 91.7%

The reason for this is because Hyperdrive was based only on logistic regression and a set criteria of parameter search. AUTOML on the otherhand was based on many different types of models including parameter search.

In saying this, Hyperdrive was quicker to train than AUTOML.

## Future work
**What are some areas of improvement for future experiments? Why might these improvements help the model?**
Some areas of improvement for future experiments can be:

* Expand AUTOML experiment longer
* Try different combinations of hyperparameters and train for longer iterrations
* Add additional data e.g features
* Explore feature engineering
* Acquire more data



