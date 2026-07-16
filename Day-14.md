# Day 14: Classification & Logistic Regression

## 📌 Introduction

Welcome to Day 14 of the AI/ML Training Program. Today, we explored **Classification**, one of the most important supervised machine learning techniques.

Unlike Regression, where the goal is to predict continuous numerical values (such as house prices), Classification predicts **categories or labels**.

For this practical session, we used the famous **Titanic Dataset (train.csv)** to understand two major classification problems:

1. **Binary Classification** – Predicting between two possible outcomes.
2. **Multiclass Classification** – Predicting between three or more possible outcomes.

---

# What is Classification?

Classification is a supervised learning technique used when the target variable consists of predefined categories.

## Binary Classification

Binary Classification occurs when the target variable contains only two possible classes.

### Examples:

* Spam Email or Not Spam
* Fraudulent Transaction or Legitimate Transaction
* Survived or Not Survived (Titanic Dataset)

### Output:

* 0 or 1
* Yes or No
* True or False

---

## Multiclass Classification

Multiclass Classification occurs when the target variable contains three or more classes.

### Examples:

* Weather Prediction (Sunny, Rainy, Cloudy)
* Animal Classification (Dog, Cat, Bird)
* Passenger Class Prediction (1st, 2nd, 3rd Class)

### Output:

* One class selected from multiple possible classes.

---

# Section 0: Imports & Setup

Before building machine learning models, necessary libraries were imported.

## Libraries Used

### NumPy

Used for numerical operations and mathematical computations.

```python
import numpy as np
```

### Pandas

Used for loading, cleaning, and manipulating datasets.

```python
import pandas as pd
```

### Matplotlib

Used for creating plots and visualizations.

```python
import matplotlib.pyplot as plt
```

### Seaborn

Used for advanced and visually appealing statistical plots.

```python
import seaborn as sns
```

### Scikit-Learn Modules

#### train_test_split

Used for splitting data into training and testing sets.

#### LogisticRegression

Used to build classification models.

#### accuracy_score

Used to measure prediction accuracy.

#### confusion_matrix

Used to visualize correct and incorrect predictions.

#### classification_report

Used to evaluate Precision, Recall, and F1-Score.

---

# Section 1: Load Data & Exploration

The Titanic dataset was loaded using Pandas.

```python
df = pd.read_csv('train.csv')
```

The dataset contains information about Titanic passengers such as:

* Passenger ID
* Passenger Class
* Name
* Age
* Gender
* Fare
* Number of Siblings/Spouses
* Number of Parents/Children
* Survival Status

Dataset exploration helps understand:

* Number of rows and columns
* Missing values
* Data types
* Feature distributions

---

## Preprocessing the Data

Machine Learning algorithms cannot directly handle:

### 1. Missing Values

Some passengers had missing values in:

* Age
* Embarked

These values were filled using statistical methods.

### Age Imputation

Missing Age values were replaced with the median age.

```python
df['Age'] = df['Age'].fillna(df['Age'].median())
```

Median is preferred because it is less affected by outliers.

---

### Embarked Imputation

Missing Embarked values were replaced with the most frequent port.

```python
most_common_embarked = df['Embarked'].mode()[0]
df['Embarked'] = df['Embarked'].fillna(most_common_embarked)
```

---

### 2. Convert Categorical Values

The Sex column contains text values:

* male
* female

Machine Learning models require numerical input.

Therefore:

```python
female = 1
male = 0
```

```python
df['IsFemale'] = df['Sex'].map({'female':1,'male':0})
```

---

## Selected Features

The following features were used:

```python
features = ['Age', 'Fare', 'SibSp', 'Parch', 'IsFemale']
```

### Feature Meaning

| Feature  | Description                       |
| -------- | --------------------------------- |
| Age      | Passenger age                     |
| Fare     | Ticket price                      |
| SibSp    | Number of siblings/spouses aboard |
| Parch    | Number of parents/children aboard |
| IsFemale | Gender indicator                  |

---

# Section 2: Binary Classification (Predicting Survival)

## Objective

Predict whether a passenger survived the Titanic disaster.

### Target Variable

```python
Survived
```

Values:

* 1 → Survived
* 0 → Did Not Survive

---

## Intuition: Logistic Regression & The Sigmoid Function

Logistic Regression is designed for classification tasks.

### How Logistic Regression Works

### Step 1

Calculate a weighted sum of all input features.

### Step 2

Pass the result through the Sigmoid Function.

### Step 3

Convert the output into a probability between 0 and 1.

### Step 4

Apply a decision threshold.

If:

```text
Probability ≥ 0.5
```

Predict:

```text
Survived (1)
```

Otherwise:

```text
Not Survived (0)
```

---

## Sigmoid Function

The Sigmoid Function transforms any number into a probability value between 0 and 1.

### Formula

[
\sigma(z)=\frac{1}{1+e^{-z}}
]

### Properties

* Output always lies between 0 and 1.
* Converts linear predictions into probabilities.
* Forms an S-shaped curve.

---

## Step 1: Split the Data

The dataset was divided into:

### Training Set

80% of data

Used to train the model.

### Testing Set

20% of data

Used to evaluate performance.

```python
train_test_split(
X, y,
test_size=0.2,
random_state=42
)
```

---

## Step 2: Train the Model

A Logistic Regression model was created.

```python
binary_model = LogisticRegression(max_iter=1000)
```

