# 🚀 Day 6 Training Report – NumPy Fundamentals

## 📖 Introduction

NumPy (Numerical Python) is one of the most important Python libraries used in Data Science, Artificial Intelligence, Machine Learning, Scientific Computing, and Data Analysis. It provides support for powerful multidimensional arrays and mathematical functions that make numerical computations faster and more efficient than traditional Python lists.

During this training session, I explored the core concepts of NumPy, including array creation, indexing, slicing, broadcasting, vectorization, and performance optimization.

---

# 🎯 Learning Objectives

By the end of this session, I was able to:

* Understand the importance of NumPy in Python programming.
* Create and manipulate NumPy arrays.
* Access and modify data using indexing and slicing.
* Filter data using Boolean masking.
* Understand the difference between views and copies.
* Apply broadcasting techniques.
* Perform vectorized operations.
* Compare NumPy performance with traditional Python loops.
* Solve practical exercises using NumPy.

---

# 📚 Topics Covered

| S.No | Topic                    |
| ---- | ------------------------ |
| 1    | Introduction to NumPy    |
| 2    | Creating NumPy Arrays    |
| 3    | Data Types in NumPy      |
| 4    | Array Creation Functions |
| 5    | Array Attributes         |
| 6    | Indexing                 |
| 7    | Boolean Indexing         |
| 8    | Slicing                  |
| 9    | Views vs Copies          |
| 10   | Broadcasting             |
| 11   | Vectorization            |
| 12   | Performance Comparison   |
| 13   | Practice Exercises       |

---

# 1️⃣ Introduction to NumPy

NumPy stands for **Numerical Python** and provides an efficient way to store and process large amounts of numerical data.

### Why NumPy?

| Python Lists                    | NumPy Arrays                     |
| ------------------------------- | -------------------------------- |
| Slower                          | Faster                           |
| More Memory Usage               | Less Memory Usage                |
| Limited Mathematical Operations | Advanced Mathematical Operations |
| Loop-Based Computations         | Vectorized Computations          |

### Example

```python
import numpy as np

arr = np.array([10, 20, 30, 40])
print(arr)
```

### Output

```python
[10 20 30 40]
```

---

# 2️⃣ Creating NumPy Arrays

NumPy arrays can be created from Python lists.

### One-Dimensional Array

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])

print(arr)
```

### Output

```python
[1 2 3 4 5]
```

---

### Two-Dimensional Array

```python
matrix = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

print(matrix)
```

### Output

```python
[[1 2 3]
 [4 5 6]]
```

---

# 3️⃣ Data Types (dtype)

Each NumPy array has a specific data type.

### Example

```python
arr = np.array([1, 2, 3])

print(arr.dtype)
```

### Output

```python
int64
```

### Common Data Types

| Data Type | Description            |
| --------- | ---------------------- |
| int32     | Integer                |
| int64     | Large Integer          |
| float32   | Decimal Number         |
| float64   | Double Precision Float |
| bool      | Boolean Values         |

---

# 4️⃣ NumPy Array Creation Functions

NumPy provides several built-in functions for generating arrays.

## Zeros Array

```python
np.zeros((2,3))
```

### Output

```python
[[0. 0. 0.]
 [0. 0. 0.]]
```

---

## Ones Array

```python
np.ones((2,3))
```

### Output

```python
[[1. 1. 1.]
 [1. 1. 1.]]
```

---

## arange()

```python
np.arange(0,10,2)
```

### Output

```python
[0 2 4 6 8]
```

---

## linspace()

```python
np.linspace(0,1,5)
```

### Output

```python
[0.   0.25 0.50 0.75 1.00]
```

---

## Identity Matrix

```python
np.eye(3)
```

### Output

```python
[[1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]]
```

---

# 5️⃣ Array Attributes

Array attributes provide useful information about the structure of an array.

```python
arr = np.array([[1,2,3],[4,5,6]])
```

| Attribute | Description          |
| --------- | -------------------- |
| ndim      | Number of dimensions |
| shape     | Shape of array       |
| size      | Total elements       |
| dtype     | Data type            |
| itemsize  | Size of each element |

### Example

```python
print(arr.ndim)
print(arr.shape)
print(arr.size)
```

### Output

```python
2
(2,3)
6
```

---

# 6️⃣ Indexing

Indexing is used to access specific elements.

### Example

```python
arr = np.array([10,20,30,40])

