# Lecture Transcript

## Welcome Back
Welcome back, everyone.

## Introduction to Regression Evaluation
We just discussed how to evaluate performance for classification problems. Now let's understand how to evaluate performance for regression tasks. So we're gonna take a moment to discuss how do we evaluate a model which is performing some sort of regression task.

## Definition of Regression
And in general, a regression is a task when a model attempts to predict continuous values unlike those classification tasks where we're trying to predict categorical values. So you may have heard of some evaluation metrics, such as accuracy, or recall, or precision, like we just discussed. However, these sort of metrics aren't going to be useful for regression problems. It doesn't really make sense to calculate the accuracy or recall of a regression task since you're actually classifying things. Instead, you're predicting a continuous value. So we need new metrics designed for those continuous values.

## Example of Regression Task
For example, imagine we're attempting to predict the price of a house given its features. That would be a regression task or attempting to predict the country a house is in given its features. That would be a classification task. And again, we're focused right now on how to evaluate that regression task where a label is continuous and it's not separate categories.

## Common Regression Metrics
So we're gonna discuss the most common evaluation metrics for regression, which are mean absolute error, mean squared error, and then root mean squared error.

## Mean Absolute Error
So let's begin with the simplest, which is mean absolute error. And this one's the easiest to understand. Essentially all you're gonna do is you're gonna compare your predictions. And remember we're comparing a continuous value here since this is a regression task. We're gonna compare our predictions to the true y label. For example, compare the actual prediction of the house price with the true house price. And what we do is we just take the difference between the true price minus our predicted price. That's y hat. And we take the absolute value of that. And the reason we take the absolute value is because technically our predictions could be over or under the true value. And since we want to average this out across all our predictions, we take the absolute value.

## Limitations of Mean Absolute Error
Okay? So that's the mean absolute error. Essentially, you're just taking the differences between your prediction versus the true label. You take the absolute value of that and then you average that out for all your predictions. Now the issue with mean absolute error is it won't punish large errors. So here we have what's known as Anscombe's quartet and we can see here that we have a wide variety of different scatters of data points here. However, the line of best fit for all of these is actually the same. So we wanna make sure that we're aware of situations like this. For example, let's take a look at this specific situation where we have one point that's a huge outlier. So we want our error metrics to actually account for these.

## Mean Squared Error
So what we can do is actually use mean squared error. And this is the mean of the squared errors. So what we're doing here is we're gonna take the difference between the true value minus our predicted value, and we're gonna square it. And as you can imagine, when we actually take that square, the larger errors are noted more than with mean absolute error, which makes mean squared error more popular because you're really gonna punish your model for those outlier situations that it's not fitting to. And we no longer need to take the absolute value because anything squared ends up being positive.

## Limitations of Mean Squared Error
However, there's another issue that we run into with mean squared error. That squaring of the actual label minus our prediction actually also squares the units themselves. So for example, if we're predicting the price of a house then our error metric of mean absolute error would be in dollars. But with mean squared error, we end up getting an error metric in units of dollars squared, which is difficult to interpret.

## Root Mean Squared Error
So the way we fix this is with the root mean squared error, essentially at the end, you just take the square root of your mean squared error. So this is the most popular because it does both punish those larger error values and at the end of the day, it has the same metrics or same units as y.

## Common Student Questions
Now the most common question again I get from students is, “Hey, is this value of root mean squared error I got good?” And as always, context is everything. Let's imagine you were performing some sort of machine learning model, and you got a root mean squared error of $10. And you're asking me is this good enough root means squared error? Well, it really depends on the context of the situation.

## Contextual Evaluation
A root mean squared error of $10 would be fantastic if you're predicting the price of a house since $10 is tiny compared to the average price of a house. But if your machine learning model was supposed to predict the price of a candy bar based on its features and your root mean squared error was $10, that's actually really bad. So what you should do is you should compare your error metric for the regression task to the average value of the label. That is the mean value in your dataset to try to get an intuition of its overall performance.

## Role of Domain Knowledge
And as always, domain knowledge also plays a really important role here. So machine learning, again, it's not done in a vacuum, it's usually done with a collaborative process. So if you're predicting the prices of a house and you wanted to get an idea if your root means squared error was good or not, it's probably then a good idea to start talking to someone with experience like a real estate agent.

## Conclusion
Okay, so now we understand the different metrics we can use for evaluating the performance of a regression task.