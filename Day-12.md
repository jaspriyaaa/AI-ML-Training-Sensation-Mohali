# Day 12: Polynomial Regression – House Price Prediction 🏠📈

## Overview

On Day 12, I learned **Polynomial Regression**, an extension of Linear Regression that helps model non-linear relationships between features and target variables. Unlike Linear Regression, which fits a straight line, Polynomial Regression can fit curved patterns in data by introducing polynomial features.

In this project, I used the **King County House Price Dataset** to predict house prices using a Degree-2 Polynomial Regression model.

---

# 🎢 The Roller Coaster Analogy: What is Polynomial Regression?

Polynomial Regression is used when data does not follow a straight-line relationship.

### Linear Regression
- Fits a straight line to the data.
- Suitable for linear relationships.
- Cannot accurately model curved trends.

### Polynomial Regression
- Extends Linear Regression by adding polynomial terms.
- Can capture curved and more complex relationships.
- Improves prediction accuracy for non-linear data.

### Example

Instead of:

y = b₀ + b₁x

Polynomial Regression uses:

y = b₀ + b₁x + b₂x²

The additional squared term allows the model to fit a curve.

---

# 🔌 Step 1: Import Libraries & Load Data

## Libraries Used

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import PolynomialFeatures
from sklearn.pipeline import make_pipeline
from sklearn.metrics import mean_absolute_error, r2_score
```

### Purpose of Libraries

- **NumPy** → Numerical computations
- **Pandas** → Data handling and analysis
- **Matplotlib** → Data visualization
- **train_test_split** → Splitting data into training and testing sets
- **LinearRegression** → Base regression algorithm
- **PolynomialFeatures** → Generates polynomial terms
- **make_pipeline** → Combines preprocessing and model training
- **mean_absolute_error** → Measures prediction error
- **r2_score** → Evaluates model performance

---

## Load Dataset

```python
df = pd.read_csv("kc_house_preprocessed.csv")
```

The preprocessed King County House Price dataset was loaded successfully.

---

## Select a Sample

```python
df_sample = df.sample(n=80, random_state=42)
```

A random sample of 80 records was selected for visualization and experimentation.

---

## Define Features and Target

```python
X = df_sample.drop(columns="price")
y = df_sample["price"]
```

### Input Features (X)
All house-related attributes except price.

### Target Variable (y)
House price.

---

## Split Data

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42
)
```

### Dataset Distribution

- Training Data → 80%
- Testing Data → 20%

The training set is used to teach the model, while the testing set evaluates performance on unseen data.

---

# 🤖 Step 2: Train the Polynomial Regression Model

## Create the Model

```python
poly_model = make_pipeline(
    PolynomialFeatures(degree=2),
    LinearRegression()
)
```

### Why Degree 2?

Degree 2 introduces squared terms such as:

- x²

These additional features help the model learn curved relationships.

---

## Train the Model

```python
poly_model.fit(X_train, y_train)
```

During training:

1. Polynomial features are generated.
2. Linear Regression learns the coefficients.
3. The model identifies patterns between house features and house prices.

---

# 📈 Step 3: Evaluate Model Performance

## Make Predictions

```python
y_pred = poly_model.predict(X_test)
```

The model predicts house prices for unseen test data.

---

## Mean Absolute Error (MAE)

```python
mae = mean_absolute_error(y_test, y_pred)
```

### Formula

MAE = Σ|Actual − Predicted| / n

### Interpretation

- Lower MAE = Better predictions
- Higher MAE = Larger prediction errors

---

## R² Score

```python
accuracy = r2_score(y_test, y_pred)
```

### Formula

R² = 1 − (SSres / SStot)

### Interpretation

- R² = 1 → Perfect prediction
- R² = 0 → No predictive power
- Higher values indicate better performance

---

## Training Accuracy

```python
accuracy1 = r2_score(y_train, ypre)
```

Training accuracy helps determine whether the model is learning effectively or overfitting.

---

# 🎨 Step 4: Visualize the Polynomial Curve

## Create Scatter Plot

```python
plt.scatter(X, y)
```

The scatter plot displays the actual house data points.

---

## Generate Smooth Input Range

```python
x_range = np.linspace(
    X['sqft_living'].min(),
    X['sqft_living'].max(),
    500
).reshape(-1,1)
```

This creates 500 evenly spaced values for smooth visualization.

---

## Predict Along the Curve

```python
y_range_pred = poly_model.predict(x_range)
```

Predictions are generated for every point in the range.

---

## Plot Polynomial Curve

```python
plt.plot(
    x_range,
    y_range_pred,
    color='crimson',
    linewidth=3
)
```

### Graph Components

- Blue Dots → Actual Data Points
- Red Curve → Polynomial Regression Prediction
- Title
- Axis Labels
- Grid
- Legend

---

# Key Learnings

✅ Understood Polynomial Regression

✅ Learned the difference between Linear and Polynomial Regression

✅ Used PolynomialFeatures to generate higher-order features

✅ Built a Polynomial Regression model using Scikit-Learn

✅ Evaluated model performance using MAE and R² Score

✅ Visualized non-linear relationships using a polynomial curve

✅ Applied Polynomial Regression to a real-world house price prediction dataset

---

# Conclusion

In Day 12, I explored Polynomial Regression and learned how it can model complex, non-linear relationships more effectively than Linear Regression. Using the King County House Price dataset, I trained a Degree-2 Polynomial Regression model, evaluated its performance using MAE and R² metrics, and visualized the resulting curve. This project demonstrated how polynomial features help machine learning models capture patterns that cannot be represented by a simple straight line.

---
