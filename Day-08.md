# 📊 Day 8 Training Report: Data Visualization with Matplotlib & Seaborn

## 🎯 Objective

The objective of Day 8 was to understand the fundamentals of **Data Visualization** using Python. We explored how graphical representations help in understanding patterns, trends, distributions, comparisons, and relationships within datasets.

The session covered:

* Matplotlib Basics
* Seaborn Visualization Techniques
* Line Plots
* Bar Charts
* Scatter Plots
* Histograms
* Box Plots
* Correlation Heatmaps
* Real-World Data Analysis using the Titanic Dataset

---

# 🛠 Technologies Used

| Technology | Purpose                            |
| ---------- | ---------------------------------- |
| Python     | Programming Language               |
| NumPy      | Numerical Computations             |
| Pandas     | Data Manipulation                  |
| Matplotlib | Basic Data Visualization           |
| Seaborn    | Advanced Statistical Visualization |

---

# 📚 Part 1: Introduction to Data Visualization

## Why Data Visualization?

Data visualization helps convert raw numerical data into graphical representations, making it easier to:

* Identify trends
* Compare categories
* Detect outliers
* Understand distributions
* Analyze relationships between variables

---

# Module 1: Matplotlib

Matplotlib is one of the most widely used Python libraries for creating visualizations.

---

## 📈 Task 1: Line Plot

### Problem Statement

A superhero's speed was recorded over five days.

| Day | Speed |
| --- | ----- |
| 1   | 10    |
| 2   | 25    |
| 3   | 45    |
| 4   | 70    |
| 5   | 95    |

### Solution

```python
import matplotlib.pyplot as plt

days = [1, 2, 3, 4, 5]
speed = [10, 25, 45, 70, 95]

plt.figure(figsize=(7,4))
plt.plot(days, speed,
         color='red',
         marker='o',
         linestyle='--',
         linewidth=2,
         label='Speed')

plt.title("Superhero Speed Over Time")
plt.xlabel("Days")
plt.ylabel("Speed")
plt.legend()
plt.grid(True)
plt.show()
```

### Output

* Displays a line graph showing the increase in superhero speed over time.
* Helps identify trends and growth patterns.

### Key Learning

✅ Line plots are useful for showing changes over time.

---

## 📊 Task 2: Bar Plot

### Problem Statement

Compare the popularity of different treats.

| Treat       | Count |
| ----------- | ----- |
| Chocolates  | 15    |
| Gummy Bears | 8     |
| Cookies     | 22    |
| Ice Cream   | 12    |

### Solution

```python
treats = ['Chocolates', 'Gummy Bears', 'Cookies', 'Ice Cream']
counts = [15, 8, 22, 12]

plt.figure(figsize=(7,4))
plt.bar(treats, counts,
        color='skyblue',
        edgecolor='darkblue')

plt.title("Favorite Treats")
plt.xlabel("Treat Type")
plt.ylabel("Count")
plt.show()
```

### Output

* Vertical bars representing popularity of each treat.
* Cookies appear as the most preferred treat.

### Key Learning

✅ Bar charts are ideal for comparing categories.

---

## 📍 Task 3: Scatter Plot

### Problem Statement

Treasure chest locations were recorded on a map.

### Solution

```python
east_coords = [2,4,1,5,3,2.5,4.5,1.5]
north_coords = [3,1,4,2,5,3.5,1.5,4.2]

plt.figure(figsize=(7,4))

plt.scatter(
    east_coords,
    north_coords,
    marker='*',
    s=150
)

plt.title("Treasure Chest Locations")
plt.xlabel("East-West")
plt.ylabel("North-South")

plt.show()
```

### Output

* Individual points plotted on a coordinate system.
* Shows exact locations of treasure chests.

### Key Learning

✅ Scatter plots help visualize relationships and distributions of data points.

---

# Module 2: Seaborn

Seaborn is built on top of Matplotlib and provides visually appealing statistical graphics with less code.

---

## 📊 Task 4: Histogram with KDE

### Problem Statement

Analyze candy distribution among children.

### Solution

