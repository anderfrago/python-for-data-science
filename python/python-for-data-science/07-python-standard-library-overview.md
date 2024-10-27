# 07 Python Standard Library Overview

The Python Standard Library is a comprehensive collection of modules and packages that provide a wide range of functionalities, from file I/O to system operations. For more detailed information, you can refer to the [Python Standard Library documentation](https://docs.python.org/library/index.html) or consult "Python Essential Reference" by David Beazley.

### Operating System Module

The `os` module in Python provides a way to interact with the operating system in a platform-independent manner. It includes functions for directory and file manipulation, among other things.

#### Directory and File Operations

*   **Get Current Directory**: To find out the current working directory, use `os.getcwd()`.

    ```python
    import os
    current_directory = os.getcwd()
    print(current_directory)  # Output: '/path/to/current/directory'
    ```
*   **List Directory Contents**: Use `os.listdir()` to list files and directories in a specified path.

    ```python
    contents = os.listdir('.')
    print(contents)  # Output: ['file1.txt', 'file2.py', 'directory']
    ```
*   **Create a Directory**: Use `os.mkdir()` to create a new directory.

    ```python
    os.mkdir('new_folder')
    print('new_folder' in os.listdir('.'))  # Output: True
    ```
*   **Rename a Directory**: Use `os.rename()` to rename a directory.

    ```python
    os.rename('new_folder', 'renamed_folder')
    print('renamed_folder' in os.listdir('.'))  # Output: True
    ```
*   **Remove a Directory**: Use `os.rmdir()` to delete a directory.

    ```python
    os.rmdir('renamed_folder')
    print('renamed_folder' in os.listdir('.'))  # Output: False
    ```
*   **Delete a File**: Use `os.remove()` to delete a file.

    ```python
    with open('temp.txt', 'w') as file:
        pass
    os.remove('temp.txt')
    print('temp.txt' in os.listdir('.'))  # Output: False
    ```

#### Path Manipulations with `os.path`

The `os.path` module provides utilities for common pathname manipulations.

*   **Get Absolute Path**: Use `os.path.abspath()` to get the absolute path of a file.

    ````python
    ```python
    import os
    ````

**Get the absolute path of a file**

absolute\_path = os.path.abspath('example.txt') print(absolute\_path) # Output: '/path/to/current/directory/example.txt'

````

- **Split Path**: Use `os.path.split()` to separate the directory path and the file name.

  ```python
  directory, filename = os.path.split(absolute_path)
  print(directory)  # Output: '/path/to/current/directory'
  print(filename)   # Output: 'example.txt'
````

*   **Get Directory Name**: Use `os.path.dirname()` to get the directory name from a path.

    ```python
    dir_name = os.path.dirname(absolute_path)
    print(dir_name)  # Output: '/path/to/current/directory'
    ```
*   **Get Base Name**: Use `os.path.basename()` to get the file name from a path.

    ```python
    base_name = os.path.basename(absolute_path)
    print(base_name)  # Output: 'example.txt'
    ```
*   **Split File Extension**: Use `os.path.splitext()` to split the file name and its extension.

    ```python
    name, extension = os.path.splitext(base_name)
    print(name)       # Output: 'example'
    print(extension)  # Output: '.txt'
    ```
*   **Check Path Existence**: Use `os.path.exists()` to check if a path exists.

    ```python
    exists = os.path.exists('example.txt')
    print(exists)  # Output: True or False
    ```
*   **Check if File**: Use `os.path.isfile()` to check if a path is a file.

    ```python
    is_file = os.path.isfile('example.txt')
    print(is_file)  # Output: True or False
    ```
*   **Check if Directory**: Use `os.path.isdir()` to check if a path is a directory.

    ```python
    is_dir = os.path.isdir('example.txt')
    print(is_dir)  # Output: False
    ```
*   **Expand User Path**: Use `os.path.expanduser()` to expand the `~` to the user’s home directory.

    ````python
    home_path = os.path.expanduser('~/documents')
    print(home_path)  # Output: '/home/username/documents'
    ```python
    ````

**Join Paths: Use os.path.join() to concatenate multiple path components intelligently.**

joined\_path = os.path.join(os.path.expanduser('\~'), 'documents', 'project') print(joined\_path) # Output: '/home/username/documents/project'

````

#### Executing External Commands

- **Using `os.system()`**: You can execute a shell command using `os.system()`. This function runs the command in a subshell.

  ```python
  import os
  os.system('ls')  # Lists directory contents
````

*   **Alternative with `sh` Module**: The `sh` module provides a more convenient way to execute shell commands and capture their output.

    ```python
    import sh
    command_output = sh.ls()
    print(command_output)  # Output: List of files and directories
    print(command_output.exit_code)  # Output: 0 (indicating success)
    ```

### Walking Through a Directory

*   **Using `os.walk()`**: This function generates the file names in a directory tree by walking the tree either top-down or bottom-up.

    ```python
    for dirpath, dirnames, filenames in os.walk('.'):
        for filename in filenames:
            print(os.path.abspath(filename))  # Prints the absolute path of each file
    ```

### Environment Variables

*   **Accessing Environment Variables**: You can access environment variables using `os.environ`.

    ```python
    import os
    # List all environment variable keys
    env_keys = os.environ.keys()
    print(env_keys)

    # Access a specific environment variable
    python_path = os.environ.get('PYTHONPATH', 'Not Set')
    print(python_path)
    ```

This overview provides a glimpse into the powerful capabilities of the Python Standard Library, particularly the `os` module, for interacting with the operating system and managing files and directories. For more detailed exploration, refer to the official documentation or comprehensive Python references.
