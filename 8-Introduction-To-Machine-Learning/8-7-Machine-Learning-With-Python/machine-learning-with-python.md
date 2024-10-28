# Lecture Transcript

## Introduction
Hello everyone and welcome to the machine learning of Python lecture. Now that we've gotten an introduction to machine learning, in this lecture we're going to discuss how we're going to be using Python and the scikit-learn package to perform machine learning with Python.

## Overview of Scikit-learn
Like I mentioned, we're going to be using the scikit-learn package. It's the most popular machine learning package for Python and it has a lot of algorithms already built into it. You'll need to install it at your command line or terminal using `conda install scikit-learn` if you have an Anaconda distribution or `pip install scikit-learn` if you have another distribution in Python.

## Basic Structure of Scikit-learn
Let's talk about the basic structure of how to use scikit-learn first. A quick review of the machine learning process: the machine learning process starts off with your data. Somehow you need to acquire data, and then the next step usually is to clean that data and format it so that the machine learning model can accept that. Before you actually give it to the machine learning model, however, you're going to split that cleaned data into a test set and a training set. You train your model on the training set and then in the next step you test your model on the test set, iterating your model and tuning the parameters until it's ready to deploy.

## Example of Scikit-learn Process
Now let's go over an example of the process to use scikit-learn. Now don't worry about memorizing any of this. We're going to get plenty of practice and review all of this when we actually start coding in subsequent lectures. This lecture is just the overview of the scikit-learn process. Don't worry about memorizing all the steps; you're going to see these steps over and over and we'll walk you through each of these steps when we actually code out the algorithms.

## Estimator Objects
Every algorithm in scikit-learn is exposed via an estimator object. First, you'll import the model, and the general form of this is to say `from sklearn.<family> import <model>`. For a specific example, let's say we want to perform linear regression, which is going to be the first machine learning algorithm we learn about. We'll go ahead and say `from sklearn.linear_model import LinearRegression`, where `linear_model` is the family of models and `LinearRegression` is the estimator object—that's the model itself.

## Instantiating the Model
Then the next step is to instantiate that model or estimator. The estimator parameters—all the parameters of an estimator—can be set when it's instantiated, and all of them have suitable default values. Later on, we're going to explore these values and parameters using `shift-tab` in the Jupyter notebook to check all the possible parameters. For example, you can instantiate a linear regression model by specifying a parameter `normalize=True`. After printing the model you just instantiated, you can check out the parameters that were defaulted to the model, such as `fit_intercept=True` and `copy_X=True`. Again, you actually don't need to specify `normalize=True`; those are just additional parameters you can use to tune the model to something more specific.

## Fitting the Model
Once you have your model created with your parameters, it's time to fit your model on some data. But remember, we should split this data into a training set and a test set. Let's go over an example of how we can do that. I'm going to go ahead and say `import numpy as np` in order to create some fake data. Then we can use scikit-learn to do a train-test split. Splitting our data into a training set and a testing set is the same for scikit-learn as it is for cross-validation.

## Train-Test Split
Then we have our sets of data, `X` and `y`, where `X` are the actual features and `y` is the actual label for each of those feature rows. Using `train_test_split`, you pass in `X` and `y` and you pass in the `test_size`. Again, don't worry too much about fully memorizing this or even fully understanding it. We're going to get a lot more practice with this process later on, but just as an overview, you can use `train_test_split` on your features and labels, and scikit-learn will automatically output your training set and your testing set. So we have `X_train`, `y_train`, `X_test`, and `y_test`, and you can see how these arrays are outputted here. Basically, you just have your labels for your training and testing data as well as your features for your training and testing data.

## Training the Model
Now that we have split the data, we can train or fit our model on the training data. This is done through the `fit` method. Basically, you take your model—remember we instantiated it as a linear regression estimator—and then you say `model.fit`, passing in your training data: `X_train` (the features of your data) and `y_train` (the training labels). Now the model has been fit and trained on the training data, and the model's ready to predict labels or values on the test set.

## Predicting and Evaluating
Keep in mind I'm showing an example of a supervised learning process. The process for an unsupervised model is going to be a little different because you're actually not going to have those labels. For a supervised learning model, we get the predicted values using the `predict` method. You would say `model.predict`, passing in your test data—those are your test features—and predictions off of that. Then you can evaluate your model by comparing your predictions to the correct values. The evaluation method depends on what sort of machine learning algorithm you are using; different evaluation methods are used for regression vs classification vs clustering, etc.

## Recap of Scikit-learn Methods
Let's go ahead and get a quick recap of all of this. Scikit-learn really strives to have a uniform interface across all methods, and we're going to see examples of these below. Every scikit-learn estimator object named `model` has the following methods available. You're going to be able to fit to the training data. For supervised learning applications, this expects two arguments: the data `X` and the labels `y`. For unsupervised learning applications, this only accepts a single argument—the data—which makes sense because unsupervised learning works with unlabeled data.

## Predicting with New Data
Estimators have a `predict` method which, given a trained model, predicts the label of a new set of data. This method accepts one argument, the new data (which is going to be `X_new`). In the previous example, it was `X_test`. This returns the learned label for each object in the array. Also available for unsupervised and supervised estimators is the `predict_proba` method. For classification problems, some estimators provide this method which returns the probability that a new observation has in each categorical label. In this case, the label of the highest probability is returned by the model's `predict` method.

## Scoring the Model
For classification or regression problems, you also have a `score` method available. Most estimators implement this method, and scores are between 0 and 1, with a larger score indicating a better fit. Also available in unsupervised estimators is the `transform` method, which allows us to transform new data into the new basis.

## Model Fit-Transform Method
Finally, we have the `fit_transform` method. Some unsupervised estimators implement this method which more efficiently performs a fit and a transform on the same input data.

## Choosing an Algorithm
Right now, you may be wondering, "How do I choose an algorithm: classification vs regression vs clustering?" If you go ahead and just Google search "scikit-learn algorithm cheat sheet," you should get an image that looks like this. This is from the official scikit-learn documentation. It’s a bit of a decision tree or a walkthrough guide on how to actually go about choosing an algorithm. If we go ahead and start off, you'll see that it asks you if you have more than 50 samples. If not, you should really get more data. If you do have more than 50 samples, then it asks you: "Are you trying to predict the category or predict the quantity?" 

## Conclusion
All right. Let's go ahead and start using Python for machine learning by starting our first machine learning algorithm, which is going to be linear regression.