print(arr[2])
```

### Output

```python
30
```

---

### 2D Indexing

```python
matrix = np.array([
    [1,2,3],
    [4,5,6]
])

print(matrix[1,2])
```

### Output

```python
6
```

---

# 7️⃣ Boolean Indexing

Boolean indexing helps filter data based on conditions.

### Example

```python
arr = np.array([10,20,30,40,50])

print(arr[arr > 25])
```

### Output

```python
[30 40 50]
```

### Applications

* Data Cleaning
* Filtering Records
* Removing Outliers
* Feature Selection

---

# 8️⃣ Slicing

Slicing extracts a subset of data.

### Example

```python
arr = np.array([10,20,30,40,50])

print(arr[1:4])
```

### Output

```python
[20 30 40]
```

---

# 9️⃣ Views vs Copies

Understanding memory behavior is crucial in NumPy.

### View

```python
arr = np.array([1,2,3,4])

view = arr.view()

view[0] = 100

print(arr)
```

### Output

```python
[100   2   3   4]
```

Changes in the view affect the original array.

---

### Copy

```python
copy_arr = arr.copy()

copy_arr[0] = 500

print(arr)
```

### Output

```python
[100   2   3   4]
```

Changes in the copy do not affect the original array.

---

# 🔟 Broadcasting

Broadcasting allows operations on arrays of different shapes.

### Example

```python
arr = np.array([1,2,3])

result = arr + 10

print(result)
```

### Output

```python
[11 12 13]
```

### Benefits

* Faster Computation
* Cleaner Code
* Less Memory Usage

---

# 1️⃣1️⃣ Vectorization

Vectorization eliminates explicit loops.

### Example

```python
arr = np.array([1,2,3,4])

print(arr * 2)
```

### Output

```python
[2 4 6 8]
```

---

# 1️⃣2️⃣ Performance Comparison

## Traditional Python Loop

```python
numbers = list(range(100000))

squared = []

for i in numbers:
    squared.append(i*i)
```

---

## NumPy Vectorization

```python
numbers = np.arange(100000)

squared = numbers * numbers
```

### Observation

NumPy performs operations significantly faster because calculations are implemented in optimized C code.

---

# 📝 Practice Exercise 1

### Question

Create a NumPy array containing numbers from 1 to 10.

### Solution

```python
import numpy as np

arr = np.arange(1,11)

print(arr)
```

### Output

```python
[ 1  2  3  4  5  6  7  8  9 10]
```

---

# 📝 Practice Exercise 2

### Question

Find all values greater than 50.

### Solution

```python
arr = np.array([25,60,75,40,90])

print(arr[arr > 50])
```

### Output

```python
[60 75 90]
```

---

# 📝 Practice Exercise 3

### Question

Create a 3×3 identity matrix.

### Solution

```python
print(np.eye(3))
```

### Output

```python
[[1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]]
```

---

# 🎓 Key Learning Outcomes

After completing this training session, I gained practical experience in:

✅ Creating NumPy arrays

✅ Understanding array dimensions and attributes

✅ Working with indexing and slicing

✅ Applying Boolean filtering

✅ Understanding views and copies

✅ Implementing broadcasting

✅ Using vectorized operations

✅ Optimizing performance with NumPy

✅ Solving practical numerical computing problems

---

# 📌 Conclusion

This training session provided a strong foundation in NumPy fundamentals. I learned how NumPy simplifies numerical computation, improves execution speed, and provides powerful tools for data manipulation. The concepts covered during this session are essential for advanced topics in Data Science, Machine Learning, Deep Learning, and Artificial Intelligence.

NumPy serves as the backbone of many Python-based data science libraries and is a crucial skill for anyone pursuing analytics or AI-related fields.

#  NumPy Essentials for AI & Machine Learning And NumPy Operations

## 📅 Training Day: 6

### Topic: NumPy Essentials for AI & Machine Learning

---

# 🎯 Objective

The objective of Day 6 was to understand the fundamentals of **NumPy (Numerical Python)** and learn how it is used for efficient numerical computation, data preprocessing, and machine learning workflows.

NumPy provides a powerful N-dimensional array object and enables fast mathematical operations without using traditional Python loops.

---

# 📚 Topics Covered

| Module | Topic                           |
| ------ | ------------------------------- |
| 1      | Introduction to NumPy Arrays    |
| 2      | Array Creation & Properties     |
| 3      | Vectorization                   |
| 4      | Indexing & Slicing              |
| 5      | Boolean Masking & Data Cleaning |
| 6      | Statistical Operations          |
| 7      | Broadcasting                    |
| 8      | Reshaping & Flattening          |
| 9      | Matrix Multiplication           |
| 10     | Hands-on Exercises              |

---

# 1️⃣ Introduction to NumPy

NumPy stands for **Numerical Python**.

It is used for:

* Fast mathematical computations
* Scientific computing
* Data analysis
* Machine Learning
* Artificial Intelligence

### Why NumPy?

| Python Lists                    | NumPy Arrays                  |
| ------------------------------- | ----------------------------- |
| Slower                          | Faster                        |
| More memory usage               | Less memory usage             |
| Loop required                   | Vectorized operations         |
| Limited mathematical operations | Advanced mathematical support |

### Example

```python
import numpy as np

