# 03 Understanding Basic Data Types in NumPy

NumPy arrays can store data in various types, which affects how the data is represented and manipulated in memory. The choice of data type can influence both the performance and the memory usage of your computations.

## Common Data Types in NumPy

*   **Integer and Floating-Point Types**:

    * When you create an array, NumPy automatically detects the data type based on the input values.

    ```python
    import numpy as np

    # Integer array
    a = np.array([1, 2, 3])
    print(a.dtype)  # Output: dtype('int64')

    # Floating-point array
    b = np.array([1., 2., 3.])
    print(b.dtype)  # Output: dtype('float64')
    ```
*   **Specifying Data Types**:

    * You can explicitly specify the data type when creating an array, which can be useful for ensuring consistency or optimizing memory usage.

    ```python
    # Specifying float data type
    c = np.array([1, 2, 3], dtype=float)
    print(c.dtype)  # Output: dtype('float64')
    ```
*   **Default Data Type**:

    * The default data type for many NumPy functions, such as `ones`, is floating-point.

    ```python
    # Default data type is float64
    a = np.ones((3, 3))
    print(a.dtype)  # Output: dtype('float64')
    ```

## Other Data Types

*   **Complex Numbers**:

    * NumPy supports complex numbers, which are useful in certain scientific and engineering applications.

    ```python
    # Complex number array
    d = np.array([1+2j, 3+4j, 5+6j])
    print(d.dtype)  # Output: dtype('complex128')
    ```
*   **Boolean Values**:

    * Arrays can also store boolean values, which are useful for logical operations and masking.

    ```python
    # Boolean array
    e = np.array([True, False, False, True])
    print(e.dtype)  # Output: dtype('bool')
    ```
*   **Strings**:

    * NumPy can handle arrays of strings, with the data type indicating the maximum string length.

    ````python
    # String array
    f = np
    ```python
    # String array
    f = np.array(['Bonjour', 'Hello', 'Hallo'])
    print(f.dtype)  # Output: dtype('S7') indicating strings with max length 7
    ````

## Additional Data Types

* **Integer Types**:
  * `int32` and `int64`: These are standard integer types with 32-bit and 64-bit precision, respectively.
  * `uint32` and `uint64`: These are unsigned integer types, meaning they can only represent non-negative numbers, with 32-bit and 64-bit precision.

NumPy's flexibility with data types allows you to choose the most appropriate type for your data, balancing between precision and memory efficiency. This is particularly important in large-scale scientific computations where performance and resource usage are critical.
