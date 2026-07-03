# 🚀 Day 1 - Python Variables & Data Types

> Industrial Training in AI & Machine Learning
>
> 📅 Day 1 Learning Report
>
> 🎯 Topic: Variables, Memory Management, Data Types, Mutability, Collections & Type Casting

---

# 📚 Learning Objectives

By the end of Day 1, I learned:

✅ What variables are in Python

✅ How Python stores objects in memory

✅ Difference between references and values

✅ Dynamic Typing

✅ Core Built-in Data Types

✅ Mutable vs Immutable Objects

✅ Python Collections

✅ Type Casting & Type Conversion

✅ Variable Naming Rules

✅ Basic Problem Solving using Python

---

# 🧠 Understanding Variables in Python

Unlike languages such as C or Java, Python variables do not directly store values.

A variable acts as a **reference (nametag)** pointing to an object in memory.

### Example

```python
x = 42
```

### What happens internally?

```text
Variable x
     │
     ▼
+---------+
|   42    |
+---------+
```

Python:

1. Creates object `42`
2. Creates variable `x`
3. Binds `x` to object `42`

---

# 🔍 Memory Address Inspection

Python provides the `id()` function to view an object's memory identity.

```python
x = 43

print(id(x))
```

Output:

```text
140732487654
```

Each object has a unique identity in memory.

---

# 🔗 Sharing References

When assigning one variable to another:

```python
x = 42
y = x
```

Both variables point to the same object.

```text
x ─────┐
       ▼
     [42]
       ▲
y ─────┘
```

Verification:

```python
print(x is y)
```

Output:

```python
True
```

---

# ⚡ Dynamic Typing

Python is dynamically typed.

A variable can point to different object types during execution.

```python
my_var = 100

print(type(my_var))

my_var = "Hello"

print(type(my_var))
```

Output:

```text
<class 'int'>
<class 'str'>
```

---

# 🔢 Numeric Data Types

## Integer (int)

```python
age = 20
```

Stores whole numbers.

---

## Float (float)

```python
pi = 3.14159
```

Stores decimal numbers.

---

## Complex (complex)

```python
z = 2 + 3j
```

Used in scientific and mathematical calculations.

```python
print(z.real)
print(z.imag)
```

---

# 📝 String Data Type

Strings store text.

```python
name = "Python"
```

### Multi-line Strings

```python
message = """
Welcome to
Industrial Training
"""
```

---

# ✅ Boolean Data Type

Represents logical values.

```python
is_raining = False
has_passed = True
```

Output:

```text
True
False
```

---

# 🚫 None Type

Represents absence of value.

```python
data = None
```

Type:

```python
print(type(data))
```

Output:

```text
<class 'NoneType'>
```

---

# 🔒 Immutable Objects

Immutable objects cannot be modified after creation.

Examples:

- int
- float
- str
- tuple
- bool

Example:

```python
a = 5
```

After:

```python
a = a + 1
```

Python creates a completely new object.

```text
5  →  New Object →  6
```

---

# 🔓 Mutable Objects

Mutable objects can be changed without creating a new object.

Examples:

- list
- dict
- set

Example:

```python
my_list = [1,2,3]

my_list.append(4)
```

Before:

```text
[1,2,3]
```

After:

```text
[1,2,3,4]
```

Memory identity remains unchanged.

---

# ⚠️ Mutable Reference Problem

```python
list_a = [10,20,30]

list_b = list_a
```

Both variables reference the same object.

```python
list_b.append(40)
```

Result:

```python
print(list_a)
```

Output:

```text
[10,20,30,40]
```

Even though only `list_b` was modified.

---

# 🛡️ Avoiding Mutable Reference Bugs

Create a copy instead.

```python
list_a = [10,20,30]

list_c = list_a.copy()

list_c.append(40)
```

Now:

```python
list_a
```

Output:

```text
[10,20,30]
```

---

# 📦 Python Collections

## 1️⃣ List

```python
fruits = ["apple","banana","cherry"]
```

✔ Ordered

✔ Mutable

✔ Duplicates Allowed

---

## 2️⃣ Tuple

```python
fruits = ("apple","banana","cherry")
```

✔ Ordered

✔ Immutable

✔ Duplicates Allowed

---

## 3️⃣ Dictionary

```python
student = {
    "name":"Alice",
    "age":25
}
```

✔ Key-Value Pair

✔ Mutable

✔ Fast Lookup

---

## 4️⃣ Set

```python
items = {"apple","banana","apple"}
```

Output:

```text
{'apple','banana'}
```

✔ Unique Values Only

✔ Mutable

✔ No Duplicates

---

# 🔄 Type Casting

Converting one datatype into another.

---

## Implicit Conversion

```python
10 + 5.5
```

Output:

```text
15.5
```

Python automatically converts integer to float.

---

## Explicit Conversion

```python
num = "123"

value = int(num)
```

Output:

```text
123
```

Type:

```python
<class 'int'>
```

---

# 🎯 Removing Duplicates Using Set

```python
numbers = [1,2,2,3,4,4,5]

unique = set(numbers)
```

Output:

```text
{1,2,3,4,5}
```

---

# 🏷️ Variable Naming Rules

## Valid

```python
student_name
age
_marks
```

## Invalid

