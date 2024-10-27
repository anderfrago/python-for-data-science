# 08 Other tools

## High-Level File Operations with `shutil`

The `shutil` module in Python provides a set of high-level operations on files and collections of files. It is especially useful for copying and moving files and directories.

*   **Recursively Delete a Directory Tree**: Use `shutil.rmtree()` to delete a directory and all its contents.

    ```python
    import shutil
    shutil.rmtree('directory_to_delete')
    ```
*   **Move Files or Directories**: Use `shutil.move()` to move a file or directory to a new location.

    ```python
    shutil.move('source_path', 'destination_path')
    ```
*   **Copy Files or Directories**: Use `shutil.copy()` to copy a file or directory.

    ```python
    shutil.copy('source_file', 'destination_file')
    ```

## File Pattern Matching with `glob`

The `glob` module is used for pattern matching in file names, similar to Unix shell-style wildcards.

*   **Find Files with Specific Extensions**: Use `glob.glob()` to find all files matching a specific pattern.

    ```python
    import glob
    txt_files = glob.glob('*.txt')
    print(txt_files)  # Output: ['holy_grail.txt', 'junk.txt', 'newfile.txt']
    ```

## System-Specific Information with `sys`

The `sys` module provides access to some variables used or maintained by the Python interpreter and to functions that interact with the interpreter.

*   **Python Version and Installation Path**: Retrieve information about the Python version and where it is installed.

    ```python
    import sys
    print(sys.platform)  # Output: 'darwin' (or your platform)
    print(sys.version)   # Output: Python version details
    print(sys.prefix)    # Output: Installation path
    ```
*   **Command Line Arguments**: Access the list of command line arguments passed to a Python script.

    ```python
    print(sys.argv)  # Output: List of command line arguments
    ```
*   **Module Search Path**: `sys.path` is a list of strings that specifies the search path for modules.

    ```python
    print(sys.path)  # Output: List of paths where Python looks for modules
    ```

## Object Persistence with `pickle`

The `pickle` module is used for serializing and deserializing Python objects, allowing you for easy storage and retrieval of complex data types.

*   **Serialize Objects**: Use `pickle.dump()` to serialize an object and write it to a file.

    ```python
    import pickle

    # Create a list
    my_list = [1, None, 'Stan']

    # Serialize and save to a file
    with open('test.pkl', 'wb') as file:
        pickle.dump(my_list, file)
    ```
*   **Deserialize Objects**: Use `pickle.load()` to read a serialized object from a file.

    ```python
    # Load the object from the file
    with open('test.pkl', 'rb') as file:
        loaded_list = pickle.load(file)

    print(loaded_list)  # Output: [1, None, 'Stan']
    ```

## Exercise: Search for `site.py` in PYTHONPATH

The goal is to iterate over the directories listed in `sys.path` and check if `site.py` exists in any of them. This script will help you locate the `site.py` module if it is present in your Python environment.

```python
import sys
import os

def find_site_py():
    # Iterate over each path in the sys.path list
    for path in sys.path:
        # Construct the full path to site.py
        site_py_path = os.path.join(path, 'site.py')

        # Check if site.py exists at this path
        if os.path.isfile(site_py_path):
            print(f"Found site.py at: {site_py_path}")
            return site_py_path

    # If site.py is not found in any of the paths
    print("site.py not found in PYTHONPATH.")
    return None

# Execute the function to search for site.py
find_site_py()
```

## Explanation

* **`sys.path`**: This is a list of strings that specifies the search path for modules. It is initialized from the `PYTHONPATH` environment variable and can be modified during runtime.
* **`os.path.join()`**: This function is used to construct a full file path by joining one or more path components intelligently.
* **`os.path.isfile()`**: This function checks if a given path is an existing regular file.

## How to Run the Script

1. Save the script to a file, for example, `find_site.py`.
2.  Run the script using Python from the command line:

    ```bash
    python find_site.py
    ```
3. The script will output the path to `site.py` if it is found, or indicate that it is not found in the `PYTHONPATH`.

This exercise demonstrates how to use Python's standard library modules to interact with the file system and environment variables, providing a practical example of searching for a specific module within the Python environment.