list1 = [10, 20, 30, 40]
arr1 = np.array(list1)

print(type(arr1))
```

### Output

```python
<class 'numpy.ndarray'>
```

---

# 2️⃣ Creating NumPy Arrays

## 1D Array

```python
import numpy as np

arr_1d = np.array([10, 20, 30, 40])

print(arr_1d)
print(arr_1d.shape)
print(arr_1d.dtype)
print(arr_1d.ndim)
```

### Output

```python
[10 20 30 40]
(4,)
int64
1
```

---

## 2D Array

```python
arr_2d = np.array([
    [1,2,3],
    [4,5,6]
])

print(arr_2d)
```

### Output

```python
[[1 2 3]
 [4 5 6]]
```

---

# Array Attributes

| Attribute | Description                  |
| --------- | ---------------------------- |
| ndim      | Number of dimensions         |
| shape     | Array dimensions             |
| size      | Total elements               |
| dtype     | Data type                    |
| itemsize  | Size of one element in bytes |

---

# 3️⃣ Vectorization

Vectorization allows operations on an entire array without loops.

### Example: Applying Tax

```python
prices = np.array([100, 200, 300, 400])

taxed_prices = prices * 1.10

print(taxed_prices)
```

### Output

```python
[110. 220. 330. 440.]
```

---

## Element-wise Addition

```python
a = np.array([1,2,3])
b = np.array([10,20,30])

print(a + b)
```

### Output

```python
[11 22 33]
```

---

# 4️⃣ Indexing and Slicing

Dataset:

```python
dataset = np.array([
    [25,50,710],
    [47,85,690],
    [31,62,780],
    [19,22,620]
])
```

---

## Access Single Value

```python
print(dataset[1,1])
```

### Output

```python
85
```

---

## Entire Row

```python
print(dataset[0])
```

### Output

```python
[ 25  50 710]
```

---

## Entire Column

```python
print(dataset[:,0])
```

### Output

```python
[25 47 31 19]
```

---

# 5️⃣ Boolean Masking & Data Filtering

Boolean masking is used to filter data based on conditions.

### Example

```python
temp = np.array([20,30,10,25,15,28,3])

cold_days = temp[temp < 20]
hot_days = temp[temp > 25]

print(cold_days)
print(hot_days)
```

### Output

```python
[10 15  3]
[30 28]
```

---

# 6️⃣ Data Cleaning using np.where()

### Example

```python
salaries = np.array([45000, -999, 52000, 61000, -999, 48000])

fixed = np.where(salaries < 0, 10000, salaries)

print(fixed)
```

### Output

```python
[45000 10000 52000 61000 10000 48000]
```

---

# 7️⃣ Statistical Operations

## Mean

```python
x = np.array([10,40,20,30,40])

print(np.mean(x))
```

### Output

```python
28.0
```

---

## Median

```python
print(np.median(x))
```

### Output

```python
30.0
```

---

## Column-wise Mean

```python
X = np.array([
    [10.0, 200.0],
    [30.0, 100.0],
    [20.0, 300.0]
])

