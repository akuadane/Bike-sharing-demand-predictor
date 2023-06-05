# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Akayou Adane Kitessa

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
I realized that submitting prediction values that are below zero caused an error from the kaggle side. Therefore, I had to change every negative prediction to zero.

### What was the top ranked model that performed?
WeightedEnsemble_L3 was the top ranked model. 

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
The features season and weather were being seen as just numbers, which they are not. So changing their data type to categorical made sure the model sees them as categories. In addition, spliting the datetime into month, day and hour made our model create relations that wouldn't have before.

### How much better did your model preform after adding additional features and why do you think that is?
The score of the model went from 1.79715 to 0.69239. 

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
The score of the model went from 0.69239 to 0.58147.

### If you were given more time with this dataset, where do you think you would spend more time?
Next steps will be to further fine tuning the model to get the score below the 0.5 score.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|    model	        |hpo1	                             |hpo2	    |hpo3	    |score  |
|-------------------|------------------------------------|------------|-----------|-------|
| 	initial	        |default	                         |default	    |default	|1.79715|
| 	add_features	|default	                         |default	    |default	|0.69239|
| 	hpo	            |'CAT': {'depth': ag.space.Int(7,8),'l2_leaf_reg':ag.space.Int(0,20)}  |   RF': {'n_estimators':200,'min_samples_split': ag.space.Int(2,5)}    |default	|0.58147|
                      	

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![model_test_score.png](model_test_score.png)

## Summary
The first thing that I wanted to create was a baseline model. This model serves as a basis from which every other model is judged. To create this model, I used the default parameters from the AutoGluon Tabular Predictor. 

After creating the baseline model, I commenced explanatory data analysis. During this period, I figured the season and weather columns should be treated as categorical dtypes. Further more, I decided to include more features by separating the day, month and hour from the datetime. This removed some unnecessary fields such as seconds.

During hyperparameter tuning, I decided to tun the parameters of the CatBoost and RF models. The exact parameters used and the result can be found above.

There is still future work left to do. I need to spend more time tuning hyperparameters to achieve a better result. From other submission for this competition, I can see the score can go as low as 0.3. Therefore, the experimenting with different algorithms and hyperparameters is required to make the model better than it is now.
