# 🕵️‍♂️ Day 9: Exploratory Data Analysis (EDA) — Detective Work on House Prices! 🏠📊

Welcome back, Data Detectives!

Today we have a very exciting mystery to solve. We have a case file containing information about **21,613 houses** from King County, USA. Some houses are small, some are huge, some are affordable, and some cost millions of dollars.

### 🎯 Our Mission

Find out what factors make a house expensive or affordable using Exploratory Data Analysis (EDA).

EDA allows us to:

* Explore the dataset
* Discover hidden patterns
* Identify outliers
* Understand relationships between features
* Prepare data for future Machine Learning models

---

# 🔍 Step 1: Load Our Spy Gear (Libraries)

Before solving the mystery, every detective needs tools.

### Tools Used

| Library       | Purpose                       |
| ------------- | ----------------------------- |
| Pandas 🐼     | Organizing and analyzing data |
| NumPy 🔢      | Numerical calculations        |
| Matplotlib 🎨 | Data visualization            |
| Seaborn 📊    | Statistical visualizations    |

### Code

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv('kc_house_data.csv')

print("Detective spy gear successfully loaded! Ready to analyze.")
```

### Output

```python
Detective spy gear successfully loaded! Ready to analyze.
```

### Observation

All required libraries were successfully imported and the investigation is ready to begin.

---

# 📁 Step 2: Opening the Case File (Loading the Data)

Let's load the dataset and see how large our investigation is.

### Code

```python
df = pd.read_csv('kc_house_data.csv')

print(f"Case File Opened! We have {df.shape[0]:,} houses and {df.shape[1]} raw columns.")
```

### Output

```python
Case File Opened! We have 21,613 houses and 21 raw columns.
```

### Available Columns

| Feature Categories |
| ------------------ |
| Price Information  |
| Bedrooms           |
| Bathrooms          |
| House Size         |
| Waterfront         |
| Floors             |
| Year Built         |
| Location Features  |
| Condition          |
| Grade              |
| Basement Details   |

### Observation

The dataset contains 21 features describing different aspects of houses.

---

# ✂️ Step 3: Simplifying the Clues (Keeping Only What We Understand)

The raw dataset contains many technical columns.

To make our investigation easier, we selected only the most meaningful and intuitive features.

### Selected Features

| Feature     | Meaning             |
| ----------- | ------------------- |
| price       | House Price         |
| bedrooms    | Number of Bedrooms  |
| bathrooms   | Number of Bathrooms |
| sqft_living | Living Area (sq ft) |
| floors      | Number of Floors    |
| waterfront  | Waterfront Property |
| yr_built    | Construction Year   |
| condition   | House Condition     |

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

### Sample Output

| price  | bedrooms | bathrooms | sqft_living | floors | waterfront | yr_built | condition |
| ------ | -------- | --------- | ----------- | ------ | ---------- | -------- | --------- |
| 221900 | 3        | 1.0       | 1180        | 1.0    | 0          | 1955     | 3         |
| 538000 | 3        | 2.25      | 2570        | 2.0    | 0          | 1951     | 3         |

### Observation

We reduced complexity and focused only on features that directly impact house prices.

---

# 📊 Step 4: The Detective Statistics

Every detective needs a summary of clues.

Using `.describe()` we can uncover important statistics.

### Code

```python
df.describe()
```

### Important Findings

| Metric                    | Value       |
| ------------------------- | ----------- |
| Average House Price       | ~$540,088   |
| Average Bedrooms          | ~3.37       |
| Average Bathrooms         | ~2.11       |
| Average House Size        | ~2080 sq ft |
| Average Construction Year | ~1971       |

### Observation

* Most houses have around 3 bedrooms.
* Average house size is approximately 2080 sq ft.
* Average selling price exceeds $500,000.

### Detective Conclusion

The dataset contains a wide variety of houses ranging from small affordable homes to luxury properties.

---

# 📈 Step 5: Visualizing Clue 1 — The Price Mountain (Univariate Analysis)

Now let's investigate how house prices are distributed.

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

### Visualization

📊 Histogram of House Prices

### Observation

* Most houses fall within lower and medium price ranges.
* A small number of houses are extremely expensive.
* Distribution is positively skewed.

### Detective Conclusion

The market contains several luxury properties acting as outliers.

---

# 🛏️ Step 6: Visualizing Clue 2 — The Bedroom Count

Let's find out how many bedrooms most houses have.

### Code

```python
sns.countplot(
    data=df,
    x='bedrooms',
    hue='bedrooms',
    palette='Set2'
)

