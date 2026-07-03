# 🚀 Day 3 Training Report – Functions & Modular Programming in Python

## 📅 Day 3 Overview

On Day 3 of the Industrial Training Program, we explored one of the most important concepts in Python programming: **Functions**. Functions help us organize code, improve reusability, reduce repetition, and make programs easier to maintain.

We also learned about different types of arguments, variable scope, recursion, and practical implementations of functions commonly used in AI/ML projects.

---

# 📚 Topics Covered

| S.No. | Topic                                           |
| ----- | ----------------------------------------------- |
| 1     | Built-in Functions                              |
| 2     | Creating Custom Functions                       |
| 3     | Parameters and Arguments                        |
| 4     | Return Statement                                |
| 5     | Prime Number Function                           |
| 6     | Types of Arguments                              |
| 7     | Variable-Length Arguments (`*args`, `**kwargs`) |
| 8     | Variable Scope (Local & Global)                 |
| 9     | Global Keyword                                  |
| 10    | Recursive Functions                             |
| 11    | Factorial using Recursion                       |
| 12    | Fibonacci Sequence using Recursion              |

---

# 1️⃣ Built-in Functions in Python

Python provides several predefined functions that are available without importing any module. These functions simplify common operations and improve productivity.

## Common Built-in Functions

| Function  | Purpose                                     |
| --------- | ------------------------------------------- |
| `len()`   | Returns the length of an object             |
| `min()`   | Returns the smallest value                  |
| `max()`   | Returns the largest value                   |
| `sum()`   | Calculates the sum of values                |
| `abs()`   | Returns absolute value                      |
| `round()` | Rounds a number to specified decimal places |
| `print()` | Displays output                             |
| `type()`  | Returns data type                           |

### Example

```python
list1 = [10, 20, 30, 40, 50]

print(len(list1))
print(min(list1))
print(sum(list1))
```

### AI/ML Relevance

Built-in functions are frequently used for:

* Dataset inspection
* Statistical calculations
* Data preprocessing
* Performance metric analysis

---

# 2️⃣ Creating Custom Functions

A function is a reusable block of code that performs a specific task.

## Syntax

```python
def function_name():
    # code
```

### Example

```python
def welcome_student():
    print("Welcome to AI/ML Industrial Training!")
    print("Let's build some functions today!")

welcome_student()
```

### Benefits of Functions

✅ Code Reusability

✅ Better Readability

✅ Easier Debugging

✅ Reduced Code Duplication

---

# 3️⃣ Parameters and Arguments

Functions become more powerful when data can be passed into them.

## Key Terms

| Term      | Meaning                                  |
| --------- | ---------------------------------------- |
| Parameter | Variable defined in function definition  |
| Argument  | Actual value passed during function call |

### Example

```python
def greet_user(username, course):
    print(f"Hello, {username}! Course: {course}")

greet_user("Amit", "BTech")
greet_user("Priya", "BCA")
```

### Calculator Function Example

```python
def calculate(a, b, symbol):
    if symbol == "+":
        print(a + b)
    elif symbol == "-":
        print(a - b)
```

---

# 4️⃣ Multiplication Table using Function

Functions can automate repetitive tasks.

```python
def table(num):
    for i in range(11):
        print(f"{num} * {i} = {num * i}")

table(5)
```

### Output Purpose

Generates the complete multiplication table for any number.

---

# 5️⃣ Return Statement

Printing a value only displays it. Returning a value allows it to be reused elsewhere in the program.

## Syntax

```python
return value
```

### Example

```python
def calculate_square(number):
    return number * number

result = calculate_square(5)

print(result)
```

### Why Return is Important

| Print                   | Return                      |
| ----------------------- | --------------------------- |
| Only displays output    | Sends value back to program |
| Cannot be reused easily | Can be stored and processed |
| Mainly for users        | Mainly for program logic    |

---

# 6️⃣ Prime Number Function

A prime number is divisible only by 1 and itself.

### Example

```python
def is_prime(n):
    if n <= 1:
        return False

    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False

    return True
```

### Test

