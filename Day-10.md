# Day 10: Data Preprocessing — Washing & Sorting our Lego Blocks! 🧼🧱

Welcome back, Data Builders!

After filtering and cleaning the house dataset, the next step was **Data Preprocessing**. Machine Learning models perform best when data is clean, organized, and properly scaled. In this session, we prepared our dataset so it becomes suitable for training ML models.

**Why Preprocessing?**

Machine Learning algorithms work with numerical and structured data. If the dataset contains missing values, outliers, or inconsistent feature scales, model performance can decrease significantly. Data preprocessing helps transform raw data into a machine-learning-ready format.

---

## 🧼 Step 1: Import Preprocessing Gear & Load Data

### Objective

Load the filtered house dataset and prepare the required libraries for preprocessing tasks.

### Libraries Used

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.preprocessing import StandardScaler, MinMaxScaler
```

### Dataset Loading

```python
df = pd.read_csv('kc_house_filtered.csv')
df.head()
```

### Missing Value Check

```python
df.isnull().sum()
```

### Observation

The dataset columns:

* price
* bedrooms
* bathrooms
* sqft_living
* floors
* waterfront
* yr_built
* condition

contained no missing values initially.

---

## 🧩 Step 2: The Mystery of the Missing Values (Imputation)

### Concept

Real-world datasets frequently contain missing information. Missing values can affect model accuracy and prevent some algorithms from functioning correctly.

### What is Imputation?

Imputation is the process of replacing missing values with meaningful estimates.

### Why Median?

Instead of using the mean, the notebook uses the **median** because:

* It is resistant to extreme values.
* It is more reliable when outliers exist.
* It represents the middle value of the distribution.

### Example Scenario

To demonstrate imputation, some values from the **Year Built (yr_built)** column are intentionally hidden and then replaced using the median year.

### Benefits

* Preserves dataset size.
* Avoids data loss.
* Maintains statistical consistency.

---

## 🤠 Step 3: Taming the Giants (Outlier Capping)

### Concept

Outliers are extremely large or small values that differ significantly from the rest of the data.

Examples:

* Houses with unusually high prices.
* Houses with exceptionally large living areas.
* Extremely high bedroom counts.

These values can mislead Machine Learning algorithms.

### Outlier Detection

A boxplot was used to visualize outliers:

```python
sns.boxplot(data=df, y="sqft_living")
```

### IQR Method

The notebook applies the **Interquartile Range (IQR)** method.

Formula:

```text
IQR = Q3 - Q1
Lower Cap = Q1 - 1.5 × IQR
Upper Cap = Q3 + 1.5 × IQR
```

Where:

* Q1 = 25th percentile
* Q3 = 75th percentile

### Outlier Capping

Instead of deleting rows, values outside the acceptable range are capped to the upper or lower limits.

Benefits:

* Preserves records.
* Reduces the influence of extreme values.
* Improves model stability.

### Visualization

The notebook also uses:

```python
sns.histplot()
sns.boxplot()
```

to understand feature distributions and outlier behavior.

---

## ⚖️ Step 4: Balancing the Scales (Feature Scaling)

### Why Scaling?

Different features may have completely different ranges.

Example:

* House size → hundreds or thousands
* Bedrooms → single-digit values

Without scaling, larger-numbered features can dominate the model.

### Min-Max Scaling

Transforms values into the range:

```text
0 → 1
```

Implementation:

```python
from sklearn.preprocessing import MinMaxScaler

minmax_scaler = MinMaxScaler()
df['Scaled_size'] = minmax_scaler.fit_transform(df[['sqft_living']])
```

### Standard Scaling

Centers data around:

```text
Mean = 0
Standard Deviation = 1
```

Implementation:

```python
from sklearn.preprocessing import StandardScaler

std_scaler = StandardScaler()
df['Year_Scaled'] = std_scaler.fit_transform(df[['yr_built']])
```

### Benefits

* Faster model convergence.
* Better performance for distance-based algorithms.
* Prevents feature dominance.

---

## 🏷️ Step 5: Translating Words to Numbers (One-Hot Encoding)

### Problem

Machine Learning models cannot directly understand text labels.

Example category:

```text
Neighborhood
```

Values:

```text
Budget
Mid-Range
Premium
```

### One-Hot Encoding

A separate binary column is created for each category.

Example:

| Neighborhood | Loc_Budget | Loc_Mid-Range | Loc_Premium |
| ------------ | ---------- | ------------- | ----------- |
| Budget       | 1          | 0             | 0           |
| Premium      | 0          | 0             | 1           |
| Mid-Range    | 0          | 1             | 0           |

### Implementation

```python
pd.get_dummies()
```

### Benefits

* Converts text into numerical format.
* Prevents incorrect ranking of categories.
* Makes categorical data usable by ML algorithms.

---

## 🎉 Step 6: Final Review & Saving the Preprocessed Lego Blocks!

### Final Feature Selection

The notebook prepares the final dataset using:

```python
final_cols = [
    'price',
    'bedrooms',
    'bathrooms',
    'Scaled_size',
    'floors',
    'waterfront',
    'sqft_living',
    'condition',
    'Loc_Budget',
    'Loc_Mid-Range',
    'Loc_Premium'
]
```

### Creating Final Dataset

```python
df_final = df_encoded[final_cols]
```

### Saving the Dataset

```python
df_final.to_csv('kc_house_preprocessed.csv', index=False)
```

### Result

A clean and fully preprocessed dataset was generated, containing:

* Handled missing values
* Treated outliers
* Scaled numerical features
* Encoded categorical variables

This dataset is now ready for Machine Learning model training.

---

# Learning Outcomes

By completing Day 10, I learned how to:

* Detect and handle missing values using imputation.
* Understand the importance of median-based replacement.
* Identify and cap outliers using the IQR method.
* Visualize distributions using boxplots and histograms.
* Apply Min-Max Scaling and Standard Scaling.
* Convert categorical features into numerical format using One-Hot Encoding.
* Create a machine-learning-ready dataset.

---

# Conclusion

Data preprocessing is one of the most important stages of the Machine Learning pipeline. Clean, scaled, and properly encoded data helps improve model accuracy and reliability. Through this session, I gained hands-on experience in preparing raw housing data for future Machine Learning applications.
