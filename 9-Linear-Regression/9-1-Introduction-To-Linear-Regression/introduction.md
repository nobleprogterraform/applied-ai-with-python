Sure! Here’s the transcript organized into separate sections:

--

### History of Linear Regression
Let's discuss the history behind linear regression. A man named Francis Galton was studying the relationship between parents and their children, particularly the relationship between the heights of fathers and the heights of their sons. What he discovered was that a man's son tended to be roughly as tall as his father. However, Galton's breakthrough was that the son's height tended to be closer to the overall average height of all people.


### Basic Example of Linear Regression
Let's go ahead and begin to plot out a simple example of linear regression with only two data points, which is the simplest possible case. Here we have two data points: (2, 4) as one data point and (5, 10) as another data point. These two little black dots represent our data points. All we're trying to do when we calculate our regression line is draw a line that's as close to every dot as possible.

### Supervised Learning
Now, wouldn't it be great if we could apply this same concept to graphs with more than just two data points? By doing this, we could take multiple men and their sons' heights and do things like tell a man how tall we expect his son to be before he even has a son. This is the idea behind supervised learning. We're going to have a bunch of labeled data points, create a model (in this case, linear regression), and try to take unlabeled data, such as a father's height, and output a prediction of the son's height.

### Goal of Linear Regression
Our goal in linear regression is to minimize the vertical distance between all the data points and our line. In determining the best line, we attempt to minimize the distance between all the points and their distance to our line. There are lots of different ways to minimize this: the sum of squares error, sum of absolute errors, etc. However, all of these methods have a general goal of minimizing the distance between your line and the rest of the data points.

### Least Squares Method
For example, one of the most popular methods we just described is the least squares method. Here we have a couple of blue data points along the x and y axes, and we want to fit a linear regression line. The question is: how do we decide which line is the best fitting one? We can go ahead and use the least squares method, which is fitted by minimizing the sum of the squares of the residuals. The residuals for an observation are the difference between the observation's y value and the fitted line. In this image, the residuals are marked by the red lines, showing the difference between the true data points in blue and your fitted model line (the black line).

### Conclusion
In the next lecture, we're going to use scikit-learn in Python to create a linear regression model. Then you'll have your own portfolio project exercise, and afterwards, we'll go over the solutions to that project.

---