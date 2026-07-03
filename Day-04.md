# 🚀 Day 4 Training Report

## Python Data Structures: Lists, Tuples, Dictionaries & Sets

### 📅 Training Day: 4

### 🎯 Objective

The objective of Day 4 was to understand and implement Python's fundamental data structures:

* Lists
* Tuples
* Dictionaries
* Sets

These data structures are essential for efficient data storage, manipulation, and preprocessing, especially in Data Science, Machine Learning, and Artificial Intelligence applications.

---

# 📚 Topics Covered

| Topic              | Description                             |
| ------------------ | --------------------------------------- |
| Lists              | Ordered and mutable collection of items |
| Tuples             | Ordered and immutable collection        |
| Dictionaries       | Key-value pair data storage             |
| Sets               | Unordered collection of unique elements |
| List Comprehension | Efficient filtering and transformation  |
| Tuple Unpacking    | Extracting values from tuples           |
| Dictionary Methods | Accessing and managing key-value pairs  |
| Set Operations     | Union, Intersection, Difference         |

---

# 1️⃣ Lists

## What is a List?

A List is an ordered and mutable collection that allows duplicate values.

### Example

```python
list1 = [10, 20, 30, 40]

print(list1)
```

### Output

```python
[10, 20, 30, 40]
```

---

## Common List Operations

| Operation      | Example     |
| -------------- | ----------- |
| Add Element    | `append()`  |
| Remove Element | `remove()`  |
| Sort           | `sort()`    |
| Reverse        | `reverse()` |
| Length         | `len()`     |
| Maximum Value  | `max()`     |
| Minimum Value  | `min()`     |

---

# 2️⃣ Tuples

## What is a Tuple?

A Tuple is an ordered but immutable collection.

### Example

```python
tuple1 = (10, 20, 30)

print(tuple1)
```

### Output

```python
(10, 20, 30)
```

---

## Tuple Features

| Feature           | Description |
| ----------------- | ----------- |
| Ordered           | Yes         |
| Mutable           | No          |
| Duplicate Values  | Allowed     |
| Faster than Lists | Yes         |

---

# 3️⃣ Dictionaries

## What is a Dictionary?

A Dictionary stores data as key-value pairs.

### Example

```python
student = {
    "name": "Simran",
    "age": 21,
    "course": "Python"
}

print(student)
```

### Output

```python
{'name': 'Simran', 'age': 21, 'course': 'Python'}
```

---

## Dictionary Operations

| Operation    | Example                 |
| ------------ | ----------------------- |
| Access Value | `dict[key]`             |
| Add Key      | `dict[new_key] = value` |
| Remove Key   | `pop()`                 |
| Get Keys     | `keys()`                |
| Get Values   | `values()`              |
| Iterate      | `items()`               |

---

# 4️⃣ Sets

## What is a Set?

A Set is an unordered collection of unique values.

### Example

```python
set1 = {10, 20, 30, 10, 20}

print(set1)
```

### Output

```python
{10, 20, 30}
```

---

## Set Features

| Feature          | Description |
| ---------------- | ----------- |
| Unique Elements  | Yes         |
| Ordered          | No          |
| Mutable          | Yes         |
| Duplicate Values | Not Allowed |

---

# 📝 Assignment Questions with Solutions & Outputs

---

# Exercise 1: Outlier / Noise Filter (Lists)

## Question

Given:

```python
predictions = [0.15, -99.0, 0.82, 1.45, -99.0, 0.67, 2.1]
```

Write a program to:

1. Remove all occurrences of `-99.0`
2. Keep only positive values
3. Print the cleaned list

---

## Solution

```python
predictions = [0.15, -99.0, 0.82, 1.45, -99.0, 0.67, 2.1]

cleaned_predictions = [
    x for x in predictions
    if x != -99.0 and x > 0
]

print("Cleaned Predictions:", cleaned_predictions)
```

## Output

```python
Cleaned Predictions: [0.15, 0.82, 1.45, 0.67, 2.1]
```

---

# Exercise 2: Dataset Split Unpacker (Tuples)

## Question

Create a function that unpacks:

```python
((X_train, y_train),
 (X_val, y_val),
 (X_test, y_test))
```

and prints the size of each dataset.

---

## Solution

```python
def unpack_splits(split_tuple):
    train_split, val_split, test_split = split_tuple

    X_train, y_train = train_split
    X_val, y_val = val_split
    X_test, y_test = test_split

    print("Train Size:", len(X_train))
    print("Validation Size:", len(X_val))
    print("Test Size:", len(X_test))


dataset_splits = (
    ([1,2,3,4], [0,1,0,1]),
    ([5,6], [1,0]),
    ([7,8,9], [0,1,1])
)

unpack_splits(dataset_splits)
```