print(np.mean(X, axis=0))
```

### Output

```python
[ 20. 200.]
```

---

# 8️⃣ Broadcasting

Broadcasting allows operations on arrays of different shapes.

```python
X = np.array([
    [10.0, 200.0],
    [30.0, 100.0],
    [20.0, 300.0]
])

means = np.mean(X, axis=0)

print(X - means)
```

### Output

```python
[[-10.    0.]
 [ 10. -100.]
 [  0.  100.]]
```

---

# 9️⃣ Reshaping and Flattening

## Reshape

```python
arr = np.arange(6)

matrix = arr.reshape(2,3)

print(matrix)
```

### Output

```python
[[0 1 2]
 [3 4 5]]
```

---

## Flatten

```python
print(matrix.flatten())
```

### Output

```python
[0 1 2 3 4 5]
```

---

# 🔟 Matrix Multiplication (Dot Product)

```python
inputs = np.array([1.0, 2.0])

weights = np.array([
    [0.2, 0.8, -0.5],
    [0.5, -0.1, 0.4]
])

outputs = np.dot(inputs, weights)

print(outputs)
```

### Output

```python
[ 1.2  0.6  0.3]
```

---

# 📝 Assignment Questions with Solutions

---

# Question 1: Celsius to Fahrenheit Conversion

### Problem

Convert the Celsius temperatures into Fahrenheit using NumPy vectorization.

### Solution

```python
import numpy as np

celsius = np.array([0, 10, 25, 36.6, 40])

fahrenheit = (celsius * 9/5) + 32

print(fahrenheit)
```

### Output

```python
[32.   50.   77.   97.88 104. ]
```

---

# Question 2: Feature and Label Split

### Problem

Extract features and labels from student data.

### Solution

```python
student_data = np.array([
    [90,18,25,85],
    [75,14,15,62],
    [95,19,30,92],
    [60,10,8,45]
])

X = student_data[:,0:3]
y = student_data[:,3]

print(X)
print(y)
```

### Output

```python
[[90 18 25]
 [75 14 15]
 [95 19 30]
 [60 10  8]]

[85 62 92 45]
```

---

# Question 3: Filter and Replace Outliers

### Problem

Replace invalid age values (<0 or >120) with 30.

### Solution

```python
age = np.array([25,-1,47,999,18,31,-5,62])

corrected = np.where(
    (age < 0) | (age > 120),
    30,
    age
)

print(corrected)
```

### Output

```python
[25 30 47 30 18 31 30 62]
```

---

# Question 4: Feature Normalization

### Problem

Normalize features using mean and standard deviation.

### Solution

```python
X = np.array([
    [10.0,100.0],
    [20.0,150.0],
    [30.0,200.0]
])

mean = np.mean(X, axis=0)
std = np.std(X, axis=0)

normalized = (X - mean) / std

print(normalized)
```

### Output

```python
[[-1.22474487 -1.22474487]
 [ 0.          0.        ]
 [ 1.22474487  1.22474487]]
```

---

# 🎓 Key Learning Outcomes

After completing Day 6, I learned:

✅ Creating NumPy arrays

✅ Understanding array dimensions and attributes

✅ Vectorized computations

✅ Data filtering using Boolean masking

✅ Cleaning datasets using `np.where()`

✅ Statistical analysis with NumPy

✅ Broadcasting concepts

✅ Reshaping and flattening arrays

✅ Matrix multiplication using `np.dot()`

✅ Feature normalization for Machine Learning

---

# 📌 Conclusion

Day 6 introduced the core NumPy operations required in Data Science, Artificial Intelligence, and Machine Learning. The concepts of vectorization, slicing, filtering, broadcasting, and normalization are fundamental for efficient data preprocessing and model development. These skills form the foundation for working with large datasets and implementing machine learning pipelines efficiently.

---

### 🚀 Tools Used

* Python
* NumPy
* Jupyter Notebook

### 📂 Repository Structure

```text
Day-6-NumPy-Essentials/
│
├── README.md
├── day6_numpy_operations.ipynb
└── screenshots/
```

⭐ This training day strengthened my understanding of NumPy and prepared me for advanced data analysis and machine learning workflows.