The model was trained using:

```python
binary_model.fit(X_train,y_train)
```

The algorithm learns relationships between passenger characteristics and survival outcomes.

---

## Step 3: Make Predictions and Evaluate

Predictions were generated on unseen test data.

```python
y_pred = binary_model.predict(X_test)
```

---

### Accuracy

Measures overall correctness.

### Formula

[
Accuracy=\frac{Correct Predictions}{Total Predictions}
]

Higher accuracy indicates better performance.

---

### Confusion Matrix

A confusion matrix provides detailed prediction analysis.

#### True Positive (TP)

Predicted Survived and actually survived.

#### True Negative (TN)

Predicted Not Survived and actually did not survive.

#### False Positive (FP)

Predicted Survived but actually did not survive.

#### False Negative (FN)

Predicted Not Survived but actually survived.

---

### Classification Report

Provides:

#### Precision

Out of all predicted survivors, how many actually survived.

#### Recall

Out of all actual survivors, how many were correctly identified.

#### F1 Score

Balanced measure combining Precision and Recall.

---

# Section 3: Multiclass (Multilevel) Classification (Predicting Passenger Class)

## Objective

Predict a passenger's travel class.

### Target Variable

```python
Pclass
```

Possible values:

* 1 → First Class
* 2 → Second Class
* 3 → Third Class

---

## Features Used

```python
['Survived','Age','Fare','SibSp','Parch','IsFemale']
```

These features help identify which passenger class a person belonged to.

---

## How Logistic Regression Handles Multiclass Problems

Although Logistic Regression is naturally binary, it can be extended to multiclass classification.

### One-vs-Rest (OvR)

Creates separate binary classifiers for each class.

Example:

* Class 1 vs Others
* Class 2 vs Others
* Class 3 vs Others

The class with the highest probability is selected.

---

### Multinomial (Softmax)

Instead of multiple binary classifiers, Softmax calculates probabilities for all classes simultaneously.

The class with the highest probability becomes the final prediction.

---

## Train the Multiclass Model

The Logistic Regression model was trained using the multiclass dataset.

```python
multiclass_model = LogisticRegression(max_iter=1000)
```

Training:

```python
multiclass_model.fit(X_train,y_train)
```

---

## Evaluate the Multiclass Model

Predictions were generated:

```python
y_pred = multiclass_model.predict(X_test)
```

Evaluation included:

### Accuracy

Measures overall classification correctness.

### Multiclass Confusion Matrix

A 3×3 matrix was generated.

Rows:

* Actual Classes

Columns:

* Predicted Classes

This shows how many passengers were classified correctly and incorrectly.

---

### Classification Report

Generated for:

* Class 1
* Class 2
* Class 3

Metrics included:

* Precision
* Recall
* F1 Score

for each class separately.

---

# Section 4: Comparing Binary vs. Multiclass

| Aspect            | Binary Classification | Multiclass Classification  |
| ----------------- | --------------------- | -------------------------- |
| Number of Classes | 2                     | 3 or More                  |
| Example           | Survival Prediction   | Passenger Class Prediction |
| Function Used     | Sigmoid               | Softmax                    |
| Output            | Single Probability    | Multiple Probabilities     |
| Confusion Matrix  | 2 × 2                 | N × N                      |
| Prediction        | Yes/No                | One of Many Classes        |

---

# Exercises

## Exercise 1: Exploring Features

### Task

Add the Pclass feature to the Binary Classification model.

New Features:

```python
['Age','Fare','SibSp','Parch','IsFemale','Pclass']
```

Train a new Logistic Regression model and compare accuracy.

### Observation

Pclass strongly influences survival because first-class passengers had greater chances of rescue.

Therefore, model accuracy generally improves.

---

## Exercise 2: Play with Thresholds

### Task

Instead of the default threshold:

```python
0.5
```

Use:

```python
0.7
```

A passenger is predicted as survived only when survival probability is at least 70%.

### Observation

The model becomes more conservative.

Effects:

* Fewer passengers predicted as survivors.
* False positives decrease.
* Some actual survivors may be missed.
* Recall may decrease.

---

# Solutions

## Solution 1: Add Pclass to Binary Classification

### Result

Including Pclass improves prediction performance because passenger class was strongly related to survival probability.

Higher-class passengers generally received rescue priority.

---

## Solution 2: Change Threshold to 0.7

### Result

Increasing the threshold makes the model stricter.

Benefits:

* Reduces incorrect survival predictions.
* Increases confidence in positive predictions.

Drawback:

* More actual survivors may be classified as non-survivors.

This demonstrates the trade-off between Precision and Recall.

---

# Key Concepts Learned

* Difference between Regression and Classification
* Binary Classification
* Multiclass Classification
* Logistic Regression
* Sigmoid Function
* Softmax Function
* Feature Engineering
* Data Preprocessing
* Train-Test Split
* Accuracy Score
* Confusion Matrix
* Precision
* Recall
* F1 Score
* Decision Thresholds
* Model Evaluation Techniques

---

# Final Outcome

By the end of Day 14, I learned how to build Logistic Regression models for both Binary and Multiclass Classification problems using the Titanic Dataset. I understood data preprocessing, feature selection, the Sigmoid and Softmax functions, model training, prediction generation, evaluation metrics, confusion matrices, classification reports, and the effect of changing decision thresholds on model behavior.
