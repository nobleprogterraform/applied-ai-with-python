
### 1. **Importing Libraries**
First, we need to import the necessary libraries for our analysis.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Set up for inline plotting
%matplotlib inline
```

**Explanation:**
- `pandas` is a powerful library for data manipulation and analysis. We’ll use it to load and handle our Titanic dataset.
- `matplotlib.pyplot` is used for creating static, interactive, and animated visualizations in Python.
- `seaborn` is built on top of Matplotlib and provides a high-level interface for drawing attractive statistical graphics.
- The `%matplotlib inline` command allows us to display plots directly within our Jupyter notebook.

### 2. **Loading the Dataset**
Next, we load the Titanic training data into a DataFrame.

```python
# Load the Titanic dataset
train_data = pd.read_csv('titanic_train.csv')

# Display the first few rows of the dataset
train_data.head()
```

**Explanation:**
- `pd.read_csv()` reads the CSV file containing our Titanic data into a DataFrame, a two-dimensional size-mutable data structure.
- `train_data.head()` shows the first five rows of the DataFrame, allowing us to understand its structure and the features we’ll be working with, like 'Survived', 'Pclass', 'Sex', etc.

### 3. **Exploratory Data Analysis (EDA)**
Now, let's check for missing values in the dataset.

```python
# Check for missing values
missing_data = train_data.isnull()
sns.heatmap(missing_data, cbar=False, yticklabels=False)
```

**Explanation:**
- `train_data.isnull()` returns a DataFrame indicating where values are missing (True for missing, False for present).
- `sns.heatmap()` visualizes the missing data. Here, yellow indicates missing data, allowing us to quickly identify which columns have the most missing values.

### 4. **Visualizing Survival Rates**
Next, we can visualize the survival rates.

```python
# Countplot of survival
sns.countplot(x='Survived', data=train_data)
plt.title('Survival Count')
plt.show()
```

**Explanation:**
- `sns.countplot()` creates a bar plot that shows the count of survivors (1) versus non-survivors (0).
- This helps us see the balance of our target variable, indicating how many passengers survived versus those who did not.

### 5. **Survival by Gender**
Now let’s explore how gender influenced survival rates.

```python
# Countplot of survival by sex
sns.countplot(x='Survived', hue='Sex', data=train_data, palette='RdBu')
plt.title('Survival by Gender')
plt.show()
```

**Explanation:**
- By setting `hue='Sex'`, we add a layer of information that lets us compare survival rates between male and female passengers.
- The palette makes it visually clear which gender corresponds to which color, enhancing the readability of our insights.

### 6. **Exploring Age Distribution**
Next, we can analyze the age distribution of passengers.

```python
# Distribution plot for age
sns.histplot(train_data['Age'].dropna(), bins=30, kde=True)
plt.title('Age Distribution')
plt.show()
```

**Explanation:**
- `sns.histplot()` provides a histogram of the age distribution, helping us visualize how many passengers fell into various age groups.
- The `dropna()` function removes any missing values from the Age column to ensure a clean histogram.

### 7. **Fare Distribution**
Finally, we will take a look at the fare prices.

```python
# Histogram of fare prices
train_data['Fare'].hist(bins=40, figsize=(10, 5))
plt.title('Fare Distribution')
plt.xlabel('Fare')
plt.ylabel('Number of Passengers')
plt.show()
```

**Explanation:**
- The histogram of fare prices shows us the distribution of ticket prices paid by passengers, revealing insights about socioeconomic status and class structure on the Titanic.


-----------------------------------------

### Lecture Summary: Data Cleaning in Logistic Regression

In this part, we focused on cleaning the dataset to prepare it for our logistic regression model. Here’s a breakdown of the key steps and code used.

---

#### 1. Filling Missing Age Values

**Code:**
```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Create a box plot to visualize age distribution by class
plt.figure(figsize=(10, 7))
sns.boxplot(x='Pclass', y='Age', data=train)
plt.show()
```
- **Explanation**: We created a box plot to visualize the age distribution across different passenger classes. This helps us understand how age correlates with class, indicating that first- and second-class passengers are generally older.

---

#### 2. Imputation Function for Age

**Code:**
```python
def imputes_age(cols):
    age = cols[0]
    pclass = cols[1]
    
    if pd.isnull(age):
        if pclass == 1:
            return 37  # Average age for first class
        elif pclass == 2:
            return 29  # Average age for second class
        else:
            return 24  # Average age for third class
    return age  # Return the actual age if not null
