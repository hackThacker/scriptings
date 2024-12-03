# Introduction to Python for Security: Scripting for Pentesters

Welcome to the **Scripting for Pentesters** module! In this section, you'll gain hands-on experience with the Python programming language. While programming skills aren't strictly required to succeed in cybersecurity, learning to script is an invaluable asset. As demonstrated in this module, Python enables you to create security tools, automate tasks, and build quick scripts that can assist you in penetration testing, defense, and analysis.

## What You Will Learn

By the end of this room, you'll have learned how to work with the following core concepts in Python:

- [Operations](#mathematical-and-comparison-operators-in-python)
- [Variable](#working-with-variables-and-data-types-in-python)
- [Logical](#logical-and-boolean-operators-in-python)
- [If Statements](#using-if-statements-in-python)
- [Loops](#loops-in-python)
- [Functions](#functions-in-python)
- [Data Structures](#data-structures)
- [File Handling](#file-handling-in-python)
- [Importing Libraries](#importing-libraries-in-python)
- [Exception Handling in Python](#exception-handling-in-python)
- [Object-Oriented Programming (OOP) in Python](#object-oriented-programming-oop-in-python)
    1. [Classes and Objects](#classes-and-objects)
    2. [Inheritance](#inheritance)
    3. [Encapsulation](#encapsulation)
    4. [Polymorphism](#polymorphism)
    5. [Abstraction](#abstraction)
    6. [Summary of OOP Concepts](#summary-of-oop-concepts)




These concepts will provide you with the foundation to write basic scripts and tools for your security work. The goal is to give you enough knowledge to begin building and utilizing Python in real-world scenarios, especially for penetration testing and security-related tasks.

## Hands-On Practice

You will use the built-in code editor (on the right-hand side) to complete exercises and challenges. These exercises are designed to teach you Python basics in a practical, hands-on manner. By working through the examples, you'll build a solid understanding of how to apply Python in the context of cybersecurity.

### Setting Up Python on Your System

If you'd prefer to use your own development environment instead of the provided editor, you can download and install Python from the official website. Installing Python will also give you an Integrated Development Environment (IDE) for writing and running Python code.

- Download Python from: [https://www.python.org/downloads/](https://www.python.org/downloads/)

The official Python IDE is called **IDLE**, but you can also use popular alternatives like **PyCharm**, **Visual Studio Code**, or **Sublime Text**.

## Understanding Syntax

In programming, **syntax** plays a crucial role in writing valid code. Syntax refers to the rules that define the structure of a programming language. It dictates how symbols, punctuation, and words should be arranged to make the code understandable to the computer.

In simpler terms, syntax is like the grammar of a language. Just as a sentence in English needs proper punctuation and structure to make sense, code must follow specific rules for the program to execute correctly. Understanding syntax is essential to writing clean, functional code.


---

# Mathematical and Comparison Operators in Python

In Python, mathematical and comparison operators are fundamental tools for performing calculations and making decisions based on conditions. Let's start by exploring the basic **mathematical operators** and then move on to **comparison operators**, which are critical for controlling the flow of a program.

## Mathematical Operators

Mathematical operators allow you to perform basic arithmetic operations like addition, subtraction, multiplication, and division. Below is a table showcasing the commonly used mathematical operators and their syntax in Python.

| **Operator** | **Syntax** | **Example**            | **Result** |
|--------------|------------|------------------------|------------|
| Addition     | `+`        | `1 + 1`                | `2`        |
| Subtraction  | `-`        | `5 - 1`                | `4`        |
| Multiplication | `*`      | `10 * 10`              | `100`      |
| Division     | `/`        | `10 / 2`               | `5.0`      |
| Modulus      | `%`        | `10 % 2`               | `0`        |
| Exponent     | `**`       | `5 ** 2`               | `25`       |

### Explanation:
- **Addition (`+`)**: Adds two numbers.
- **Subtraction (`-`)**: Subtracts the second number from the first.
- **Multiplication (`*`)**: Multiplies two numbers.
- **Division (`/`)**: Divides the first number by the second and returns a floating-point result.
- **Modulus (`%`)**: Returns the remainder of the division.
- **Exponent (`**`)**: Raises the first number to the power of the second.

## Comparison Operators

Comparison operators are used to evaluate expressions or conditions in Python. They help to compare values and make decisions, which is essential when using loops or conditional statements (e.g., `if` statements). Below is a table showcasing the most common comparison operators.

| **Operator**      | **Syntax**  | **Example**      | **Result**        |
|-------------------|-------------|------------------|-------------------|
| Greater than      | `>`         | `5 > 3`          | `True`            |
| Less than         | `<`         | `3 < 5`          | `True`            |
| Equal to          | `==`        | `5 == 5`         | `True`            |
| Not Equal to      | `!=`        | `5 != 3`         | `True`            |
| Greater than or equal to | `>=`   | `5 >= 5`         | `True`            |
| Less than or equal to    | `<=`   | `3 <= 5`         | `True`            |

### Explanation:
- **Greater than (`>`)**: Checks if the value on the left is greater than the value on the right.
- **Less than (`<`)**: Checks if the value on the left is less than the value on the right.
- **Equal to (`==`)**: Checks if both values are equal.
- **Not Equal to (`!=`)**: Checks if both values are not equal.
- **Greater than or equal to (`>=`)**: Checks if the value on the left is greater than or equal to the value on the right.
- **Less than or equal to (`<=`)**: Checks if the value on the left is less than or equal to the value on the right.

---


# Working with Variables and Data Types in Python

In Python, **variables** are used to store data that can be accessed and modified throughout the program. A variable is essentially a container for a piece of data that you can reference and manipulate by using the variable's name.

## Variables

Variables allow you to store and update data in your program. Each variable has a name, and the value you store in it can be anything, such as a number or a string of text.

### Example:

```python
food = "ice cream"
money = 2000
```

In this example:
- The variable `food` is storing the string `"ice cream"`.
- The variable `money` is storing the integer value `2000`.

### Updating Variables

Variables in Python are powerful because you can change their values during the course of the program. For example, you can update a variable like this:

```python
age = 30
age = age + 1
print(age)
```

In this case:
- The variable `age` is initially set to `30`.
- On the second line, we update the `age` variable by adding `1` to its current value.
- The final value of `age` will be `31` when printed.

Notice how the variable `age` is updated on the left side of the assignment (`=`) operator, and the updated value on the right side (`age + 1`).

---

## Data Types in Python

Data types define the kind of data that can be stored in a variable. Python has several built-in data types, each used for storing specific kinds of information. Here's an overview of the most commonly used data types:

### Common Data Types:

| **Data Type** | **Description**                                   | **Example**         |
|---------------|---------------------------------------------------|---------------------|
| **String**    | A sequence of characters, such as letters or symbols. | `"Hello, World!"`    |
| **Integer**   | Whole numbers (positive or negative).              | `42`                |
| **Float**     | Numbers that contain decimal points (fractions).   | `3.14`              |
| **Boolean**   | Data that can be either `True` or `False`.         | `True` or `False`    |
| **List**      | A collection of values, which can be of different data types. | `[1, 2, 3, "apple"]` |

### Explanation of Data Types:
- **String (`str`)**: Strings are used to store sequences of characters, such as names, sentences, or symbols. They are enclosed in either double quotes (`" "`) or single quotes (`' '`).

  ```python
  name = "Alice"
  greeting = 'Hello!'
  ```

- **Integer (`int`)**: Integers are whole numbers that do not have a decimal point. They can be positive or negative.

  ```python
  age = 25
  score = -100
  ```

- **Float (`float`)**: Floats are numbers that contain a decimal point. They can represent real numbers and fractions.

  ```python
  pi = 3.14159
  temperature = -5.5
  ```

- **Boolean (`bool`)**: Booleans are binary values that can only be `True` or `False`. These are often used for conditional checks.

  ```python
  is_active = True
  is_student = False
  ```

- **List (`list`)**: Lists are collections of items (elements) that can be of any data type. Lists are enclosed in square brackets (`[ ]`) and elements are separated by commas.

  ```python
  fruits = ["apple", "banana", "cherry"]
  mixed = [1, 3.14, "hello", True]
  ```

---



# Logical and Boolean Operators in Python

Logical operators allow assignment and comparisons to be made and are used in conditional testing (such as in `if` statements). These operators are essential for controlling the flow of execution based on conditions.

## Logical Operators

Logical operators are used to compare values and determine the relationships between them. The most common logical operations in Python are:

| **Logical Operation**              | **Operator** | **Example**               |
|------------------------------------|--------------|---------------------------|
| **Equivalence**                    | `==`         | `if x == 5`               |
| **Less than**                       | `<`          | `if x < 5`                |
| **Less than or equal to**           | `<=`         | `if x <= 5`               |
| **Greater than**                    | `>`          | `if x > 5`                |
| **Greater than or equal to**        | `>=`         | `if x >= 5`               |

### Example Usage:

```python
x = 10
if x >= 5:
    print("x is greater than or equal to 5")
```

In this example:
- The code checks if `x` is greater than or equal to `5` using the `>=` operator.

## Boolean Operators

Boolean operators are used to combine and compare relationships between different conditions or statements. They are commonly used in `if` statements to determine whether a condition is true or false.

### Common Boolean Operators:

| **Boolean Operation**                 | **Operator** | **Example**                         |
|---------------------------------------|--------------|-------------------------------------|
| **Both conditions must be true for the statement to be true** | `AND`        | `if x >= 5 AND x <= 100`           |
| **Returns TRUE if x is between 5 and 100** |              |                                     |
| **Only one condition of the statement needs to be true** | `OR`         | `if x == 1 OR x == 10`            |
| **Returns TRUE if x is 1 or 10**       |              |                                     |
| **If a condition is the opposite of an argument** | `NOT`        | `if NOT y`                         |
| **Returns TRUE if the y value is False** |              |                                     |

### Example Usage:

```python
a = 1
if a == 1 or a > 10:
     print("a is either 1 or above 10")
```

In this example:
- The condition checks whether `a` is equal to `1` or greater than `10` using the `or` operator.

### Using `AND`, `OR`, and `NOT` Together:

```python
name = "bob"
hungry = True

if name == "bob" and hungry == True:
     print("bob is hungry")
elif name == "bob" and not hungry:
     print("Bob is not hungry")
else:  # If all other conditions are not met
     print("Not sure who this is or if they are hungry")
```

In this code:
- The `if` statement checks if `name` is equal to `"bob"` and `hungry` is `True`. If both conditions are true, it prints `"bob is hungry"`.
- The `elif` statement checks if `name` is `"bob"` and `hungry` is `False`, printing `"Bob is not hungry"`.
- If neither condition is met, the `else` block is executed, printing `"Not sure who this is or if they are hungry"`.

---


# Using "If Statements" in Python

In Python, **if statements** allow programs to make decisions. They enable a program to choose a specific action based on a condition. This is a fundamental concept in programming, as it allows the program to execute different blocks of code depending on whether a condition is met.

## Example of an If Statement

```python
age = 16

if age < 17:
    print('You are NOT old enough to drive')
else:
    print('You are old enough to drive')
```

### Explanation:
- In the above example, if the variable `age` is less than `17`, the program will print the message `"You are NOT old enough to drive"`.
- If `age` is greater than or equal to `17`, the program will print `"You are old enough to drive"`.
- The condition being checked is `age < 17`, and based on whether this condition is **True** or **False**, different sections of code will be executed.

## Key Components of an If Statement

There are a few key points to understand about how an `if` statement works in Python:

1. **The `if` keyword**: This indicates the start of an `if statement`, followed by a condition to evaluate.
   
2. **Condition**: The condition (in this case, `age < 17`) is what is being checked. The `if` statement will only execute the code that follows it if the condition is **True**.

3. **The `else` keyword**: This part of the statement specifies a block of code to run if the condition is **False**.

4. **Colon (`:`)**: After the condition in an `if` or `else` statement, a colon `:` is required to indicate the start of the block of code to be executed.

5. **Indentation**: Anything that is indented after the colon is considered part of the `if` statement (or `else` statement). Proper indentation is crucial in Python, as it defines the scope of the statement.

### Example with Indentation:

```python
age = 20

if age < 17:
    print('You are NOT old enough to drive')
else:
    print('You are old enough to drive')
```

In this example:
- If `age` is less than `17`, the first print statement runs.
- If `age` is **greater than or equal to 17**, the code inside the `else` block will execute.

---

# Loops in Python

In programming, **loops** allow programs to iterate and perform actions multiple times. There are two main types of loops in Python: **for loops** and **while loops**. Both allow you to execute a block of code repeatedly, but they function in different ways.

## While Loops

A **while loop** runs as long as the condition provided is true. It will continue to loop until the condition becomes false.

### Example of a While Loop:

```python
i = 1
while i <= 10:
    print(i)
    i = i + 1
```

### Explanation:
- The variable `i` is initially set to `1`.
- The `while` loop checks if `i <= 10`. As long as this condition is true, the code inside the loop will execute.
- The `print(i)` statement outputs the current value of `i`.
- After printing, `i` is incremented by `1` (`i = i + 1`).
- The loop continues until `i` becomes greater than `10`.

In this case, the loop will run 10 times, outputting the numbers 1 to 10.

### Key Points:
- The loop runs indefinitely or for a specified number of times based on the condition.
- The loop continues until the condition is no longer true.

## For Loops

A **for loop** is used to iterate over a sequence (such as a list, tuple, or string) or a range of numbers. It allows you to loop through each element in the sequence.

### Example of a For Loop:

```python
websites = ["facebook.com", "google.com", "amazon.com"]
for site in websites:
    print(site)
```

### Explanation:
- The variable `websites` is a list that contains 3 strings.
- The `for` loop iterates through each element in the list, assigning the current element to the variable `site`.
- The loop then executes the `print(site)` statement, outputting the current value of `site` (i.e., each website).
- The loop stops when it has gone through all the elements in the list.

In this case, the loop will print each website in the list:

```
facebook.com
google.com
amazon.com
```

### Key Points:
- The loop will iterate through each element in a sequence.
- After the loop has gone through all elements, it stops.


## Using the `range` Function in For Loops

In Python, you can use the `range()` function to generate a sequence of numbers, and iterate over it with a **for loop**.

### Example:

```python
for i in range(5):
    print(i)
```

### Explanation:
- The `range(5)` function generates a sequence of numbers from 0 to 4.
- The `for` loop iterates over this range, printing each number in the sequence.

The output will be:

```
0
1
2
3
4
```

### Key Points:
- The `range()` function generates a sequence of numbers.
- The loop will iterate over these numbers, starting from 0 up to, but not including, 5.

---



# Functions in Python

As programs grow larger and more complex, some of your code may become repetitive, requiring the same calculations or actions to be performed multiple times. This is where **functions** come in. A **function** is a block of code designed to perform a specific task. Once defined, a function can be called at different places in your program, removing the need to repeat the same code.

### Why Use Functions?
- Functions help eliminate repetitive code by allowing you to reuse a block of code multiple times.
- You can define a function to perform calculations, format text, or execute any task you want to repeat in different parts of your program.

## Defining a Function

To define a function, we use the `def` keyword, followed by the function name and a pair of parentheses `()` which can hold input values (known as parameters). After that, a colon `:` marks the beginning of the function's body, and the code inside the function is indented.

### Example 1: A Simple Function

```python
def sayHello(name):
    print("Hello " + name + "! Nice to meet you.")

sayHello("Ben")  # Output: Hello Ben! Nice to meet you
```

### Explanation:
- The `def` keyword defines the function.
- `sayHello` is the name of the function.
- The parameter `name` is passed to the function.
- The function prints a greeting with the passed name.

### Key Components:
1. **def keyword**: Defines the function.
2. **Function name**: `sayHello` is the function name.
3. **Parentheses ()**: Used for passing parameters.
4. **Colon (:)**: Marks the start of the function body.
5. **Indentation**: Everything indented after the colon is part of the function.

---

## Returning Values from Functions

Functions can return values that can be used elsewhere in the program. For example, you can create a function to perform calculations and return the result.

### Example 2: Function Returning a Value

```python
def calcCost(item):
    if(item == "sweets"):
        return 3.99
    elif (item == "oranges"):
        return 1.99
    else:
        return 0.99

spent = 10
spent = spent + calcCost("sweets")
print("You have spent: $" + str(spent))
```

### Explanation:
- The `calcCost` function takes an `item` as input.
- It checks the `item` and returns the corresponding cost based on the conditions.
- In the main part of the program, we call `calcCost("sweets")`, which returns `3.99`.
- The result is added to the `spent` variable, and the final amount is printed.

### Key Points:
- The `return` statement sends the result of the function back to the place where the function was called.
- The function `calcCost` returns different values depending on the input.
- The `spent` variable is updated by adding the cost returned by the function.

---

# File Handling in Python

In Python, you can read from and write to files, which is especially useful in fields like cybersecurity. Scripts often import or export data from files, whether it's to store output or to load a list (e.g., a list of websites to enumerate).

## Reading from a File

To read from a file, you can use the built-in `open()` function. The `"r"` parameter stands for "read", indicating that you're opening the file in read mode. Here's an example:

### Example: Reading from a File

```python
f = open("file_name", "r")  # Open file in read mode
print(f.read())  # Read the entire contents of the file
```

### Explanation:
- The `open()` function opens the file named `"file_name"` in read mode (`"r"`).
- The `read()` method reads the entire content of the file and prints it to the console.

If the file is in the same directory as the Python script, you only need to provide the filename. If it's located elsewhere, you must specify the full path to the file.

### Reading Line by Line

You can also read the file line by line using the `readlines()` method. This is particularly useful when the file contains a list of items, each on a new line.

```python
f = open("file_name", "r")
for line in f.readlines():
    print(line)
f.close()
```

### Closing the File
- Always remember to close the file after you're done reading. You can do this by calling the `close()` method, which ensures that the file is properly closed and that resources are freed.


## Writing to a File

Python also allows you to write data to a file. You can append data to an existing file or create and write to a new file.

### Example: Appending to an Existing File

```
f = open("demofile1.txt", "a")  # Open file in append mode
f.write("The file will include more text..")
f.close()
```

### Example: Creating and Writing to a New File

```
f = open("demofile2.txt", "w")  # Create a new file or overwrite an existing file
f.write("demofile2 file created, with this content in!")
f.close()
```

### Explanation:
- **"a" (append)**: This mode appends new data to the end of an existing file.
- **"w" (write)**: This mode creates a new file or overwrites an existing one. It will erase the existing content in the file if the file already exists.
- The `write()` method writes a string to the file.
- Don't forget to use `close()` to close the file after writing, ensuring all changes are saved.



.

### Key Points:
- **Reading Files**: Use `open()` with `"r"` and methods like `read()` or `readlines()`.
- **Writing to Files**: Use `open()` with `"w"` (write) or `"a"` (append) and the `write()` method.
- Always **close** the file after you're done to free up resources.

By mastering file handling, you can manage large datasets, log outputs, and automate processes more efficiently in your Python programs.

---

# Importing Libraries in Python

In Python, you can import libraries, which are collections of pre-written functions that you can use in your program. Think of importing a library as gaining access to a set of functions that are already available for you to use. For example, there is a **datetime** library that provides you with many functions for working with dates and times.

## Example: Importing and Using the `datetime` Library


import datetime  # Importing the datetime library
current_time = datetime.datetime.now()  # Accessing the current date and time
print(current_time)  # Output the current date and time


### Explanation:
- We use the `import` keyword to import a library.
- After importing the `datetime` library, we use `datetime.datetime.now()` to get the current date and time.
- The `.now()` method is a function inside the `datetime` library that returns the current date and time.

### Popular Libraries for Pentesting
Here are some useful libraries that you may encounter in scripting as a **pentester**:

- **Request**: A simple HTTP library used for sending HTTP requests.
- **Scapy**: A library for sending, sniffing, dissecting, and forging network packets.
- **Pwntools**: A CTF (Capture The Flag) and exploit development library.

### Installing External Libraries

While many libraries are built into Python, some libraries are written by other developers and are not pre-installed on your machine. You can install these libraries using **pip**, which is Python's package manager.

For example, if you want to install the **scapy** library (which allows you to craft your own network packets and send them to other machines), you can install it using pip with the following command:

```
pip install scapy
```

Once installed, you can import the **scapy** library and use its functions in your program.

### Summary:
- **Importing Libraries**: Use the `import` keyword to gain access to predefined functions in a library.
- **Built-in Libraries**: Libraries like `datetime` are built into Python.
- **External Libraries**: Libraries like `scapy` can be installed using `pip` and then imported into your program.
---


# Exception Handling in Python

Exception handling allows you to manage errors in your Python programs without crashing them. Instead of letting the program stop when it encounters an error, you can use exception handling to gracefully handle the issue and continue execution.

## What is an Exception?

An exception is an error that occurs during the execution of a program. In Python, you can handle these errors using `try`, `except`, `else`, and `finally` blocks.

## Syntax for Exception Handling

```
try:
    # Code that might cause an exception
except ExceptionType:
    # Code that runs if an exception occurs
else:
    # Code that runs if no exception occurs
finally:
    # Code that runs no matter what
```

### **Key Components of Exception Handling**

1. **try**:
   - The `try` block lets you test a block of code for errors.
   - You write the code that might throw an exception inside the `try` block.

2. **except**:
   - The `except` block lets you handle the error.
   - You can specify the type of exception (like `ValueError`, `ZeroDivisionError`, etc.).
   - If the exception occurs, the `except` block executes.

3. **else**:
   - The `else` block will execute if no exception occurs.
   - It is optional and can be used to write code that should run if the `try` block succeeds.

4. **finally**:
   - The `finally` block always runs, regardless of whether an exception occurred or not.
   - It's useful for clean-up actions (e.g., closing files, releasing resources).

## Example : Handling a Division by Zero Error

```python
try:
    num1 = 10
    num2 = 0
    result = num1 / num2
except ZeroDivisionError:
    print("You can't divide by zero!")
else:
    print(f"The result is {result}")
finally:
    print("Execution completed.")
```

**Explanation**:
- In this example, we try to divide `10` by `0`, which raises a `ZeroDivisionError`.
- The `except` block catches the error and prints a message.
- The `finally` block always executes, printing "Execution completed."

**Output**:
```
You can't divide by zero!
Execution completed.
```

## Example : Handling Multiple Exceptions

```python
try:
    num1 = int(input("Enter a number: "))
    result = 10 / num1
except ValueError:
    print("That's not a valid number!")
except ZeroDivisionError:
    print("You can't divide by zero!")
else:
    print(f"The result is {result}")
finally:
    print("Execution completed.")
```

**Explanation**:
- This code handles two types of exceptions: `ValueError` (if the user inputs a non-integer value) and `ZeroDivisionError` (if the user enters `0`).
- It also uses the `else` block to print the result if no exception occurs.

**Output**:
```
Enter a number: 0
You can't divide by zero!
Execution completed.
```

## Example : Using the `else` and `finally` Blocks

```python
def divide_numbers(a, b):
    try:
        result = a / b
    except ZeroDivisionError:
        print("You can't divide by zero!")
    else:
        print(f"Result: {result}")
    finally:
        print("Function execution complete.")

divide_numbers(10, 2)
```

**Explanation**:
- If no error occurs in the `try` block, the `else` block executes and prints the result.
- The `finally` block executes regardless of whether an error occurred or not.

**Output**:
```
Result: 5.0
Function execution complete.
```

## Best Practices for Exception Handling

- **Catch Specific Exceptions**: Always try to catch specific exceptions rather than a general `except` block. This makes your code more robust and easier to debug.
- **Keep `try` Blocks Short**: Only put code that might raise an exception inside the `try` block to avoid catching unintended errors.
- **Use `finally` for Cleanup**: Always use `finally` to release resources or close files, ensuring that clean-up actions are performed regardless of exceptions.

## Common Python Exceptions

Here are some of the most common exceptions in Python that you might encounter:

- **ZeroDivisionError**: Raised when you attempt to divide by zero.
- **ValueError**: Raised when a function receives an argument of the correct type but an inappropriate value (e.g., passing a string instead of a number).
- **IndexError**: Raised when you try to access an index that is out of range in a list or string.
- **FileNotFoundError**: Raised when trying to open a file that doesn't exist.
- **KeyError**: Raised when trying to access a key that doesn’t exist in a dictionary.
---
Yes, I understand. Below is an explanation of **Object-Oriented Programming (OOP)** in Python, including **classes**, **objects**, **inheritance**, and **encapsulation**, all formatted in **Markdown** with examples embedded.

---

# object-oriented-programming-oop-in-python

Object-Oriented Programming (OOP) is a programming paradigm that uses objects and classes to structure code. In Python, OOP allows you to model real-world things as objects, making the code more modular, reusable, and easier to maintain. The core concepts of OOP include **classes**, **objects**, **inheritance**, and **encapsulation**.

# Classes and Objects

### What is a Class?
A **class** is a blueprint for creating objects (instances). It defines a set of attributes and methods that the created objects will have. In Python, classes are created using the `class` keyword.

### What is an Object?
An **object** is an instance of a class. When you create an object, you are creating an instance of a class with its own set of attributes.

### Example: Defining a Class and Creating Objects


## Defining a Class and Creating Objects

```python
class Dog:
    def __init__(self, name, age):
        self.name = name  # Instance variable
        self.age = age    # Instance variable

    def bark(self):
        print(f"{self.name} says woof!")

# Creating objects (instances) of the Dog class
dog1 = Dog("Buddy", 3)
dog2 = Dog("Bella", 5)

dog1.bark()  # Output: Buddy says woof!
dog2.bark()  # Output: Bella says woof!
```

In the example above:
- We define a class `Dog` with an `__init__` method (constructor) to initialize the object’s attributes (`name` and `age`).
- The `bark` method is a function within the class that prints a message when called.
- `dog1` and `dog2` are two objects (instances) of the `Dog` class.

# Inheritance

### What is Inheritance?
**Inheritance** allows a class to inherit attributes and methods from another class. It helps promote code reuse by enabling one class to access the functionality of another class.

### Example: Inheriting from a Parent Class

## Inheriting from a Parent Class

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} makes a sound")

class Dog(Animal):  # Dog inherits from Animal
    def __init__(self, name, breed):
        super().__init__(name)  # Call the constructor of the parent class
        self.breed = breed

    def speak(self):
        print(f"{self.name} says woof!")

class Cat(Animal):  # Cat inherits from Animal
    def speak(self):
        print(f"{self.name} says meow!")

# Creating objects of Dog and Cat
dog = Dog("Buddy", "Golden Retriever")
cat = Cat("Whiskers")

dog.speak()  # Output: Buddy says woof!
cat.speak()  # Output: Whiskers says meow!
```

In this example:
- The `Dog` and `Cat` classes inherit from the `Animal` class.
- The `speak` method is overridden in both the `Dog` and `Cat` classes to provide specific behaviors.
- The `super()` function is used to call the constructor of the parent class (`Animal`).

# Encapsulation

### What is Encapsulation?
**Encapsulation** is the concept of restricting access to some of the object’s components and protecting the object’s internal state. In Python, this is achieved by using private attributes and methods.

### Example: Using Private Attributes and Methods


## Using Private Attributes and Methods

```python
class Account:
    def __init__(self, balance):
        self.__balance = balance  # Private variable

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
        else:
            print("Deposit amount must be positive")

    def withdraw(self, amount):
        if 0 < amount <= self.__balance:
            self.__balance -= amount
        else:
            print("Invalid withdrawal amount")

    def get_balance(self):
        return self.__balance

# Creating an Account object
account = Account(1000)
account.deposit(500)
account.withdraw(200)
print(account.get_balance())  # Output: 1300
```

In this example:
- The `__balance` attribute is private (denoted by the double underscore `__`), meaning it cannot be accessed directly outside the class.
- Methods like `deposit`, `withdraw`, and `get_balance` are used to interact with the private attribute.
- Encapsulation ensures that the balance cannot be modified directly, which helps protect the integrity of the object’s state.

# Polymorphism

### What is Polymorphism?
**Polymorphism** allows a class to define methods that have the same name but behave differently depending on the object calling them. It enables the use of the same method name in multiple classes but with different implementations.

### Example: Polymorphism in Action

## Polymorphism Example

```python
class Animal:
    def speak(self):
        print("Animal makes a sound")

class Dog(Animal):
    def speak(self):
        print("Dog barks")

class Cat(Animal):
    def speak(self):
        print("Cat meows")

# Creating instances of different animal classes
animals = [Dog(), Cat()]

# Using polymorphism
for animal in animals:
    animal.speak()  # Output: Dog barks, Cat meows
```

In this example:
- The `speak` method is defined in both the `Dog` and `Cat` classes, but the behavior is different for each class.
- This is an example of **polymorphism**, where the same method name (`speak`) has different implementations based on the object type.

# Abstraction

### What is Abstraction?
**Abstraction** is the concept of hiding complex implementation details and showing only the essential features of an object. In Python, abstraction can be achieved using abstract classes and methods, typically using the `abc` module.

### Example: Using Abstract Base Class


## Abstraction Example

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius ** 2

# Creating an instance of Circle
circle = Circle(5)
print(circle.area())  # Output: 78.5
```

In this example:
- The `Shape` class is an abstract class with an abstract method `area`. This method doesn't have an implementation in the `Shape` class and must be overridden by subclasses.
- The `Circle` class implements the `area` method to calculate the area of the circle.

---

# Summary of OOP Concepts

- **Classes**: Blueprints for creating objects.
- **Objects**: Instances of classes.
- **Inheritance**: A way for one class to inherit the methods and attributes of another class.
- **Encapsulation**: Restricting access to the internal state of an object and only allowing interaction through public methods.
- **Polymorphism**: The ability for different classes to define methods with the same name but different behaviors.
- **Abstraction**: Hiding complex details and exposing only the essential features.

These OOP principles help make your code more modular, reusable, and easier to maintain.

