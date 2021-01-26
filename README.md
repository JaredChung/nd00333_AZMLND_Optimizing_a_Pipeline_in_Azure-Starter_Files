# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
The dataset contains data about bankmarketing and we seek to predict if the customer subscribes to a fixed term deposit. The features that are used in this model customer related information such as (Age, Education, Martial Status etc). This plays an important part because certain demographics are more receptible to the marketing campaign as banking related products are based on the life stages of an individual

The best performing model scored 91.12%
* Regulisation rate 4
* Number of iterrations 100

## Scikit-learn Pipeline
There were multiple steps involved which started off loading Data from the web, then cleaning the data, breaking the data up the data into X and Y. After this the data was then cleaned. next it needed to be broken into train and test. Hyperparameter tuning was then processed to find the best model. The best model was then selected and saved.

Random sampling method was used which was based defined range using "choice" so I would understand the predefined parameters and would train for shorter period. The benefit of using this method is because it supports early termination of low-performance runs.

The BanditPolicy was used as the early stopping policy which takes into account the slack factor and evaluation_interval. Bandit is an early termination policy.The policy early terminates any runs where the primary metric is not within the specified slack factor/slack amount with respect to the best performing training run.

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

* Expand AUTOML experiment longer, as within the configuration of the experiment it timeouted at 30 mins. This could be increased to 1-2 hours potentially. The benefit of doing this would be to have more models produced and thus the potential to have model out perform the current best run.
* Try different combinations of hyperparameters and train for longer iterrations. The hyperparameter model best results was at 100 which is the boundary of the experiment. This means that the model could still gain performance by increasing this parameter. Increasing it to say 500 may result in better performance.
* Add additional data e.g features. This will provide more information for the model to learn from. Some features to consider would be transactional data from the bank which more determine certain characteristics such as income or how much savings they have whhich would potentially be predictive variables of someone who would consider getting a Term Deposit.
* Explore feature engineering this may involve working with banking subject matter experts to outline potential segments they have an understanding of (e.g Baby Boomers, young professionals) This features can be built off the current ones. This may be additional information the model may learn from and thus perform better.
* Acquire more data is usually a good way to get additional performance. This is due to Machine Learning / Deep Learning models have more examples to learn from and thus generalise better