```python
import seaborn as sns

sns.histplot(
    data=df_candy,
    x="Candies",
    kde=True
)
```

### Output

* Histogram displays frequency distribution.
* KDE line shows the overall data trend smoothly.

### Key Learning

✅ Histograms help understand data distribution.

---

## 📦 Task 5: Box Plot

### Problem Statement

Analyze frog jump distances and identify unusual values.

### Dataset

```python
frog_jumps = [5,6,4,7,5,7,6,7,5,18,20]
```

### Solution

```python
sns.boxplot(data=df_frogs,
            x="JumpDistance")
```

### Output

* Box plot identifies extreme values.
* 18 and 20 appear as outliers.

### Key Learning

✅ Box plots are excellent for outlier detection.

---

## 🌡️ Task 6: Correlation Heatmap

### Problem Statement

Analyze relationships among video game features.

### Dataset

| Feature          |
| ---------------- |
| Play Time        |
| Popularity Score |
| Game Difficulty  |

### Solution

```python
corr_matrix = df.corr()

sns.heatmap(
    corr_matrix,
    annot=True,
    cmap="coolwarm"
)
```

### Output

* Displays correlation values.
* Positive and negative relationships become visually clear.

### Key Learning

✅ Heatmaps help analyze relationships among variables.

---

# 📝 Coding Exercises

---

## Exercise 1: Plant Growth Trend

### Question

Plot the height of a sunflower over five weeks.

### Solution

```python
weeks = [1,2,3,4,5]
heights = [5,12,22,35,48]

plt.plot(
    weeks,
    heights,
    color="green",
    marker="^",
    linestyle=":"
)

plt.title("Sunflower Growth Trend")
plt.xlabel("Weeks")
plt.ylabel("Height")
plt.show()
```

### Output

A line chart showing steady plant growth over time.

---

## Exercise 2: Candy Jar Counts

### Question

Compare counts of different candy brands.

### Solution

```python
candy_brands = ['Skittles','M&Ms','Snickers','KitKat']
candy_counts = [45,60,30,25]

plt.bar(
    candy_brands,
    candy_counts,
    color="gold",
    edgecolor="black"
)

plt.title("Candy Count")
plt.show()
```

### Output

Bar chart showing M&Ms as the highest-count candy.

---

## Exercise 3: Toy Car Speed Outlier Detection

### Question

Identify unusual speed values using a box plot.

### Dataset

```python
car_speeds = [12,14,13,15,12,11,14,13,35,12]
```

### Solution

```python
sns.boxplot(
    data=df_cars,
    x="Speed",
    color="lightgreen"
)
```

### Output

The value **35** is detected as an outlier.

### Key Learning

✅ Outliers can significantly affect analysis and should be investigated.

---

# 🚢 Part 2: Titanic Dataset Visualization Project

This section applied visualization techniques to a real-world dataset.

---

## Exercise 1: Dataset Loading

### Question

Load Titanic dataset and inspect initial records.

### Solution

```python
import pandas as pd

df = pd.read_csv("train.csv")

df.head(3)
```

### Output

Displays the first three records of the Titanic dataset.

---

## 🔎 Exercise 2: Passenger Age Distribution

### Question

Analyze age distribution of passengers.

### Solution

```python
plt.figure(figsize=(8,5))

sns.histplot(
    data=df,
    x="Age",
    kde=True,
    color="teal"
)

plt.title(
    "Titanic Passenger Age Distribution"
)

plt.show()
```

### Output

* Majority of passengers were young adults.
* KDE line reveals the age trend.

### Insight

Most passengers were between **20–35 years** of age.

---

## 🔎 Exercise 3: Survival Count Analysis

### Question

Compare passengers who survived and those who did not.

### Solution

```python
sns.countplot(
    data=df,
    x="Survived",
    palette="Set2"
)
```

### Output

Two bars representing:

* 0 → Did Not Survive
* 1 → Survived

### Insight

More passengers died than survived.

---

## 🔎 Exercise 4: Fare Distribution & Outliers

### Question

