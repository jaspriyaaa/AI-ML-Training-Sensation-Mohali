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

# 🧪 Practical Exercise 1

### Student Result Card

```python
name = input("Enter Student Name: ")
marks = float(input("Enter Marks: "))
```

Check:

```python
if marks >= 33:
    status = "Pass"
else:
    status = "Fail"
```

Output:

```text
====================
RESULT CARD
====================
Name : John
Marks: 85
Status: Pass
```

---

# 🧪 Practical Exercise 2

Identity vs Equality

```python
a = [1,2,3]
b = a
c = [1,2,3]
```

```python
a is b
```

Output:

```text
True
```

```python
a == c
```

Output:

```text
True
```

```python
a is c
```

Output:

```text
False
```

---

# 🧪 Practical Exercise 3

Tuple Modification

Since tuples are immutable:

```python
fruits = ("apple","pear","cherry")
```

Convert:

```python
fruits = list(fruits)
```

Modify:

```python
fruits[1] = "banana"
```

Convert back:

```python
fruits = tuple(fruits)
```

---

# 🧪 Practical Exercise 4

AI Hyperparameters Dictionary

```python
hyperparameters = {
    "learning_rate":0.001,
    "batch_size":32,
    "optimizer":"Adam",
    "epochs":10
}
```

Updated Learning Rate:

```python
hyperparameters["learning_rate"] = 0.005
```

---

# 🧪 Practical Exercise 5

Unique User Roles

```python
roles = [
"admin",
"user",
"user",
"editor",
"admin"
]
```

Using:

```python
set(roles)
```

Output:

```text
{'admin','editor','user'}
```

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

⭐ Looking forward to Day 2!
