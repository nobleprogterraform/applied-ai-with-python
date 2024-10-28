# Lecture Transcript

## Welcome and Introduction
Welcome everyone to this lecture on evaluating performance, particularly for classification problems. In the next lecture, we'll discuss evaluating performance for regression tasks.

## Importance of Performance Metrics
So we just learned that after our machine learning process is complete, we're going to be using performance metrics to evaluate how our model actually did. And we keep mentioning the fact that we train our model on the training data and then we're gonna use some sort of metric to actually see how it performed on either the test set or the validation set. So let's go ahead and discuss what that actually means.

## Key Classification Metrics
What classification metrics are we going to be using? And the key classification metrics we should be understanding are accuracy, recall, precision, and F1-score. But first, we should understand the reasoning behind these metrics and how they will actually work in the real world.

## Correct vs. Incorrect Predictions
Typically, in any classification task, your model can actually really only achieve two results: either your model was correct in its prediction or your model was incorrect in its prediction. And all classification metrics stem from this idea. Now, fortunately, incorrect versus correct also expands the situations where you have multiple classes, such as trying to predict categories of more than two. For example, you have category A, B, C, D. You can either be correct in predicting the correct category or incorrect in predicting the right category.

## Binary Classification Example
Now for the purpose of explaining the metrics, we're gonna go ahead and simplify this to what's known as a binary classification situation, binary meaning two. So there's only two available classes, either class zero or class one. And this idea is going to expand to multiple classes as well. But for simplification, let's imagine just a binary classification situation. So in our example, we're gonna attempt to predict if an image is a dog or a cat, and we'll actually perform this task later on during the convolutional neural network portion of this course.

## Model Training Process
Now, since it's a supervised learning problem, what we're gonna need to do first is fit or train a model on training data. That means we're gonna have images that someone's already gone ahead and labeled dog or cat. So we know the correct answer on these images. Then we're gonna test that model on the testing data. So we're gonna show new images that the model hasn't seen before, get the model's prediction, and then compare the results of the model prediction to the correct answer that we already know.

## Evaluation Process
So once we have the model's predictions from X_test data, we compare it to the true Y values, the correct labels. So let's actually diagram this process out. Let's imagine we've already trained our model on some training data, and now it's time to actually evaluate the model's performance. This is where our test dataset comes in. So we take a test image from what we're gonna label X_test, X meaning features. So the actual image itself is a feature and this is from the test set. And there is a corresponding correct label from y_test. So we have the feature or image X, and that's the test image, and we also have the correct label from y_test. And in this case we can see that this image is an image of a dog. 

## Prediction Comparison
So what we're gonna do is we're just gonna feed in the features, in this case, the image into our already trained model, and then the model is going to make some prediction. So the model predicts that this is a dog, and then what we do is we compare the prediction to the correct label. So this dog equal dog, and in this case, it was correct. However, maybe it predicted that this image was a cat, and in this case, this comparison to the correct label would be incorrect. And these are essentially just the only two situations. Either you're right or you're wrong, correct or incorrect.

## Counting Predictions
So we'll repeat this process for all the images in our X_test data, and at the end we will have a count of correct matches and a count of incorrect matches. And the key realization here that we need to make is that in the real world, not all incorrect or correct matches hold equal value. So let's kind of hone in on what we mean by that.

## Limitations of a Single Metric
So in the real world, a single metric won't tell the complete story. And to understand all of this, let's bring back those four metrics we mentioned and see how they're actually calculated. We could organize our predicted values compared to the real values in what is known as a confusion matrix. So we'll touch upon the confusion matrix later on, but first, let's talk about accuracy.

## Accuracy
Accuracy is one of the most common classification metrics and luckily, it's also the easiest to understand. It's just really intuitive what it's measuring. Accuracy and classification problems is the number of correct predictions made by the model, divided by the number of, or the total number of predictions. So again, it's the number of correct predictions divided by the total number of predictions, essentially answering the questions, how many predictions did you get right as a percentage? So for example, let's imagine that X_test set was 100 images and our model correctly predicted 80 images. Then we have 80 divided by 100 or 0.8 or 80% accuracy. 

## Balanced vs. Unbalanced Classes
And accuracy is really useful when the target classes are well-balanced. So what does that mean, well-balanced? Well, in our example, that would mean we have roughly the same amount of cat images as we have dog images throughout our data. So it means the actual labels themselves are roughly equally represented in the dataset. But let's imagine that we have what's known as an unbalanced class situation. In this case, accuracy is actually not a good metric to use.