Analyze ticket fares and identify unusual values.

### Solution

```python
sns.boxplot(
    data=df,
    x="Fare",
    color="teal"
)
```

### Output

Several fare values appear far beyond the whiskers.

### Insight

The highest fare exceeded $500 while most passengers paid under $50.

---

## 🔎 Exercise 5: Age vs Fare Relationship

### Question

Study relationship between passenger age and ticket fare.

### Solution

```python
median_age = df['Age'].median()

df['Age'] = df['Age'].fillna(
    median_age
)

sns.scatterplot(
    data=df,
    x='Age',
    y='Fare',
    hue='Survived'
)
```

### Output

Scatter plot showing age, fare, and survival status.

### Insight

Higher-fare passengers often showed better survival rates.

---

## 🔎 Exercise 6: Correlation Heatmap

### Question

Analyze relationships among:

* Survived
* Passenger Class
* Age
* Fare

### Solution

```python
columns = [
    'Survived',
    'Pclass',
    'Age',
    'Fare'
]

corr = df[columns].corr()

sns.heatmap(
    corr,
    annot=True,
    cmap='coolwarm'
)
```

### Output

Correlation matrix displayed visually.

### Insight

* Fare has a positive relationship with survival.
* Passenger class negatively correlates with survival.
* Age has weaker correlation compared to other features.

---

# 📊 Visualization Summary

| Visualization | Purpose               |
| ------------- | --------------------- |
| Line Plot     | Trend Analysis        |
| Bar Plot      | Category Comparison   |
| Scatter Plot  | Relationship Analysis |
| Histogram     | Distribution Analysis |
| Box Plot      | Outlier Detection     |
| Heatmap       | Correlation Analysis  |
| Count Plot    | Frequency Analysis    |

---


# 🚢 Dataset Used

**Titanic Dataset (`train.csv`)**

The dataset contains passenger information such as:

| Column   | Description                       |
| -------- | --------------------------------- |
| Survived | Survival Status (0 = No, 1 = Yes) |
| Pclass   | Passenger Class                   |
| Name     | Passenger Name                    |
| Sex      | Gender                            |
| Age      | Passenger Age                     |
| Fare     | Ticket Fare                       |
| Embarked | Port of Embarkation               |

---

# Exercise 1: Load and Explore the Dataset

## Question

1. Import Pandas, NumPy, Matplotlib, and Seaborn.
2. Load the Titanic dataset (`train.csv`).
3. Display the first few rows.
4. Check for missing values.

---

## Solution

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("train.csv")

print(df.head())
print(df.isnull().sum())
```

---

## Output

* Dataset loaded successfully.
* First few records displayed.
* Missing values found mainly in:

  * Age
  * Cabin
  * Embarked

---

## Learning

Before visualization, it is important to inspect the dataset and identify missing values.

---

# 🔎 Detective Clue 1: Passenger Age Distribution

## Question

Create a histogram of passenger ages using Seaborn and display a KDE (Kernel Density Estimation) curve.

---

## Solution

```python
plt.figure(figsize=(8,5))

sns.histplot(
    data=df,
    x="Age",
    color="teal",
    kde=True,
    edgecolor="darkgreen"
)

plt.title("Titanic Passenger Age Distribution")
plt.xlabel("Age")
plt.ylabel("Frequency")

plt.show()
```

---

## Output

A histogram showing the distribution of passenger ages along with a smooth KDE curve.

---

## Observation

* Most passengers were young adults.
* Age values are concentrated between 20–40 years.
* Distribution is slightly right-skewed.

---

## Learning

Histograms help understand how data is distributed.

---

# 🔎 Detective Clue 2: Survival Analysis

## Question

Display the count of passengers who survived and those who did not survive.

---

## Solution

```python
plt.figure(figsize=(8,5))

sns.countplot(
    data=df,
    x="Survived",
    palette="Set2"
)

plt.title("Titanic Passenger Survival Count")
plt.xlabel("Survived")
plt.ylabel("Count")

