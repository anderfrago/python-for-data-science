# 04 Defining Functions in Python

Functions in Python are blocks of reusable code that perform a specific task. They help in organizing code and making it more readable and maintainable.

### Creating a Function

To define a function, use the `def` keyword followed by the function name and parentheses. The function body is indented.

```python
def greet():
    print('Hello from the greet function!')

greet()
```

**Note:** Indentation is crucial in Python to define the scope of the function.

### Returning Values

Functions can return values using the `return` statement.

```python
def calculate_area(radius):
    return 3.14159 * radius * radius

print(calculate_area(2))
```

If no `return` statement is used, the function returns `None` by default.

### Function Syntax

* **`def` keyword**: Used to define a function.
* **Function name**: Followed by parentheses.
* **Parameters**: Inside the parentheses, separated by commas.
* **Colon (`:`)**: Ends the function header.
* **Function body**: Indented block of code.
* **Return statement**: Optional, to return values.

### Parameters

Functions can have mandatory (positional) and optional (keyword) parameters.

**Positional Parameters:**

```python
def multiply_by_two(x):
    return x * 2

print(multiply_by_two(4))
```

**Keyword Parameters:**

```python
def multiply_by_two(x=3):
    return x * 2

print(multiply_by_two())
print(multiply_by_two(5))
```

**Note:** Default values are evaluated when the function is defined, not when it is called. Be cautious with mutable default values.

### Mutable and Immutable Types

Parameters are passed by reference, but the behavior depends on whether the object is mutable or immutable.

```python
def modify_list(lst):
    lst.append(100)

my_list = [1, 2, 3]
modify_list(my_list)
print(my_list)  # Output: [1, 2, 3, 100]
```

### Global Variables

Variables defined outside a function can be accessed inside it. To modify them, use the `global` keyword.

````python
x = 10

def change_x():
    global x
    x = 20

change_x()
print(x)  # Output: 20
``

### Variable Number of Parameters

Python allows functions to accept a variable number of arguments using special syntax:

- **`*args`**: Collects extra positional arguments into a tuple.
- **`**kwargs`**: Collects extra keyword arguments into a dictionary.

```python
def display_info(*args, **kwargs):
    print('Positional arguments:', args)
    print('Keyword arguments:', kwargs)

display_info('apple', 'banana', fruit='orange', count=3)
````

## Docstrings

Docstrings are used to document what a function does. They are written as the first statement in a function and can be accessed using the `__doc__` attribute or the `help()` function.

```python
def add(a, b):
    """Add two numbers and return the result."""
    return a + b

print(add.__doc__)
```

## Functions as First-Class Objects

In Python, functions are first-class objects, meaning they can be:

* Assigned to variables
* Stored in data structures
* Passed as arguments to other functions

```python
def greet(name):
    return f"Hello, {name}!"

say_hello = greet
print(say_hello("Alice"))
```

## Methods

Methods are functions that are associated with an object. They are called on objects and can access and modify the object's data.

```python
class Dog:
    def __init__(self, name):
        self.name = name

    def bark(self):
        print(f"{self.name} says woof!")

my_dog = Dog("Buddy")
my_dog.bark()
```

## Exercises

**Exercise: Fibonacci Sequence**

Write a function to generate the first `n` terms of the Fibonacci sequence.

```python
def fibonacci(n):
    sequence = [0, 1]
    for i in range(2, n):
        sequence.append(sequence[-1] + sequence[-2])
    return sequence[:n]

print(fibonacci(10))
```

**Exercise: Quicksort Algorithm**

Implement the quicksort algorithm to sort an array.

```python
def quicksort(arr):
    if len(arr) < 2:
        return arr
    pivot = arr[0]
    less = [x for x in arr[1:] if x <= pivot]
    greater = [x for x in arr[1:] if x > pivot]
    return quicksort(less) + [pivot] +
```
