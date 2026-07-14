# 📊 Day 9 Training - Exploratory Data Analysis (EDA) on House Price Dataset

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Plots-purple)

---

## 🎯 Objective

The objective of this assignment is to perform **Exploratory Data Analysis (EDA)** on the King County House Price Dataset and gain insights into the factors affecting house prices.

EDA helps in:

- Understanding the dataset
- Identifying trends and patterns
- Detecting outliers
- Finding relationships between variables
- Preparing data for Machine Learning models

---

# 📂 Dataset Overview

The dataset contains information about residential properties in King County, USA.

## Features Used

| Feature | Description |
|----------|-------------|
| price | Selling price of house |
| bedrooms | Number of bedrooms |
| bathrooms | Number of bathrooms |
| sqft_living | Living area (square feet) |
| floors | Number of floors |
| waterfront | Waterfront property (0 = No, 1 = Yes) |
| yr_built | Year built |
| condition | Overall house condition |

---

# 🛠️ Libraries Used

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

| Library | Purpose |
|----------|---------|
| Pandas | Data manipulation |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |

---

# Assignment Questions & Solutions

---

## Question 1: Load Dataset

### Code

```python
df = pd.read_csv('kc_house_data.csv')
print(df.shape)
```

### Output

```python
(21613, 21)
```

### Observation

- Total Records: 21,613
- Total Features: 21

---

## Question 2: Select Important Features

### Code

```python
friendly_cols = [
    'price',
    'bedrooms',
    'bathrooms',
    'sqft_living',
    'floors',
    'waterfront',
    'yr_built',
    'condition'
]

df = df[friendly_cols]
df.head()
```

### Output

| price | bedrooms | bathrooms | sqft_living | floors | waterfront | yr_built | condition |
|--------|----------|------------|-------------|---------|------------|-----------|------------|
| 221900 | 3 | 1.0 | 1180 | 1.0 | 0 | 1955 | 3 |
| 538000 | 3 | 2.25 | 2570 | 2.0 | 0 | 1951 | 3 |

### Observation

Selected only the most relevant columns for analysis.

---

## Question 3: Statistical Summary

### Code

```python
df.describe()
```

### Output

The summary provides:

- Count
- Mean
- Standard Deviation
- Minimum Value
- Maximum Value
- Quartiles

### Observation

Provides a quick understanding of data distribution and spread.

---

## Question 4: Dataset Information

### Code

```python
df.info()
```

### Output

```python
<class 'pandas.core.frame.DataFrame'>
21613 entries
8 columns
```

### Observation

- All selected features are numeric.
- No datatype issues observed.

---

## Question 5: Price Distribution Analysis

### Code

```python
plt.figure(figsize=(10,5))

sns.histplot(
    data=df,
    x="price",
    kde=True,
    bins=50,
    color='red'
)

plt.show()
```

### Output

📈 Histogram of House Prices

### Observation

- Most houses are concentrated in lower price ranges.
- Few houses have extremely high prices.
- Distribution is right-skewed.

---

## Question 6: Bedroom Distribution

### Code

```python
plt.figure(figsize=(10,5))

sns.countplot(
    data=df,
    x='bedrooms',
    hue='bedrooms',
    palette='Set2'
)

plt.show()
```

### Output

📈 Bedroom Count Plot

### Observation

- 3-bedroom houses are the most common.
- Houses with very high bedroom counts are rare.

---

## Question 7: House Size vs Price

### Code

```python
plt.figure(figsize=(10,6))

sns.scatterplot(
    data=df,
    x='sqft_living',
    y='price',
    hue='waterfront'
)

plt.show()
```

### Output

📈 Scatter Plot

### Observation

- Larger houses generally have higher prices.
- Waterfront houses tend to be more expensive.

---

## Question 8: Waterfront Impact on Price

### Code

```python
plt.figure(figsize=(8,5))

sns.boxplot(
    x='waterfront',
    y='price',
    data=df,
    hue='waterfront',
    palette='pastel'
)

plt.show()
```

### Output

📈 Box Plot

### Observation

| Waterfront | Impact |
|------------|---------|
| No | Lower median price |
| Yes | Higher median price |

### Conclusion

Waterfront properties significantly increase house value.

---

## Question 9: Condition vs Price

### Code

```python
plt.figure(figsize=(8,5))

sns.barplot(
    x='condition',
    y='price',
    data=df,
    hue='condition',
    palette='coolwarm'
)

plt.show()
```

### Output

📈 Bar Chart

### Observation

Better-maintained houses generally have higher average prices.

---

## Question 10: Correlation Heatmap

### Code

```python
plt.figure(figsize=(10,8))

corr = df.corr()

sns.heatmap(
    corr,
    annot=True,
    cmap='coolwarm',
    linewidths=0.5,
    vmin=-1,
    vmax=1
)

plt.show()
```

### Output

📈 Correlation Heatmap

### Key Findings

| Feature | Correlation with Price |
|----------|----------------------|
| sqft_living | Strong Positive |
| bathrooms | Moderate Positive |
| waterfront | Positive |
| condition | Weak Positive |

### Observation

House size has the strongest relationship with price.

---

## Question 11: Missing Value Check

### Code

```python
df.isnull().sum()
```

### Output

```python
price          0
bedrooms       0
bathrooms      0
sqft_living    0
floors         0
waterfront     0
yr_built       0
condition      0
```

### Observation

✅ No missing values found.

---

## Question 12: Save Processed Dataset

### Code

```python
df.to_csv(
    'kc_house_filtered.csv',
    index=False
)
```

### Output

```python
kc_house_filtered.csv saved successfully.
```

### Observation

Processed dataset is ready for future Machine Learning tasks.

---

# 📌 Key Insights

| Analysis | Insight |
|-----------|---------|
| House Size | Strongest factor affecting price |
| Waterfront | Increases house value significantly |
| Condition | Better condition leads to higher prices |
| Bedrooms | Most houses have 3 bedrooms |
| Outliers | Some extremely expensive properties exist |
| Missing Values | No missing values found |

---

# 🎓 Learning Outcomes

After completing this assignment, I learned:

- Data Loading using Pandas
- Feature Selection
- Statistical Analysis
- Data Visualization
- Histogram Analysis
- Scatter Plot Interpretation
- Box Plot Analysis
- Correlation Analysis
- Heatmap Visualization
- Missing Value Detection
- Dataset Exporting

---

# ✅ Conclusion

This Exploratory Data Analysis (EDA) project helped in understanding the King County House Price Dataset and identifying the major factors affecting house prices.

### Major Findings

- Larger houses tend to have higher prices.
- Waterfront properties are considerably more expensive.
- House condition positively impacts price.
- The dataset contains outliers that may require preprocessing.
- No missing values were found in the selected features.

The dataset is now ready for further preprocessing and Machine Learning model development.

---

## 🚀 Day 9 Completed Successfully
### Topic: Exploratory Data Analysis (EDA) on House Price Dataset