```python
result = is_prime(11)

print(result)
```

### Output

```python
True
```

---

# 7️⃣ Types of Arguments

Python provides flexibility while passing values to functions.

## Argument Types

| Type                      | Description                           |
| ------------------------- | ------------------------------------- |
| Positional Arguments      | Values assigned according to order    |
| Keyword Arguments         | Values assigned using parameter names |
| Default Arguments         | Predefined default values             |
| Variable-Length Arguments | Accept unlimited inputs               |

### Example

```python
def intro(name, age=18, course="12th"):
    print(f"{name} is {age} years old and studies in {course}")

intro("Sahil", 17, "11th")
intro("Priya")
```

---

# 8️⃣ Variable-Length Arguments

Sometimes the number of inputs is unknown.

Python provides:

## `*args`

Accepts multiple positional arguments.

```python
def calculate_total_expenses(*expenses):
    return sum(expenses)

total = calculate_total_expenses(12.5, 45.0, 100.25, 7.8)
```

### Output

```python
165.55
```

---

## `**kwargs`

Accepts multiple keyword arguments.

```python
def print_model_parameters(**hyperparams):
    print(hyperparams)

print_model_parameters(learning_rate=0.01, epochs=100)
```

### Output

```python
{
    'learning_rate': 0.01,
    'epochs': 100
}
```

---

# 9️⃣ Variable Scope

Scope determines where a variable can be accessed.

## Types of Scope

| Scope        | Description                     |
| ------------ | ------------------------------- |
| Global Scope | Accessible throughout program   |
| Local Scope  | Accessible only inside function |

### Example

```python
metric_name = "Accuracy"

def evaluate():
    score = 0.95
    print(metric_name, score)

evaluate()
```

---

# 🔟 Global Keyword

The `global` keyword allows modification of a global variable inside a function.

### Example

```python
a = 10

def change():
    global a
    a = 20

change()

print(a)
```

### Output

```python
20
```

---

# 1️⃣1️⃣ Recursive Functions

A recursive function calls itself repeatedly until a stopping condition is reached.

## Components of Recursion

| Component      | Purpose              |
| -------------- | -------------------- |
| Base Case      | Stops recursion      |
| Recursive Case | Calls function again |

### Advantages

* Elegant solutions
* Useful for tree structures
* Suitable for divide-and-conquer algorithms

---

# 1️⃣2️⃣ Factorial using Recursion

### Formula

```text
5! = 5 × 4 × 3 × 2 × 1
```

### Implementation

```python
def calculate_factorial(n):
    if n == 0 or n == 1:
        return 1
    else:
        return n * calculate_factorial(n - 1)

print(calculate_factorial(5))
```

### Output

```python
120
```

---

# 1️⃣3️⃣ Fibonacci Sequence using Recursion

The Fibonacci sequence follows:

```text
0, 1, 1, 2, 3, 5, 8, 13, ...
```

## Formula

```python
fib(0) = 0
fib(1) = 1
fib(n) = fib(n-1) + fib(n-2)
```

### Implementation

```python
def fibonacci(n):
    if n == 0 or n == 1:
        return n
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)

print(fibonacci(6))
```

### Output

```python
8
```

---

# 🎯 Key Learnings

* Understood the importance of functions in modular programming.
* Learned to create reusable custom functions.
* Explored parameters, arguments, and return statements.
* Implemented practical examples such as calculators and prime number checkers.
* Learned different argument-passing techniques.
* Understood local and global variable scope.
* Used the `global` keyword to modify global variables.
* Implemented recursive solutions for factorial and Fibonacci problems.
* Connected function concepts with real-world AI/ML programming practices.

---

# 🏁 Conclusion

Day 3 focused on mastering **Functions and Modular Programming**, which form the backbone of scalable Python applications. Understanding functions enables developers to write cleaner, reusable, and more efficient code. Concepts such as recursion, argument handling, and scope management are essential not only for Python development but also for advanced AI, Machine Learning, and Data Science projects.

⭐ This session strengthened the foundation required for writing structured and professional Python programs.