plt.show()
```

---

## Output

A count plot containing two bars:

| Value | Meaning         |
| ----- | --------------- |
| 0     | Did Not Survive |
| 1     | Survived        |

---

## Observation

The number of passengers who did not survive was greater than those who survived.

---

## Learning

Count plots are useful for visualizing categorical frequencies.

---

# 🔎 Detective Clue 3: Ticket Price Distribution & Outliers

## Question

Create a box plot for the Fare column and identify outliers.

---

## Solution

```python
plt.figure(figsize=(8,5))

sns.boxplot(
    data=df,
    x="Fare",
    color="teal"
)

plt.title("Titanic Passenger Fare")

plt.show()
```

---

## Output

A box plot showing fare distribution and extreme fare values.

---

## Observation

* Most passengers paid relatively low fares.
* Several passengers paid exceptionally high fares.
* These high values appear as outliers.

---

## Learning

Box plots are highly effective for detecting unusual values in data.

---

# 🔎 Detective Clue 4: Age vs Fare Relationship

## Question

Create a scatter plot showing the relationship between passenger age and ticket fare.

Handle missing age values before plotting.

---

## Solution

```python
median_age = df['Age'].median()

df['Age'] = df['Age'].fillna(median_age)

sns.scatterplot(
    data=df,
    x='Age',
    y='Fare',
    hue='Survived'
)

plt.title("Age vs Fare Relationship")
plt.show()
```

---

## Output

Scatter plot showing:

* Passenger Age
* Ticket Fare
* Survival Status

---

## Observation

* Higher fare passengers appear more frequently in the survivor category.
* No strong linear relationship exists between Age and Fare.

---

## Learning

Scatter plots help identify relationships between numerical variables.

---

# 🔎 Detective Clue 5: Correlation Heatmap

## Question

Calculate the correlation between:

* Survived
* Pclass
* Age
* Fare

Visualize the results using a heatmap.

---

## Solution

```python
columns = [
    'Survived',
    'Pclass',
    'Age',
    'Fare'
]

corr = df[columns].corr()

sns.heatmap(
    corr,
    annot=True,
    vmax=1,
    vmin=-1,
    cmap="coolwarm"
)

plt.title("Correlation Heatmap")
plt.show()
```

---

## Output

A color-coded heatmap showing correlation values between variables.

---

## Observation

| Relationship       | Observation          |
| ------------------ | -------------------- |
| Fare vs Survived   | Positive Correlation |
| Pclass vs Survived | Negative Correlation |
| Age vs Survived    | Weak Correlation     |

---

## Learning

Heatmaps help understand relationships between variables and are widely used during Exploratory Data Analysis (EDA).

---

# 📚 Key Concepts Learned

| Visualization | Purpose               |
| ------------- | --------------------- |
| Histogram     | Data Distribution     |
| KDE Curve     | Smoothed Distribution |
| Count Plot    | Frequency Analysis    |
| Box Plot      | Outlier Detection     |
| Scatter Plot  | Relationship Analysis |
| Heatmap       | Correlation Analysis  |

---
## 🎯 Key Learning Outcomes

After completing Day 8, I learned:

- How to create effective visualizations using **Matplotlib** and **Seaborn**.
- How to analyze **trends, distributions, relationships, and outliers** in data.
- How to work with a real-world dataset (**Titanic Dataset**).
- How to handle missing values and prepare data for analysis.
- How to perform **Exploratory Data Analysis (EDA)** using different visualization techniques.
- How to use **line plots, bar charts, scatter plots, histograms, box plots, and heatmaps** effectively.
- How data visualization helps in extracting meaningful insights and supports **data-driven decision-making**.

---

## ✅ Conclusion

Day 8 focused on understanding and applying **Data Visualization** techniques using **Matplotlib** and **Seaborn**. Through various visualizations and a hands-on analysis of the **Titanic Dataset**, I explored data distributions, identified outliers, analyzed relationships between variables, and discovered meaningful patterns. This practical experience strengthened my understanding of **Exploratory Data Analysis (EDA)** and provided a strong foundation for future work in **Data Analytics, Machine Learning, and Artificial Intelligence**.
