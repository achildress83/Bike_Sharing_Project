# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Aaron Childress

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
TODO: Add your explanation
The submission had be a dataframe with a datetime column along with the predictions.
I made a function that takes the test_df and preds and returns the submission_df
### What was the top ranked model that performed?
TODO: Add your explanation
The base model with AutoGluon presets was the best I achieved.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
TODO: Add your explanation
Looking at the histograms, temp and humidity are fairly normally distributed, windspeed is right skewed, and count has a sortof pareto distribution.

I added date features (year, month, week, weekday, day, hour) and set them to type categorical.
### How much better did your model preform after adding additional features and why do you think that is?
TODO: Add your explanation
My model didn't perform better. It performed worse. I think AutoGluon parses dates and engineers date fields internally, so manually feature engineering date fields was potentially just adding dimensionality to the dataset, not useful information.
## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
TODO: Add your explanation
Again, I didn't get any improvement from hyperameter tuning. I set auto_stack=True, which I discovered is the default with presets='best_quality'. I also doubled time_limit.

### If you were given more time with this dataset, where do you think you would spend more time?
TODO: Add your explanation
I looked at the correlation table and saw that the atemp category potentially created some multicolinearity issues with temp and holiday had little correlation with count so I dropped these columns ( I could have dropped workingday as well). I ran an experiment on the reduced dataset with baseline model and got no improvement.

I would spend more time on hyperparameter tuning (i.e. increasing layers, adjusting learning rate, etc)
### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
model	hpo1	hpo2	hpo3	score
0	initial	time_limit=600	presets=best_quality	auto_stack=False	1.39
1	add_features	time_limit=600	presets=best_quality	auto_stack=False	1.78
2	hpo	time_limit=1200	presets=best_quality	auto_stack=True	1.80

### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: Replace the image below with your own.

![scores.png](img/scores.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![train_scores.png](img/train_scores.png)

## Summary
TODO: Add your explanation
Not sure if/what I'm overlooking, but still trying to make sense of why I was unable to achieve a better model relative to the baseline.