# 09 Handling Exceptions in Python

**Understanding Exceptions**

Exceptions are errors that occur during the execution of Python code. They can be caused by various reasons, such as invalid input, incorrect data types, or unexpected conditions. By effectively handling exceptions, you can make your code more robust and prevent unexpected crashes.

**Common Exception Types**

Here are some of the most common exception types you might encounter:

* **ZeroDivisionError:** Raised when you attempt to divide a number by zero.
* **TypeError:** Raised when you try to perform an operation on objects of incompatible types.
* **KeyError:** Raised when you access a dictionary key that doesn't exist.
* **IndexError:** Raised when you try to access an element of a sequence (like a list or tuple) using an invalid index.
* **AttributeError:** Raised when you try to access an attribute of an object that doesn't exist.

**Catching Exceptions**

To handle exceptions gracefully, you can use the `try...except` block. This block allows you to execute code within the `try` block, and if an exception occurs, the code in the `except` block will be executed.

```python
try:
    # Code that might raise an exception
except ExceptionType:
    # Code to handle the exception
```

**Example:**

```python
while True:
    try:
        number = int(input("Enter a number: "))
        break
    except ValueError:
        print("Invalid input. Please enter a number.")
```

**Finally Block**

The `finally` block is optional and is always executed, regardless of whether an exception is raised or not. It's often used for cleanup tasks like closing files or releasing resources.

```python
try:
    # Code that might raise an exception
finally:
    # Code that always executes
```

**Raising Exceptions**

You can raise exceptions using the `raise` keyword. This is useful for indicating that a specific error condition has occurred.

```python
if condition:
    raise ExceptionType("Error message")
```

**Example:**

```python
def divide(a, b):
    if b == 0:
        raise ZeroDivisionError("Cannot divide by zero")
    return a / b
```

**Best Practices**

* **Be specific:** Catch only the exceptions you expect to handle.
* **Use `try...finally` for resource management.**
* **Raise exceptions when appropriate.**
* **Provide informative error messages.**

By following these guidelines, you can write more reliable and maintainable Python code.
