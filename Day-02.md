# 🚀 Day 2 Training Report: Python Foundations – Operators, Loops & Control Flow

## 📅 Training Details

| Field                | Information                                                                              |
| -------------------- | ---------------------------------------------------------------------------------------- |
| **Training Program** | Industrial Training in AI & Machine Learning                                             |
| **Day**              | Day 2                                                                                    |
| **Topic**            | Python Foundations: Operators, Loops & Control Flow                                      |
| **Language Used**    | Python                                                                                   |
| **Objective**        | Understand operators, decision-making, loops, and practical problem-solving using Python |

---

## 📚 Table of Contents

* [Overview](#-overview)
* [Day 1 Quick Recap](#-day-1-quick-recap)
* [Python Operators](#️-python-operators)

  * [Arithmetic Operators](#1️⃣-arithmetic-operators)
  * [Comparison Operators](#2️⃣-comparison-operators)
  * [Logical Operators](#3️⃣-logical-operators)
  * [Assignment Operators](#4️⃣-assignment-operators)
  * [Bitwise Operators](#5️⃣-bitwise-operators)
  * [Membership Operators](#6️⃣-membership-operators)
  * [Identity Operators](#7️⃣-identity-operators)
* [Problem Solving Using Operators](#-problem-solving-using-operators)
* [Python Loops](#-python-loops)

  * [For Loop](#-for-loop)
  * [While Loop](#-while-loop)
  * [Loop Control Statements](#-loop-control-statements)
* [Loop Else](#-loop-else)
* [Key Learning Outcomes](#-key-learning-outcomes)
* [Conclusion](#-conclusion)

---

# 📖 Overview

Day 2 focused on strengthening Python fundamentals by exploring various types of operators, conditional statements, loops, and practical implementations. The session combined theoretical concepts with hands-on coding exercises to develop logical thinking and problem-solving skills.

---

# 🔄 Day 1 Quick Recap

Before starting new concepts, we revised the fundamentals covered on Day 1.

## Topics Covered

* Variables and References
* Data Types
* Type Casting
* Mutable vs Immutable Objects
* Naming Conventions
* Memory References (`id()`)
* Object Identity (`is`)

### Example: Mutable Objects

```python
list_a = [1, 2, 3]
list_b = list_a

list_b.append(4)

print(list_a)
```

### Output

```python
[1, 2, 3, 4]
```

This demonstrates that both variables point to the same object in memory.

---

# ⚙️ Python Operators

Operators are symbols used to perform operations on variables and values.

## 1️⃣ Arithmetic Operators

Used for mathematical calculations.

| Operator | Description    | Example  |
| -------- | -------------- | -------- |
| `+`      | Addition       | `a + b`  |
| `-`      | Subtraction    | `a - b`  |
| `*`      | Multiplication | `a * b`  |
| `/`      | Division       | `a / b`  |
| `%`      | Modulus        | `a % b`  |
| `//`     | Floor Division | `a // b` |
| `**`     | Exponentiation | `a ** b` |

### Example

```python
a = 15
b = 4

print(a + b)
print(a / b)
print(a // b)
print(a % b)
print(a ** b)
```

---

## 2️⃣ Comparison Operators

Used to compare values and return Boolean results.

| Operator | Meaning                  |
| -------- | ------------------------ |
| `==`     | Equal To                 |
| `!=`     | Not Equal To             |
| `>`      | Greater Than             |
| `<`      | Less Than                |
| `>=`     | Greater Than or Equal To |
| `<=`     | Less Than or Equal To    |

### Example

```python
x = 10
y = 20

print(x == y)
print(x != y)
print(x < y)
```

---

## 3️⃣ Logical Operators

Logical operators combine multiple conditions.

| Operator | Purpose                             |
| -------- | ----------------------------------- |
| `and`    | Both conditions must be True        |
| `or`     | At least one condition must be True |
| `not`    | Reverses Boolean value              |

### Example

```python
is_sunny = True
is_weekend = False

print(is_sunny and is_weekend)
print(is_sunny or is_weekend)
print(not is_sunny)
```

---

## 4️⃣ Assignment Operators

Used to assign and update values.

| Operator | Example   |
| -------- | --------- |
| `=`      | `x = 5`   |
| `+=`     | `x += 2`  |
| `-=`     | `x -= 2`  |
| `*=`     | `x *= 2`  |
| `/=`     | `x /= 2`  |
| `//=`    | `x //= 2` |
| `%=`     | `x %= 2`  |

### Example

```python
num = 10

num += 5
num *= 2

print(num)
```

---

## 5️⃣ Bitwise Operators

Operate directly on binary values.

| Operator | Description |    |
| -------- | ----------- | -- |
| `&`      | AND         |    |
| `        | `           | OR |
| `^`      | XOR         |    |
| `~`      | NOT         |    |
| `<<`     | Left Shift  |    |
| `>>`     | Right Shift |    |

### Example

```python
n1 = 5
n2 = 3

print(n1 & n2)
print(n1 | n2)
print(n1 ^ n2)
```

---

## 6️⃣ Membership Operators

Used to check whether an element exists in a collection.

| Operator | Description            |
| -------- | ---------------------- |
| `in`     | Element exists         |
| `not in` | Element does not exist |

### Example

```python
fruits = ["apple", "banana", "cherry"]

print("apple" in fruits)
print("kiwi" not in fruits)
```

---

## 7️⃣ Identity Operators

Used to compare memory locations.

| Operator | Description       |
| -------- | ----------------- |
| `is`     | Same object       |
| `is not` | Different objects |

### Example

```python
list_x = [1, 2, 3]
list_y = [1, 2, 3]

print(list_x == list_y)
print(list_x is list_y)
```

---

# 🧠 Problem Solving Using Operators

## Even or Odd Number Checker

```python
number = int(input("Enter a number: "))

if number % 2 == 0:
    print("Even")
else:
    print("Odd")
```

## Percentage Calculator

```python
e = int(input("English: "))
h = int(input("Hindi: "))
m = int(input("Maths: "))
s = int(input("Science: "))
sst = int(input("SST: "))

total = e + h + m + s + sst
percentage = (total / 500) * 100

print(percentage)
```

## Greatest Among Three Numbers

```python
if a > b and a > c:
    print("A is greatest")
elif b > a and b > c:
    print("B is greatest")
else:
    print("C is greatest")
```

---

# 🔁 Python Loops

Loops help execute a block of code repeatedly.

Python provides:

1. `for` Loop
2. `while` Loop

---

## 🔹 For Loop

Used when the number of iterations is known.

### Example

```python
for i in range(0, 11):
    print(i)
```

### Multiplication Table

```python
n = int(input("Enter a number"))

for i in range(11):
    print(f"{n} x {i} = {n * i}")
```

### Iterating Through Lists

```python
languages = ["Python", "SQL", "C++"]

for lang in languages:
    print(lang)
```

### Password Strength Checker

```python
passwords = ["abc123", "abc", "abcdfe", "12"]

for p in passwords:
    if len(p) >= 6:
        print("Strong Password")
    else:
        print("Weak Password")
```

---

## 🔄 While Loop

A `while` loop runs until its condition becomes False.

```python
count = 1

while count <= 3:
    print(count)
    count += 1
```

---

# 🎯 Loop Control Statements

## Break

```python
for num in range(1, 10):
    if num == 5:
        break
```

## Continue

```python
for num in range(1, 10):
    if num == 5:
        continue
```

## Pass

```python
if num == 3:
    pass
```

---

# 🔍 Loop Else

The `else` block executes only when the loop completes normally.

```python
for fruit in fruits:
    if fruit == target:
        break
else:
    print("Target not found")
```

# 📋 Exercises Performed

---

## Exercise 1: Check Whether a Number is Positive and Even

### Question

Write a Python program to check whether a given number is both positive and even.

### Solution

```python
num = 12

if num > 0 and num % 2 == 0:
    print("The number is positive and even.")
else:
    print("The number is not positive and even.")
```

### Output

```text
The number is positive and even.
```

---

## Exercise 2: Find the Largest of Three Numbers

### Question

Write a Python program to find the largest among three numbers.

### Solution

```python
a = 25
b = 40
c = 15

if a >= b and a >= c:
    print("Largest number:", a)
elif b >= a and b >= c:
    print("Largest number:", b)
else:
    print("Largest number:", c)
```

### Output

```text
Largest number: 40
```

---

## Exercise 3: Print Numbers from 1 to 10 Using a For Loop

### Question

Write a Python program to print numbers from 1 to 10 using a for loop.

### Solution

```python
for i in range(1, 11):
    print(i)
```

### Output

```text
1
2
3
4
5
6
7
8
9
10
```

---

## Exercise 4: Print the Multiplication Table of 5

### Question

Write a Python program to print the multiplication table of 5.

### Solution

```python
for i in range(1, 11):
    print(f"5 x {i} = {5*i}")
```

### Output

```text
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
5 x 4 = 20
5 x 5 = 25
5 x 6 = 30
5 x 7 = 35
5 x 8 = 40
5 x 9 = 45
5 x 10 = 50
```

---

## Exercise 5: Calculate the Sum of First 10 Natural Numbers

### Question

Write a Python program to calculate the sum of the first 10 natural numbers.

### Solution

```python
total = 0

for i in range(1, 11):
    total += i

print("Sum =", total)
```

### Output

```text
Sum = 55
```

---

## Exercise 6: Print Even Numbers from 1 to 20

### Question

Write a Python program to print all even numbers between 1 and 20.

### Solution

```python
for i in range(1, 21):
    if i % 2 == 0:
        print(i)
```

### Output

```text
2
4
6
8
10
12
14
16
18
20
```

---

## Exercise 7: Password Validation Using Break Statement

### Question

Given a list of passwords, stop the search when a valid password (length ≥ 6) is found.

### Solution

```python
passwords = ["abc", "123", "python123", "welcome"]

for password in passwords:
    if len(password) >= 6:
        print("Valid Password Found:", password)
        break
```

### Output

```text
Valid Password Found: python123
```

---

## Exercise 8: Age Category Checker

### Question

Write a Python program that categorizes a person based on age.

### Solution

```python
age = 25

if age < 13:
    print("Child")
elif age <= 19:
    print("Teenager")
elif age <= 59:
    print("Adult")
else:
    print("Senior Citizen")
```

### Output

```text
Adult
```

---

## Exercise 9: Number Printing Using While Loop

### Question

Write a Python program that prints numbers from 1 to 5 using a while loop.

### Solution

```python
count = 1

while count <= 5:
    print(count)
    count += 1
```

### Output

```text
1
2
3
4
5
```

---

## Exercise 10: ATM System Simulator

### Question

Create a simple ATM system that allows users to:

* Check Balance
* Deposit Money
* Withdraw Money
* Exit

### Solution

```python
balance = 1000

while True:
    print("\n1. Check Balance")
    print("2. Deposit")
    print("3. Withdraw")
    print("4. Exit")

    choice = int(input("Enter choice: "))

    if choice == 1:
        print("Balance:", balance)

    elif choice == 2:
        amount = int(input("Enter deposit amount: "))
        balance += amount
        print("Updated Balance:", balance)

    elif choice == 3:
        amount = int(input("Enter withdrawal amount: "))
        if amount <= balance:
            balance -= amount
            print("Updated Balance:", balance)
        else:
            print("Insufficient Balance")

    elif choice == 4:
        print("Thank You for Using ATM")
        break

    else:
        print("Invalid Choice")
```

### Sample Output

```text
1. Check Balance
2. Deposit
3. Withdraw
4. Exit

Enter choice: 1
Balance: 1000

Enter choice: 2
Enter deposit amount: 500
Updated Balance: 1500

Enter choice: 4
Thank You for Using ATM
```

---




# 🎯 Key Learning Outcomes

By the end of Day 2, I was able to:

* ✅ Use all major Python operators effectively
* ✅ Perform logical and mathematical operations
* ✅ Implement decision-making using `if`, `elif`, and `else`
* ✅ Create programs using `for` and `while` loops
* ✅ Control loop execution using `break`, `continue`, and `pass`
* ✅ Strengthen problem-solving and programming logic
* ✅ Develop a deeper understanding of Python control flow mechanisms

---

# 📌 Conclusion

Day 2 significantly improved my understanding of Python programming fundamentals. Through extensive hands-on practice with operators, loops, and control flow statements, I learned how to create interactive and logic-based applications. These concepts form the foundation for more advanced topics in Artificial Intelligence, Machine Learning, Data Science, and Software Development.

---

⭐ **Day 2 Training Completed Successfully**