```
- **Explanation**: This function checks if the age value is null. If it is, it returns an average age based on the passenger's class. This method is more refined than simply using the overall mean.

---

**Code to Apply the Function:**
```python
train['Age'] = train[['Age', 'Pclass']].apply(imputes_age, axis=1)
```
- **Explanation**: We apply the `imputes_age` function to the `Age` and `Pclass` columns of the dataset, effectively filling in the missing age values based on class.

---

#### 3. Checking for Remaining Missing Values

**Code:**
```python
sns.heatmap(train.isnull(), yticklabels=False, cbar=False, cmap='viridis')
```
- **Explanation**: This heatmap visually checks for any remaining missing values in the dataset after our imputation.

---

#### 4. Dropping the Cabin Column

**Code:**
```python
train.drop('Cabin', axis=1, inplace=True)
```
- **Explanation**: We decided to drop the `Cabin` column due to too many missing values, which would not be useful for our model.

---

#### 5. Dropping Other Missing Values

**Code:**
```python
train.dropna(inplace=True)
```
- **Explanation**: This line removes any remaining rows with missing values, ensuring we have a complete dataset for our analysis.

---

#### 6. Handling Categorical Features

**Code for Dummy Variables:**
```python
sex_dummies = pd.get_dummies(train['Sex'], drop_first=True)
embarked_dummies = pd.get_dummies(train['Embarked'], drop_first=True)
```
- **Explanation**: We convert categorical variables (`Sex` and `Embarked`) into dummy variables. The `drop_first=True` parameter prevents multi-collinearity by dropping one category.

---

#### 7. Concatenating New Columns

**Code:**
```python
train = pd.concat([train, sex_dummies, embarked_dummies], axis=1)
```
- **Explanation**: We concatenate the new dummy variable columns back into the main dataframe.

---

#### 8. Dropping Unnecessary Columns

**Code:**
```python
train.drop(['Sex', 'Embarked', 'Name', 'Ticket'], axis=1, inplace=True)
```
- **Explanation**: We drop the original categorical columns since we have created dummy variables for them. Columns like `Name` and `Ticket` are also dropped as they do not provide useful numerical data.

---

#### 9. Dropping Passenger ID Column

**Code:**
```python
train.drop('PassengerId', axis=1, inplace=True)
```
- **Explanation**: The `PassengerId` column is dropped as it only serves as an index and does not contribute any predictive power.

---

### Final Data Check

**Code:**
```python
print(train.head())
print(train.columns)
```
- **Explanation**: We review the final dataset structure and column names to ensure everything is in order for modeling.

---

### Next Steps

We successfully cleaned the dataset by handling missing values and encoding categorical variables. In the next part, we will proceed to create and train our logistic regression model.

--------------------------------------

---

---

#### 1. Preparing the Data

**Separating Features and Labels:**

**Code:**
```python
X = train.drop('Survived', axis=1)
y = train['Survived']
```
- **Explanation**: We separate the dataset into features (`X`) and the target label (`y`). The `Survived` column is what we aim to predict.

---

#### 2. Splitting the Data

**Code:**
```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=101)
```
- **Explanation**: We use `train_test_split` from Scikit-learn to divide our data into training and testing sets. Here, 30% of the data is reserved for testing.

---

#### 3. Importing the Logistic Regression Model

**Code:**
```python
from sklearn.linear_model import LogisticRegression

log_model = LogisticRegression()
```
- **Explanation**: We import the `LogisticRegression` class and create an instance of the model, named `log_model`.

---

#### 4. Training the Model

**Code:**
```python
log_model.fit(X_train, y_train)
```
- **Explanation**: The model is trained using the `fit` method, which takes in the training features and labels.

---

#### 5. Making Predictions

**Code:**
```python
predictions = log_model.predict(X_test)
```
- **Explanation**: After training, we use the `predict` method to make predictions based on the test set features.

---

#### 6. Evaluating the Model

**Classification Report:**

**Code:**
```python
from sklearn.metrics import classification_report

print(classification_report(y_test, predictions))
```
- **Explanation**: The `classification_report` provides key metrics, including precision, recall, and F1 score, helping evaluate the model's performance.

---

**Confusion Matrix:**

**Code:**
```python
from sklearn.metrics import confusion_matrix

conf_matrix = confusion_matrix(y_test, predictions)
print(conf_matrix)
```
- **Explanation**: The confusion matrix shows the number of true positives, true negatives, false positives, and false negatives, giving further insight into model accuracy.

---

#### 7. Analyzing Model Performance

- **Discussion**: The results are promising, especially considering that we trained the model on a smaller subset of data. Suggestions for improvement include:
  - Using the entire training set after cleaning the test set.
  - Exploring feature engineering options, such as extracting titles from names or analyzing cabin locations.

---

#### 8. Open-Ended Exploration

- **Suggestions**: The lecturer encourages further exploration of the dataset, including potential feature engineering and trying different modeling approaches like Random Forests.
