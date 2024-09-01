# Project Description

This program creates a model that utilizes random forest regression to predict the price of an uber taking into account, day of the week, time, distance, and the number of passengers. 
Tools being used in this program are python, jupyter notebook, numpy, pandas, calendar, and scikit learn.
All data used was pulled from https://www.kaggle.com/

## Step By Step Walkthrough

The program starts by importing necessary libraries and assigning them to abbreviations for coding ease. 
The training data excel file is then opened so that its columns can be manipulated to only contain the information needed to make the predictions.
A variable "pickup_datetime" is changed from data type object to data type datetime so we can use the calendar import later on in the code.
The same process of dropping unnecessary columns is done now on the testing data excel file.
Next, all of the distance values in the training file that are longer than the max distance seen in the testing file are removed to improve accuracy of the model.
Columns of specific hours, days, months, etc, are created using lambda to create anonymous function "x", and assigning it to the correct values from the calendar import.
A hashmap is then created to determine days of the week.
Variables "x" and "y" are then created, "y" being all of the fare amounts in the training file, and "x" being every other column in the training file.
"train_test_split" is then used to split both "x" and "y" into training and testing variables, and the test_size of .25 is used so the 75% of the data is used for training, which holds the original ratio of the file sizes for "train.csv" and test.csv".
The next step taken in the code is testing to see whether a linear regression model or a random forest model would be better to use for the program.
To see which model is better, we will train both types of models, and predict the values of "x_test", and then compare it to the actual values of "y_test" to see which model is more accurate.
The number used to see which model is more accurate is the root mean squared error, which is a value that can be within the range of 0-100 inclusive, and the closer to 0 the mean squared error is, the more accurate the prediction is.
Root mean squared error is calculated using "mean_squared_error" from the scikit import, and then finding the square root of it using numpy.
The linear model was trained and tested first, and it had a root mean squared error of 5.153543821806007, which is decently accurate.
Next, the random forest model was trained and tested, and it had a root mean squared error of 4.502888321830521, which is more accurate than the linear regression moddel, meaning we will be using a random forest for the rest of the program.
An out of bag error is calculated for the random forest amd it has a value of 0.262700023218537 which isn't super low, but it is decent for the amount of data that is trained.
The original testing file is then reopened, and the process of dropping unnecessary columns, changing "pickip_datetime" to a datetime data type, and creating a hashmap for the days of the week is done again.
The entire testing file is predicted using the same model we created earlier from fitting the "x_train" and "y_train" data.
A data frame is then created, using pandas, and it is written to the .csv file called "pred.csv".

## About Random Forest Models

Random forest regression is a technique of training certain models by creating a certain amount of trees, and using a random subset of the training data and features, also known as bootstrapping, and then averaging out the predictions for all the trees, also known as aggregation.
Random forest models are a great skill to have due to their ability to be used for regression and classification models.
In this model, I used parameter tuning to find the optimal number of trees for me to be 100, and the optimal max number of features to be three.
Out of bag error is a method of determining the error for random forest problems. 
To calculate out of bag error, the program takes specific data points, called out of bag samples, that were not used in a particular bootstrap, and uses those samples to test a specific tree.

## Ways To Make The Model More Accurate

The first and foremost way that would make the model more accurate would be to use more data, which could be said for almost sort of regression model.
Another way to make the model more accurate is more in depth parameter tuning.
I found 100 trees to be the most beneficial for me, because more trees slows the program down a lot, and only makes it slightly more accurate, but if this model is trained on a strong computer, more trees would be better.
If more trees are used, it might be best to change the max amount of features, but for 100 trees, 3 max features worked best. 
