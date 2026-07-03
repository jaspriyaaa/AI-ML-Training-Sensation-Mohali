# 🚀 Day 7 Training Report: Pandas Data Manipulation & Data Analysis

## 📖 Introduction

On Day 7 of the Python Data Analytics Training Program, I explored **Pandas**, one of the most powerful and widely used Python libraries for data analysis and manipulation.

The objective of this session was to understand how real-world datasets can be loaded, explored, filtered, cleaned, and analyzed using Pandas DataFrames. This training provided practical experience with handling structured data and performing common data preprocessing operations required in Data Science and Machine Learning.

---

# 🎯 Learning Objectives

After completing this training, I was able to:

* Understand the importance of Pandas in Data Analysis.
* Create and manipulate Pandas Series and DataFrames.
* Load datasets from CSV files.
* Explore dataset structure and metadata.
* Select and filter data efficiently.
* Handle missing values.
* Perform grouping and aggregation operations.
* Generate meaningful insights from datasets.

---

# 🛠️ Technologies Used

| Technology       | Purpose                      |
| ---------------- | ---------------------------- |
| Python           | Programming Language         |
| Pandas           | Data Analysis & Manipulation |
| Jupyter Notebook | Development Environment      |
| CSV Dataset      | Data Source                  |

---

# 📚 What is Pandas?

Pandas is an open-source Python library designed for data manipulation and analysis.

It provides fast, flexible, and expressive data structures that make working with structured data easier.

### Key Features

* Easy handling of tabular data.
* Built-in support for missing values.
* Powerful filtering and selection operations.
* Grouping and aggregation capabilities.
* Data cleaning and preprocessing tools.
* CSV, Excel, JSON, SQL support.

---

# Module 1: Understanding Pandas Data Structures

Pandas mainly provides two data structures:

| Data Structure | Description                       |
| -------------- | --------------------------------- |
| Series         | One-dimensional labeled array     |
| DataFrame      | Two-dimensional tabular structure |

---

## 1. Creating a Pandas Series

### Program

```python
import pandas as pd

ages = pd.Series([23, 45, 31, 19], name="Age")
print(ages)
```

### Output

```text
0    23
1    45
2    31
3    19
Name: Age, dtype: int64
```

### Explanation

A Series is a one-dimensional data structure capable of storing data of any type.

In this example:

* Four age values are stored.
* Pandas automatically assigns indexes.
* The series is named "Age".

---

## 2. Creating a DataFrame

### Program

```python
import pandas as pd

student = {
    "Name": ["Sima", "Ria", "Ryan"],
    "Course": ["BCA", "BTech", "BCA"],
    "RollNo": [1, 2, 3]
}

df = pd.DataFrame(student)

print(df)
```

### Output

| Name | Course | RollNo |
| ---- | ------ | ------ |
| Sima | BCA    | 1      |
| Ria  | BTech  | 2      |
| Ryan | BCA    | 3      |

### Explanation

A DataFrame is a two-dimensional data structure similar to a spreadsheet or SQL table.

Each column can store different data types.

---

# Module 2: Reading and Exploring Datasets

Most real-world data is stored in CSV files.

## Loading a Dataset

```python
df = pd.read_csv("data.csv")
```

The dataset is loaded into a DataFrame for further analysis.

---

## Dataset Inspection Methods

| Function   | Purpose                    |
| ---------- | -------------------------- |
| head()     | Displays first rows        |
| tail()     | Displays last rows         |
| info()     | Dataset information        |
| shape      | Number of rows and columns |
| columns    | Displays column names      |
| describe() | Statistical summary        |
| dtypes     | Data types of columns      |

---

### Example: Viewing First Records

```python
df.head()
```

Output displays the first 5 rows of the dataset.

---

### Example: Dataset Information

```python
df.info()
```

This provides:

* Total entries
* Number of columns
* Missing values
* Memory usage
* Data types

---

# Module 3: Data Selection and Slicing

Selecting specific portions of data is essential during analysis.

---

## Selecting a Single Column

```python
df["Income"]
```

Returns a Series containing all income values.

---

## Selecting Multiple Columns

```python
df[["CustomerID", "Age", "Income"]]
```

Returns only the specified columns.

---

## Using loc[]

Label-based indexing.

```python
df.loc[0:3, "CustomerID":"Income"]
```

### Explanation

* Select rows 0–3.
* Select columns from CustomerID to Income.

---

## Using iloc[]

Position-based indexing.

```python
df.iloc[1:4, 1:4]
```

### Explanation

* Select rows using positions.
* Select columns using positions.

---

## Comparison

| Method | Type             |
| ------ | ---------------- |
| []     | Column Selection |
| loc[]  | Label-Based      |
| iloc[] | Position-Based   |

---

# Module 4: Boolean Indexing and Filtering

Filtering helps extract specific records based on conditions.

---

## Example 1: High Income Customers

