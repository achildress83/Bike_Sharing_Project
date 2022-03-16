# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Aaron Childress

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
TODO: Add your explanation
The submission had be a dataframe with a datetime column along with the predictions.
I made a function that takes the test_df and preds and returns the submission_df
### What was the top ranked model that performed?
TODO: Add your explanation
The last model with the tuned hyparameters.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
TODO: Add your explanation
Looking at the histograms, temp and humidity are fairly normally distributed, windspeed is right skewed, and count has a sortof pareto distribution.

I added date features (year, month, week, weekday, day, hour) and set them to type categorical.
### How much better did your model preform after adding additional features and why do you think that is?
TODO: Add your explanation
My model performance on the the Kaggle test data improved ~7% by adding date features 
## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
TODO: Add your explanation
Adding hyperparameter tuning improved the model performance on the Kaggle data by another ~8%

### If you were given more time with this dataset, where do you think you would spend more time?
TODO: Add your explanation
Given the limited additional opportunities for feature engineering (based on the given features) and the fact that minimal hyperparameter tuning resulted in the 
largest performance improvement, I would spend more time tuning hyperparameters.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
model	hpo1	hpo2	hpo3	score
0	initial	default_vals	default_vals	default_vals	1.80
1	add_features	default_vals	default_vals	default_vals	1.68
2	hpo	default_vals	GBM num_boost_round [100] num_leaves [26, 36, 66], learning_rate[0.01, 0.001, 0.0001]	default_vals	1.54
### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: Replace the image below with your own.

![test_scores.png](img/model_test_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![train_scores.png](img/model_train_score.png)

## Summary
TODO: Add your explanation

I trained three AutoGluon models. The first was using all default settings to establish a baseline.
The second was light feature engineering to extract information from the date field.
The third was tuning the LightGBM hyperparameters to see if I could achieve a better result over default settings.
Further areas of improvement would focus on additinal hyperparameter tuning and herhaps removing some fields.
For example, the atemp and temp field are highly correlated (redundant) perhaps introducing a multicollinearity issue. 