## Output

```python
Train Size: 4
Validation Size: 2
Test Size: 3
```

---

# Exercise 3: Safe Vocabulary Word Indexer (Dictionaries)

## Question

Convert words into numerical indices using a vocabulary dictionary.

Unknown words should receive index `0`.

---

## Solution

```python
def text_to_indices(text, vocab_dict):
    words = text.lower().split()

    indices = [
        vocab_dict.get(word, 0)
        for word in words
    ]

    return indices


vocab = {
    "hello": 1,
    "world": 2,
    "python": 3,
    "ai": 4
}

text = "Hello Python developers learning AI in this world"

result = text_to_indices(text, vocab)

print(result)
```

## Output

```python
[1, 3, 0, 0, 4, 0, 0, 2]
```

---

# Exercise 4: Clean & Overlap Checker (Sets)

## Question

Find labels present in the test set but absent in the training set.

---

## Solution

```python
train_labels = [
    "tumor",
    "healthy",
    "healthy",
    "tumor",
    "cyst",
    "tumor"
]

test_labels = [
    "tumor",
    "healthy",
    "fibroid",
    "tumor"
]

train_set = set(train_labels)
test_set = set(test_labels)

unseen_classes = test_set - train_set

print("Train Classes:", train_set)
print("Test Classes:", test_set)
print("Unseen Classes:", unseen_classes)
```

## Output

```python
Train Classes: {'tumor', 'healthy', 'cyst'}

Test Classes: {'tumor', 'healthy', 'fibroid'}

Unseen Classes: {'fibroid'}
```

---

# Exercise 5: Confusion Matrix Evaluation

## Question

Calculate:

* TP
* TN
* FP
* FN
* Accuracy

using actual and predicted labels.

---

## Solution

```python
actual_labels = [1,0,1,1,0,1,0,0,1,0]
predicted_labels = [1,0,0,1,0,1,1,0,1,1]

tp = tn = fp = fn = 0

for act, pred in zip(actual_labels, predicted_labels):

    if act == 1 and pred == 1:
        tp += 1

    elif act == 0 and pred == 0:
        tn += 1

    elif act == 0 and pred == 1:
        fp += 1

    elif act == 1 and pred == 0:
        fn += 1

metrics = {
    "TP": tp,
    "TN": tn,
    "FP": fp,
    "FN": fn
}

accuracy = (tp + tn) / (tp + tn + fp + fn)

print(metrics)
print("Accuracy:", accuracy)
```

## Output

```python
{'TP': 4, 'TN': 3, 'FP': 2, 'FN': 1}

Accuracy: 0.7
```

### Confusion Matrix Summary

| Metric   | Value |
| -------- | ----- |
| TP       | 4     |
| TN       | 3     |
| FP       | 2     |
| FN       | 1     |
| Accuracy | 70%   |

---

# Exercise 6: Customer Dataset Preprocessing Pipeline

## Question

Perform:

1. Duplicate removal
2. Negative salary removal
3. Count valid records
4. Calculate average age of subscribers

---

## Solution

```python
raw_records = [
    (25, 50000, 1),
    (47, 85000, 0),
    (25, 50000, 1),
    (31, -1000, 1),
    (40, 60000, 1),
    (47, 85000, 0),
    (35, 75000, 0),
    (22, 12000, 1)
]

unique_records = list(set(raw_records))

cleaned_records = [
    rec
    for rec in unique_records
    if rec[1] >= 0
]

count = len(cleaned_records)

ages = [
    rec[0]
    for rec in cleaned_records
    if rec[2] == 1
]

average_age = sum(ages) / len(ages)

print("Cleaned Records:", cleaned_records)
print("Count:", count)
print("Average Age:", average_age)
```

## Output

```python
Cleaned Records:
[(25, 50000, 1),
 (47, 85000, 0),
 (40, 60000, 1),
 (35, 75000, 0),
 (22, 12000, 1)]

Count: 5

Average Age: 29.0
```

---

# 🎯 Key Learnings

✅ Learned List operations and comprehensions

✅ Understood Tuple creation and unpacking

✅ Implemented Dictionary-based lookups

✅ Performed Set operations for uniqueness

✅ Applied Data Structures in ML preprocessing

✅ Built mini real-world data cleaning pipelines

✅ Calculated evaluation metrics for machine learning models

---

# 📌 Conclusion

Day 4 focused on mastering Python Data Structures and their practical applications in data preprocessing, machine learning workflows, and efficient programming. Through multiple exercises and real-world examples, we learned how Lists, Tuples, Dictionaries, and Sets can be used to organize, clean, analyze, and process data effectively.

**Day 4 Successfully Completed ✅**