```python
2age
student-name
class
```

---


# 📝 Assignment

## 📌 Problem Statement

Write a Python program that takes a student's name and marks as input and prints a formatted result card showing **Pass/Fail** status.

---

## 💻 Solution

```python
name = input("Enter Student Name: ")
marks = float(input("Enter Marks Obtained: "))

if marks >= 33:
    status = "Pass"
else:
    status = "Fail"

print("\n" + "=" * 30)
print("         RESULT CARD")
print("=" * 30)
print(f"Student Name : {name}")
print(f"Marks        : {marks} / 100")
print(f"Status       : {status}")
print("=" * 30)
```

### 📤 Sample Output

```text
Enter Student Name: Jaspriya
Enter Marks Obtained: 85

==============================
         RESULT CARD
==============================
Student Name : Jaspriya
Marks        : 85.0 / 100
Status       : Pass
==============================
```

### 🎓 Learning Outcome

- Taking user input
- Conditional statements (`if-else`)
- String formatting using f-strings
- Building a real-world mini project

---

# 🧪 Exercise 1: Identity vs Equality

## 📌 Question

```python
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print(a is b)
print(a == c)
print(a is c)
```

### 🔮 Prediction

| Expression | Expected Output |
|------------|----------------|
| `a is b` | True |
| `a == c` | True |
| `a is c` | False |

---

## 💻 Solution

```python
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print("a is b:", a is b)
print("a == c:", a == c)
print("a is c:", a is c)
```

### 📤 Output

```text
a is b: True
a == c: True
a is c: False
```

### 🎓 Learning Outcome

- `is` checks whether two variables point to the same object.
- `==` checks whether two objects contain the same value.

---

# 🧪 Exercise 2: The Immutability Trap

## 📌 Question

Try modifying a tuple:

```python
fruits = ("apple", "pear", "cherry")
fruits[1] = "banana"
```

### ⚠️ Problem

```text
TypeError: 'tuple' object does not support item assignment
```

---

## 💻 Solution

```python
fruits = ("apple", "pear", "cherry")

fruits_list = list(fruits)
fruits_list[1] = "banana"

fruits = tuple(fruits_list)

print("Modified tuple:", fruits)
```

### 📤 Output

```text
Modified tuple: ('apple', 'banana', 'cherry')
```

### 🎓 Learning Outcome

- Tuples are immutable.
- Convert tuple → list → modify → convert back to tuple.

---

# 🧪 Exercise 3: AI Hyperparameters Dictionary

## 📌 Question

Create a dictionary containing:

| Parameter | Value |
|------------|--------|
| Learning Rate | 0.001 |
| Batch Size | 32 |
| Optimizer | Adam |
| Epochs | 10 |
| Early Stopping | True |

Then update the learning rate to **0.005**.

---

## 💻 Solution

```python
hyperparameters = {
    "learning_rate": 0.001,
    "batch_size": 32,
    "optimizer": "Adam",
    "epochs": 10,
    "early_stopping": True
}

print("LR:", hyperparameters["learning_rate"])
print("Batch Size:", hyperparameters["batch_size"])
print("Optimizer:", hyperparameters["optimizer"])
print("Epochs:", hyperparameters["epochs"])
print("Early stopping:", hyperparameters["early_stopping"])

hyperparameters["learning_rate"] = 0.005

print("\nUpdated dictionary:", hyperparameters)
```

### 📤 Output

```text
LR: 0.001
Batch Size: 32
Optimizer: Adam
Epochs: 10
Early stopping: True

Updated dictionary:
{
 'learning_rate': 0.005,
 'batch_size': 32,
 'optimizer': 'Adam',
 'epochs': 10,
 'early_stopping': True
}
```

### 🎓 Learning Outcome

- Dictionaries store information using key-value pairs.
- Dictionaries are mutable and can be updated easily.

---

# 🧪 Exercise 4: Explicit Cast & Set Magic

## 📌 Question

Given:

```python
roles = ["admin", "user", "user", "editor", "admin", "user", "viewer"]
```

Find:

1. Total user accounts
2. Unique roles
3. Count of unique roles

---

## 💻 Solution

```python
roles = ["admin", "user", "user", "editor", "admin", "user", "viewer"]

print("Total user accounts:", len(roles))

unique_roles = set(roles)

print("Unique roles in the system:", unique_roles)

print("Count of unique roles:", len(unique_roles))
```

### 📤 Output

```text
Total user accounts: 7

Unique roles in the system:
{'admin', 'editor', 'user', 'viewer'}

Count of unique roles: 4
```

### 🎓 Learning Outcome

- Sets automatically remove duplicate values.
- Useful for finding unique elements in a collection.

---


# 📈 Key Takeaways

✔ Variables are references to objects

✔ Python is dynamically typed

✔ Objects have identities in memory

✔ Mutable and Immutable objects behave differently

✔ Lists, Tuples, Dictionaries and Sets are fundamental collections

✔ Type casting is essential for data processing

✔ Understanding memory references prevents common bugs

---

# 🎓 Day 1 Summary

Today I built a strong foundation in Python programming by understanding variables, memory references, data types, collections, mutability, and type conversion. These concepts form the backbone of Data Science, Artificial Intelligence, Machine Learning, and Software Development.


