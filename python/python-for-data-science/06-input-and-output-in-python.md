# 06 Input and Output in Python

When working with Python, handling input and output operations is essential, especially when dealing with file operations. This section provides an overview of how to read from and write to files in Python. If you're focusing on numerical methods for file operations, you might skip this section initially and return to it later.

### Writing to a File

To write data to a file, you need to open it in write mode. Here's an example:

```python
# Open a file named 'example.txt' in write mode
file = open('example.txt', 'w')

# Check the type of the file object
print(type(file))  # Output: <class '_io.TextIOWrapper'>

# Write a string to the file
file.write('Hello, Python!\nWelcome to file handling.')

# Close the file
file.close()
```

### Reading from a File

To read data from a file, open it in read mode:

```python
# Open the file in read mode
file = open('example.txt', 'r')

# Read the content of the file
content = file.read()

# Print the content
print(content)  # Output: Hello, Python! Welcome to file handling.

# Close the file
file.close()
```

### Iterating Over a File

You can also iterate over each line in a file:

```python
# Open the file in read mode
file = open('example.txt', 'r')

# Iterate over each line in the file
for line in file:
    print(line.strip())  # Output each line without extra newline characters

# Close the file
file.close()
```

### File Modes

When opening files, you can specify different modes:

* **Read Only (`r`)**: Open a file for reading.
* **Write Only (`w`)**: Open a file for writing. This will create a new file or overwrite an existing file.
* **Append (`a`)**: Open a file for appending. Data is added to the end of the file.
* **Read and Write (`r+`)**: Open a file for both reading and writing.
* **Binary Mode (`b`)**: Use this mode for binary files, especially on Windows systems.

For more detailed information on input and output in Python, you can refer to the [official Python documentation](https://docs.python.org/tutorial/inputoutput.html).
