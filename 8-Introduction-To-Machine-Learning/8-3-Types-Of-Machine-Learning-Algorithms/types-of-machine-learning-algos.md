Sure! Here’s the transcript separated into distinct sections:

---

### 1. Introduction
 we're going to discover the types of machine learning discussed in future lectures and sections of the course.
- So as we've mentioned before, there's two main types of machine learning we're covering in upcoming sections, and those are supervised learning algorithms and unsupervised learning algorithms.
- Keep in mind, we're gonna have future lectures that take much deeper dives into each of these different types of machine learning segments, supervised versus unsupervised.

### 2. Overview of Supervised and Unsupervised Learning
- For right now, we wanna give you a basic overview of the vocabulary necessary to distinguish supervised learning versus unsupervised learning.
- So formally speaking, supervised learning uses historical and labeled data.
- So we have two keywords there, historical and labeled, and then once we have historical and labeled data, that machine learning model can predict a future labeled or a future value.
- Unsupervised learning instead is applied to unlabeled data. The machine learning model then discovers possible patterns in the data.

### 3. Supervised Learning Explained
- So essentially what we have here is of supervised learning, you have previous historical data, and what you wanna do is predict a value or future label.
- For unsupervised learning, since you don't have that label, you actually need to discover or apply the label yourself to the data you currently have.
- Let's dive a little deeper into both of these since the formal definitions can sometimes be a little murky.
- So let's talk about supervised learning specifically first.
- Recall that supervised learning requires historical labeled data, and essentially what these two keywords mean is that historical data just essentially tells you that you have known results and data from the past.

### 4. Example of Supervised Learning
- So for example, if we think about predicting the price that a house should sell at, that's actually a supervised learning problem as long as we have historical labeled data.
- Historical just means that we know houses in the past have been sold and we've been able to look at the various features of the house, such as the square footage, square area, number of bedrooms, bathrooms, et cetera.
- Then most importantly for supervised learning is the fact that the data is labeled. Labeled data just means you know the desired output or result for the historical data.
- So what that would mean in the context of something like predicting the price a house should sell at is that the historical data not only has the features of the house, but also that house sold previously in the past, which means I have the known label, the price the house sold at.
- And so hopefully the machine learning algorithm could take a look at the various features of these past houses that have been sold, and then connect what features are important to the label, the price the house sold at in the past.
- That way when a new house comes on the market where we only know the features, we'd be able to predict the price it should sell at.

### 5. Types of Labels in Supervised Learning
- Now there's actually two main label types for supervised learning.
- There's the categorical value to predict, which is known as a classification task, and then there's the continuous value to predict, which is known as a regression task.
- The example we just talked about for the pricing prediction of a house about to be put on market is a regression task, since the label we're trying to predict is continuous, it's just a continuous dollar amount.
- But what happens with classification tasks? Well, classification tasks are essentially a subset of supervised learning where we're trying to predict an assigned category.
- So that could be something like having a bunch of data features for tumors that have already been extracted from previous people and measurements were done on those tumors, and we were able to correctly classify them into cancers versus benign tumors.
- Then hopefully, when you later on have some sort of surgery and someone extracts the tumor based off historical data, perhaps a machine learning algorithm can help guide a doctor to understand whether something was cancerous or benign.

### 6. Examples of Classification Tasks
- Same thing for something like fulfillment versus credit default. We essentially, if we're maybe having a supervised learning task for classification of whether or not someone is going to default on their loan, that's essentially two classes. Are they going to default or are they going to fulfill and pay off their loan?
- And then hopefully we can use previous people that have fulfilled their loan or defaulted on their loan as well as their features, maybe their annual salary or where they live, and use those features to predict whether a current or future customer is going to be credit worthy.
- Then this can go into much more complex areas like assigning image categories. Something like handwriting recognition is technically classification tasks.
- The previous examples here are known as binary classification, where you only have two classes, but we could expand on this and just have every single letter in the alphabet be its own class, which means if I show a machine learning algorithm an image of a single letter, it’ll be able to then predict the actual class for that letter, which in just case is what letter is the image corresponding to? Is it an A, B, C, D, et cetera.

### 7. Regression Tasks
- Now, let's talk about regression tasks. Recall regression tasks are then the subset of supervised learning that wants to predict a continuous value, such as future prices, for example, the future price of a home, what it should sell at, or things like electricity loads or things like test scores based off features of a student.
- Are they gonna test well or test poorly? What are they actually going to test from sum zero to 100 range? So these are all continuous values. They're not specific distinct categories.

### 8. Overview of Unsupervised Learning
- Now let's shift over to briefly discovering unsupervised learning.
- Unsupervised learning is a little bit harder to understand, which is why we're gonna cover it in much more detail later on in the course.
- But in general, we can think of unsupervised learning as trying to group and interpret data without a label.
- We're essentially then tasked to discover the label on our own.
- So for example, we could try clustering customers into separate groups based off their behavior features.
- And keep in mind, the downside to unsupervised learning is that there's no historical correct label, which means it's much harder to actually evaluate the performance of an unsupervised learning algorithm since you didn't have the correct label to begin with.
- So go ahead and don't worry too much about understanding fully unsupervised learning, because we're gonna go into it much more later on in the course.

### 9. Focus on Supervised Learning
- But for right now, what we're gonna do is the first batch of machine learning algorithms that we're gonna first focus on and learn about are falling under supervised learning.
- So, since we're first focusing on supervised learning to build an understanding of machine learning capabilities, what we're gonna do in the next lecture is take a much deeper dive through the full supervised learning process.
- Then later on in the course, we'll shift focus to unsupervised learning for things like clustering and dimensionality reduction, since those are a bit harder to understand if you go and dive first into those.
- So typically students will learn supervised learning first, and then they'll learn unsupervised learning. So we'll take that approach here as well, since it's typically easier for the student.

### 10. Conclusion and Next Steps
- So finally, before we go into the next section and dive into coding and linear regression, what we're gonna do is we're gonna have a really deep dive into the entire supervised machine learning process to set ourselves up for success.
- That way we can really focus on the algorithms in each of the future sections instead of trying to recall the larger picture of supervised machine learning.
- So coming up next, we're gonna do a whole overview of the supervised machine learning process.