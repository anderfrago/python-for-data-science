# 05 Code Reuse: Scripts and Modules

When working with Python, especially for larger projects, it's beneficial to write your code in text files, known as scripts or modules, rather than typing everything directly into the interpreter. This approach allows for better organization and reuse of code.

### Scripts

A script is essentially a file containing a sequence of Python instructions that are executed sequentially. You can create a script using any text editor that supports Python syntax highlighting. Save your script with a `.py` extension.

For example, create a file named `example.py` with the following content:

```python
greeting = "Hello, world!"
for char in greeting:
    print(char)
```

To execute this script within an interactive Python session, such as IPython, you can use the `%run` command:

```python
In [1]: %run example.py
H
e
l
l
o
,

w
o
r
l
d
!
```

After running the script, any variables defined within it, like `greeting`, are available in the interactive session.

Scripts can also be executed directly from the command line:

```bash
$ python example.py
H
e
l
l
o
,

w
o
r
l
d
!
```

Scripts can accept command-line arguments using the `sys` module:

```python
# In script.py
import sys
print(sys.argv)
```

Running this script with arguments:

```bash
$ python script.py arg1 arg2
['script.py', 'arg1', 'arg2']
```

### Modules

Modules are Python files that can be imported into other Python scripts. This allows you to reuse functions, classes, and variables across different scripts.

For example, create a module named `utilities.py`:

```python
def greet(name):
    """Print a greeting message."""
    print(f"Hello, {name}!")

def farewell(name):
    """Print a farewell message."""
    print(f"Goodbye, {name}!")
```

You can import and use this module in another script:

```python
import utilities

utilities.greet("Alice")
utilities.farewell("Bob")
```

### Importing from Modules

You can import specific functions or variables from a module:

```python
from utilities import greet

greet("Charlie")
```

Avoid using wildcard imports (`from module import *`) as they can lead to unintended consequences, such as name clashes and reduced code readability. Instead, import only what you need to maintain clarity and avoid potential conflicts.

### Creating Your Own Modules

To create a module, simply write your Python code in a `.py` file. For larger projects, organizing your code into modules can help manage complexity and improve reusability.

For instance, consider a module `math_utils.py`:

```python
def add(a, b):
    """Return the sum of two numbers."""
    return a + b

def subtract(a, b):
    """Return the difference between two numbers."""
    return a - b
```

You can import and use these functions in another script:

```python
import math_utils

result = math_utils.add(5, 3)
print(result)  # Output: 8
```

### Reloading Modules

When you modify a module, you need to reload it to see the changes in an interactive session. In Python 3, use the `importlib` module:

```python
import importlib
importlib.reload(math_utils)
```

### Using `__main__` for Script Execution

Sometimes, you want certain code to run only when a script is executed directly, not when it's imported as a module. Use the `if __name__ == '__main__':` construct for this purpose:

```python
# In main_example.py
def main():
    print("This runs only when the script is executed directly.")

if __name__ == '__main__':
    main()
```

### Organizing Code: Scripts vs. Modules

* **Scripts**: Use for code that performs specific tasks and is executed directly.
* **Modules**: Use for reusable code, such as functions and classes, that can be imported into multiple scripts.

### Finding and Importing Modules

Python searches for modules in a list of directories defined by the `sys.path` variable. You can add directories to this list by modifying the `PYTHONPATH` environment variable or directly in your script:

```python
import sys
sys.path.append('/path/to/your/modules')
```

### Packages

A package is a directory containing multiple modules, identified by an `__init__.py` file. This file can be empty or contain initialization code for the package.

Example package structure:

```
mypackage/
    __init__.py
    module1.py
    module2.py
```

You can import modules from a package using the dot notation:

```python
import mypackage.module1
from mypackage import module2
```

### Summary

* **Scripts**: Use for executing tasks directly. They can be run from the command line or within an interactive session.
* **Modules**: Use for organizing reusable code. They can be imported into other scripts or modules.
* **Packages**: Use for organizing related modules into a directory structure, allowing for a hierarchical organization of code.

By organizing your code into scripts, modules, and packages, you can create more maintainable, reusable, and scalable Python projects. This approach not only enhances code readability but also facilitates collaboration and version control in larger projects.
