# Day 13: Ridge & Lasso Regularization — Putting a Leash on our Robot!

## 📌 Overview

On Day 13, we explored **Regularization Techniques** used to prevent machine learning models from overfitting. After learning Polynomial Regression previously, we discovered that highly complex models can become too sensitive to training data and fail to generalize well on unseen data.

To solve this problem, we studied two powerful regularization methods:

* **Ridge Regression (L2 Regularization)**
* **Lasso Regression (L1 Regularization)**

Both techniques help control model complexity and improve prediction performance on new data.

---

## 🎓 The "Try-Hard Student" Analogy: What is Overfitting?

Imagine two students preparing for an examination:

### ❌ The Memorizer (Overfitting)

* Memorizes every practice question and answer.
* Performs perfectly on familiar questions.
* Struggles when new questions appear.
* Focuses on memorization rather than understanding.

### ✅ The Smart Learner (Regularization)

* Understands patterns and concepts.
* May not memorize every detail.
* Performs well on unseen questions.
* Generalizes knowledge effectively.

Machine learning models behave in a similar way. When a model memorizes training data instead of learning patterns, it becomes **overfitted**. Regularization helps the model focus on meaningful patterns rather than noise.

---

## 🎗️ The Two Types of Leashes

### 1. Ridge Regression (L2 Penalty) 🎗️

Ridge Regression adds a penalty to large coefficient values.

#### Characteristics:

* Shrinks feature weights toward zero.
* Does not make coefficients exactly zero.
* Reduces model complexity.
* Produces smoother prediction curves.
* Helps prevent overfitting.

#### Formula:

Ridge minimizes:

Loss = RSS + αΣ(w²)

Where:

* RSS = Residual Sum of Squares
* α (alpha) = Regularization strength
* w = Model coefficients

#### Advantages:

* Improves generalization.
* Handles multicollinearity well.
* Retains all features while reducing their impact.

---

### 2. Lasso Regression (L1 Penalty) 🪓

Lasso Regression applies a stricter penalty compared to Ridge.

#### Characteristics:

* Shrinks coefficients toward zero.
* Can set some coefficients exactly to zero.
* Automatically performs feature selection.
* Removes less important features.

#### Formula:

Lasso minimizes:

Loss = RSS + αΣ|w|

Where:

* RSS = Residual Sum of Squares
* α (alpha) = Regularization strength
* w = Model coefficients

#### Advantages:

* Reduces model complexity.
* Performs feature selection.
* Creates simpler and more interpretable models.

---

## 🔌 Step 1: Import our Tools & Load the Clean Data

### Libraries Used

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression, Ridge, Lasso
from sklearn.preprocessing import PolynomialFeatures
from sklearn.pipeline import make_pipeline
from sklearn.metrics import mean_absolute_error, r2_score
```

### Dataset

The preprocessed housing dataset:

```python
kc_house_preprocessed.csv
```

was loaded using Pandas.

### Purpose

The dataset contains house-related features and prices. It was used to train Polynomial Regression models and compare the effects of Ridge and Lasso Regularization.

---

## 🤖 Step 2: The Wild Robot (No Leash / Overfitting)

### Objective

Train a Degree-6 Polynomial Regression model without any regularization.

### Model

```python
wild_model = make_pipeline(
    PolynomialFeatures(degree=6),
    LinearRegression()
)
```

### Working

* Polynomial features of degree 6 were generated.
* Linear Regression was applied to these transformed features.
* No restriction was placed on coefficient values.

### Expected Behavior

Because the model is highly flexible:

* It tries to fit every training point.
* It may learn noise instead of patterns.
* The curve becomes excessively complex.
* Generalization ability decreases.

### Evaluation Metrics

```python
mean_absolute_error()
r2_score()
```

#### MAE (Mean Absolute Error)

Measures the average prediction error.

#### R² Score

Measures how well the model explains the variance in the target variable.

---

## 🎗️ Step 3: The Gentle Leash (Ridge Regularization)

### Objective

Apply Ridge Regularization to control the complexity of the Degree-6 Polynomial model.

### Model

```python
ridge_model = make_pipeline(
    PolynomialFeatures(degree=6),
    Ridge(alpha=0.1)
)
```

### Working

* Polynomial features are created.
* Ridge adds an L2 penalty to large coefficients.
* The model becomes smoother and more stable.

### Role of Alpha

```python
alpha = 0.1
```

Alpha controls regularization strength.

* Small alpha → weak regularization
* Large alpha → strong regularization

### Benefits

* Prevents extreme coefficient values.
* Reduces overfitting.
* Improves prediction stability.
* Keeps all features while reducing their influence.

### Evaluation

Predictions were generated and evaluated using:

```python
mean_absolute_error()
r2_score()
```

to compare performance with the unregularized model.

---

## 🪓 Step 4: The Strict Leash (Lasso Regularization)

### Objective

Apply Lasso Regularization to simplify the model and remove unnecessary polynomial terms.

### Model

```python
lasso_model = make_pipeline(
    PolynomialFeatures(degree=6),
    Lasso(alpha=100.0, max_iter=10000)
)
```

### Working

* Degree-6 polynomial features are generated.
* Lasso applies an L1 penalty.
* Less important coefficients are forced to zero.

### Role of Alpha

```python
alpha = 100.0
```

A higher alpha applies stronger regularization.

### Benefits

* Performs automatic feature selection.
* Produces simpler models.
* Removes irrelevant polynomial terms.
* Reduces overfitting.

### Evaluation

Model performance was measured using:

```python
mean_absolute_error()
r2_score()
```

and compared with Ridge and the unregularized model.

---

## 🎨 Step 5: Draw the Curves!

### Objective

Visualize the behavior of all three models on the same graph.

### Models Compared

1. Wild Robot (Polynomial Regression)
2. Ridge Regression
3. Lasso Regression

### Visualization Process

* Plot actual training data points.
* Generate a smooth range of input values.
* Draw prediction curves for all models.
* Compare flexibility and smoothness.

### Observations

#### Wild Robot

* Highly flexible.
* Can create unnecessary bends.
* More likely to overfit.

#### Ridge Regression

* Produces smoother curves.
* Controls excessive fluctuations.
* Maintains all features.

#### Lasso Regression

* Creates a simpler curve.
* Eliminates unnecessary polynomial terms.
* Focuses on the most important patterns.

### Conclusion from Graph

The graph clearly demonstrates that regularization prevents the model from becoming overly complex and improves its ability to generalize to unseen data.

---

# 📚 Key Concepts Learned

* Overfitting occurs when a model memorizes training data.
* Polynomial Regression can easily overfit with higher degrees.
* Regularization helps control model complexity.
* Ridge Regression uses L2 penalty and shrinks coefficients.
* Lasso Regression uses L1 penalty and can eliminate features.
* Alpha controls regularization strength.
* MAE and R² are useful evaluation metrics.
* Visualization helps compare model behavior and complexity.

---

# 🎯 Final Outcome

By the end of Day 13, I understood how Ridge and Lasso Regularization help prevent overfitting in Polynomial Regression models. I learned how to train, evaluate, and visualize regularized models and how these techniques improve generalization performance by controlling model complexity.