plt.show()
```

### Observation

| Bedrooms | Frequency Trend |
| -------- | --------------- |
| 3        | Highest         |
| 4        | Second Highest  |
| 5+       | Less Common     |

### Outlier Investigation

```python
giant_outlier = df[df['bedrooms'] > 10]
print(giant_outlier)
```

### Finding

Some houses have unusually high bedroom counts, including an extreme case with more than 30 bedrooms.

### Detective Conclusion

Most families prefer 3-bedroom houses, while extremely large houses represent rare outliers.

---

# 📏 Step 7: Connecting the Dots — Size vs. Price (Bivariate Analysis)

Does a larger house cost more?

### Code

```python
sns.scatterplot(
    data=df,
    x='sqft_living',
    y='price',
    hue='waterfront'
)

plt.show()
```

### Observation

* Strong upward trend visible.
* Larger houses generally have higher prices.
* Waterfront homes often appear among higher-priced properties.

### Detective Conclusion

House size is one of the strongest indicators of price.

---

# 🌊 Step 8: Waterfront Houses — Living by the Lake (Bivariate Analysis)

Does living near water increase property value?

### Code

```python
sns.boxplot(
    x='waterfront',
    y='price',
    data=df,
    hue='waterfront'
)

plt.show()
```

### Findings

| Waterfront | Price Trend              |
| ---------- | ------------------------ |
| No         | Lower median price       |
| Yes        | Much higher median price |

### Observation

Waterfront properties consistently command premium prices.

### Detective Conclusion

A lake or waterfront view significantly increases house value.

---

# 🛠️ Step 9: House Condition — Does Neater Mean Costlier?

Let's investigate whether better-maintained houses are worth more.

### Code

```python
sns.barplot(
    x='condition',
    y='price',
    data=df,
    hue='condition'
)

plt.show()
```

### Observation

* Houses in better condition generally have higher average prices.
* Poor-condition houses sell for lower values.

### Detective Conclusion

Condition plays an important role in determining house value.

---

# 🗺️ Step 10: The Detective's Map — The Connection Matrix

To understand how features relate to each other, we use a correlation heatmap.

### Code

```python
correlation_map = df.corr()

sns.heatmap(
    correlation_map,
    annot=True,
    cmap='coolwarm',
    linewidths=0.5,
    vmin=-1,
    vmax=1
)

plt.show()
```

### Key Correlations

| Feature     | Correlation with Price |
| ----------- | ---------------------- |
| sqft_living | Strong Positive        |
| bathrooms   | Moderate Positive      |
| waterfront  | Positive               |
| condition   | Weak Positive          |

### Observation

House size has the strongest relationship with house price.

### Detective Conclusion

The bigger the house, the more expensive it tends to be.

---

# 🕵️‍♂️ Summary of Discoveries

### Major Findings

| Discovery                           | Insight                                           |
| ----------------------------------- | ------------------------------------------------- |
| 🏠 Size Matters Most                | House size has the strongest impact on price      |
| 🌊 Waterfront Bonus                 | Waterfront homes are significantly more expensive |
| 🛏️ Most Common Layout              | 3-bedroom houses dominate the dataset             |
| ⚠️ Outliers Detected                | Houses with extremely high bedroom counts exist   |
| 🛠️ Better Condition = Higher Price | Well-maintained homes sell for more               |
| 📊 Clean Dataset                    | No significant missing-value issues found         |

---

# 💾 Saving the Processed Dataset

### Code

```python
df.to_csv(
    'kc_house_filtered.csv',
    index=False
)
```

### Output

```python
kc_house_filtered.csv saved successfully
```

---

# 🎓 What I Learned

Through this assignment, I learned:

* Exploratory Data Analysis (EDA)
* Data Cleaning & Feature Selection
* Statistical Summaries using Pandas
* Histogram Analysis
* Count Plot Visualization
* Scatter Plot Analysis
* Box Plot Interpretation
* Correlation Analysis
* Heatmap Visualization
* Outlier Detection
* Dataset Preparation for Machine Learning

---

# ✅ Final Conclusion

This detective investigation successfully uncovered the key factors affecting house prices in King County.

### Final Answers to Our Mystery

✔️ Larger houses generally cost more.

✔️ Waterfront properties are significantly more expensive.

✔️ House condition positively affects selling price.

✔️ Most homes contain 3 bedrooms.

✔️ A few unusual outliers exist and should be handled before machine learning.

✔️ The dataset is clean and ready for predictive modeling.

🚀 **Day 9 Completed Successfully — Exploratory Data Analysis on House Price Dataset**


## 🚀 Day 9 Completed Successfully
### Topic: Exploratory Data Analysis (EDA) on House Price Dataset