## Thought Experiment
So let's do a little thought experiment. Let's imagine that in this test set we had 99 images of dogs and only 1 image of a cat. Now, if our model was simply a line that just always predicted dog no matter what image it saw, then we would actually get 99% accuracy on this particular test set because by just always saying dog, 99 images are dogs and 1 image is of a cat, then we only missed one. So that's why you have to be aware of the downside of accuracy. And the downside really comes when you have an unbalanced class situation. If your classes are roughly balanced, then accuracy is a very nice intuitive method or a metric to understand. However, if you have an unbalanced class, you can see in this particular situation where it starts to represent a problem, and that's where the other metrics come into play.

## Recall and Precision
So again, in this situation, we'll want to understand recall and precision. That helps us understand how well it's performing on unbalanced classes. Recall is the ability of a model to find all the relevant cases within a dataset. And the precise definition of recall is the number of what's known as true positives. And we'll kind of hone in on that later when we see the confusion matrix, but it's the number of true positives divided by the number of true positives plus the number of false negatives. And the precision is the ability of a classification model to identify only the relevant data points where precision is defined as the number of true positives divided by the number of true positives plus the number of false positives.

## Trade-off Between Recall and Precision
Now, often, you have a trade-off between recall and precision. While recall expresses the ability to find all the relevant instances in a dataset, precision expresses the proportion of the data points our model says was relevant that actually were relevant. And then F1-score is essentially a combination of these two. In cases where we want to find an optimal blend of precision and recall, we can combine the two metrics using what is known as the F1-score. 

## F1-Score Calculation
And the F1-score is the harmonic mean of precision and recall, taking both metrics into account in the following equation. So this isn't just taking the average of recall, precision. It's taking the harmonic mean of them. And so here we have the formula for F1-score or F1-score is equal to two, times precision, times recall in the numerator, and then divided by precision plus recall in the denominator. So the reason we use the harmonic mean instead of just a simple mean or simple average is because it's gonna punish extreme values.

## Importance of Harmonic Mean
For example, if you created a classifier that had a precision of one, meaning essentially perfect precision, and a recall of zero, essentially the worst recall possible, if you were just to take the simple average of this, then it would be 0.5, but the F1-score, because it's taking a harmonic mean, we have precision times recall there at the top which means you'd get zero times one at the top and you get an F1-score of zero. So this is really nice because it lets you punish extreme differences between the precision and recall. So it gives you kind of a fair assessment of that trade-off between precision and recall.

## Confusion Matrix Overview
Now we can also view all correct classified versus incorrectly classified images in the form of a confusion matrix. So confusion matrix looks something like this. We have the underlying true conditions, so that's the true correct label. And we can think of condition as positive or negative, such as actually being a dog or not being a dog, or oftentimes is used in a medical diagnosis, such as having presence of a disease versus not having presence of a disease.

## Components of Confusion Matrix
And then we have the model's predicted condition. So prediction positive or prediction negative. And I think when it comes to confusion matrices, it's often easiest to first get an intuition if you think of this as a diagnostic test for having some sort of disease present in a person after maybe you take a blood sample and run it through your model. So for example

, true positives is the number of cases that are actually positive, and the model also predicts them as positive. True negatives is the number of cases that are actually negative and the model also predicted them as negative. False positives are cases that are actually negative but the model predicted them as positive. And false negatives are cases that are actually positive but the model predicted them as negative.

## Derived Metrics from Confusion Matrix
And what we can do is we can derive the various metrics from the confusion matrix. So accuracy is defined as true positives plus true negatives divided by the total number of predictions, so in this case that's true positives plus true negatives plus false positives plus false negatives. We can calculate precision from the confusion matrix as true positives divided by true positives plus false positives. Recall is true positives divided by true positives plus false negatives.

## Common Student Questions
Now, a common student question that I receive is, “What is a good enough accuracy?” And the answer to that question is always, it depends. So it can depend on a few factors like the context of the problem, the distribution of the labels in the dataset, and also the domain of the application you're looking at. 

## Disease Diagnosis Example
For example, let's say you're building a model to predict whether someone has a disease or not. In that case, you might want a very high recall because you want to make sure that you find all the people who actually have the disease, and you might be okay with lower precision because you're okay with some false positives. However, if you were building a model to filter spam emails, you might want to prioritize precision over recall because you don't want to incorrectly classify a legitimate email as spam.

## Contextual Considerations
So it's really important to understand the context behind your metrics, and this is something you should be discussing with your domain experts. There isn't a blanket answer for what constitutes good metrics, and as always, context is key.

## Conclusion
So in conclusion, this was a summary of how we evaluate classification models. In the next lecture, we'll be discussing how to evaluate performance for regression tasks.