```python
df[df["Income"] > 60000]
```

### Explanation

Displays customers whose income exceeds ₹60,000.

---

## Example 2: Female Customers Above Age 25

```python
df[(df["Age"] >= 25) & (df["Gender"] == "F")]
```

### Explanation

Displays female customers aged 25 years or older.

---

## Boolean Mask

```python
mask = df["Income"] > 60000

df[mask]
```

### Explanation

A boolean mask stores True/False values which are then used to filter rows.

---

# Module 5: Handling Missing Values

Missing values are common in real-world datasets.

Pandas represents missing values as:

```python
NaN
```

---

## Detecting Missing Values

```python
df.isnull().sum()
```

### Purpose

Displays the number of missing values in each column.

---

## Filling Missing Values

### Using Mean

```python
mean_age = df["Age"].mean()

df["Age"] = df["Age"].fillna(mean_age)
```

### Explanation

Missing age values are replaced with the average age.

---

## Removing Missing Records

```python
df = df.dropna(subset=["Gender"])
```

### Explanation

Rows containing missing Gender values are removed.

---

## Common Techniques

| Method   | Purpose               |
| -------- | --------------------- |
| fillna() | Fill missing values   |
| dropna() | Remove missing values |
| mean()   | Average               |
| median() | Middle value          |
| mode()   | Most frequent value   |

---

# Module 6: GroupBy and Aggregation

GroupBy is one of the most powerful Pandas features.

It helps summarize large datasets.

---

## Average Income by Gender

```python
df.groupby("Gender")[["Income", "Age"]].mean()
```

### Explanation

Calculates average income and age for each gender category.

---

## Average Metrics by Purchase Status

```python
df.groupby("Purchased")[["Income", "Age"]].mean()
```

### Explanation

Compares customers who purchased products versus those who did not.

---

## Aggregation Functions

| Function | Description        |
| -------- | ------------------ |
| mean()   | Average            |
| sum()    | Total              |
| min()    | Minimum            |
| max()    | Maximum            |
| count()  | Count              |
| std()    | Standard Deviation |

---

# 📝 Assignment Questions with Solutions

---

# Question 1

### Create a Pandas Series containing four age values and display it.

## Solution

```python
import pandas as pd

ages = pd.Series([23, 45, 31, 19], name="Age")

print(ages)
```

## Output

```text
0    23
1    45
2    31
3    19
Name: Age, dtype: int64
```

---

# Question 2

### Create a DataFrame containing student details.

## Solution

```python
import pandas as pd

student = {
    "Name": ["Sima", "Ria", "Ryan"],
    "Course": ["BCA", "BTech", "BCA"],
    "RollNo": [1, 2, 3]
}

df = pd.DataFrame(student)

print(df)
```

## Output

| Name | Course | RollNo |
| ---- | ------ | ------ |
| Sima | BCA    | 1      |
| Ria  | BTech  | 2      |
| Ryan | BCA    | 3      |

---

# Question 3

### Find all customers whose income is greater than 60000.

## Solution

```python
df[df["Income"] > 60000]
```

## Output

Displays all customer records where Income > 60000.

---

# Question 4

### Replace missing age values with the mean age.

## Solution

```python
mean_age = df["Age"].mean()

df["Age"] = df["Age"].fillna(mean_age)
```

## Output

All missing Age values are replaced with the average age.

---

# Question 5

### Calculate average income and age by gender.

## Solution

```python
df.groupby("Gender")[["Income", "Age"]].mean()
```

## Output

| Gender | Avg Income       | Avg Age          |
| ------ | ---------------- | ---------------- |
| F      | Calculated Value | Calculated Value |
| M      | Calculated Value | Calculated Value |

---

# 📊 Key Concepts Practiced

* Data Loading
* Data Exploration
* Data Inspection
* Data Cleaning
* Missing Value Handling
* Filtering Records
* Boolean Indexing
* GroupBy Operations
* Aggregations
* Statistical Analysis

---

# 🎯 Skills Gained

After completing this training session, I gained practical experience in:

* Working with real-world datasets
* Cleaning and preprocessing data
* Performing exploratory data analysis
* Generating summaries and insights
* Preparing datasets for Machine Learning workflows

---

# ✅ Conclusion

Day 7 was focused on mastering Pandas fundamentals and data manipulation techniques. Through hands-on exercises and assignments, I learned how to efficiently load, inspect, clean, filter, and summarize datasets using Pandas.

These concepts are essential for Data Analysis, Data Science, Business Intelligence, and Machine Learning projects, making Pandas one of the most valuable tools in the Python ecosystem.

---

## 🌟 Day 7 Status


**Topic:** Pandas Data Manipulation & Data Analysis

**Tools Used:** Python, Pandas, Jupyter Notebook

**Outcome:** Successfully performed data exploration, cleaning, filtering, and aggregation operations using Pandas.
