# 10 advance matrix operations



**4.3.1 Diverse Data Types**

**Type Conversion**

When combining different data types, the more complex type prevails:

```python
import numpy as np
result = np.array([1, 2, 3]) + 1.5
print(result)  # Output: array([2.5, 3.5, 4.5])
```

Assignments do not alter the data type:

```python
a = np.array([1, 2, 3])
print(a.dtype)  # Output: dtype('int64')
a[0] = 1.9  # The float is truncated to an integer
print(a)  # Output: array([1, 2, 3])
```

**Forced Type Conversion:**

```python
a = np.array([1.7, 1.2, 1.6])
b = a.astype(int)  # Converts to integer, truncating values
print(b)  # Output: array([1, 1, 1])
```

**Rounding Values:**

```python
a = np.array([1.2, 1.5, 1.6, 2.5, 3.5, 4.5])
b = np.around(a)
print(b)  # Output: array([1., 2., 2., 2., 4., 4.])
c = np.around(a).astype(int)
print(c)  # Output: array([1, 2, 2, 2, 4, 4])
```

### Data Types and Casting in NumPy

**Data Types** in NumPy represent the kind of data stored in an array. Understanding data types is crucial for efficient memory usage and accurate calculations.

**Casting** is the process of converting one data type to another. NumPy provides various methods for casting.

#### Mixed-Type Operations

When performing operations on arrays with different data types, NumPy follows a rule: the **"largest" type wins**. This means the result will have the data type of the array with the highest precision.

```python
import numpy as np

arr = np.array([1, 2, 3]) + 1.5
print(arr)  # Output: [2.5 3.5 4.5]
```

In this example, `arr` is an integer array, but adding `1.5` (a float) results in a float array because floats have higher precision.

**Note:** Assigning a value to an array element does not change the array's overall data type.

#### Forced Casting

To explicitly cast an array to a different data type, use the `astype()` method.

```python
arr = np.array([1.7, 1.2, 1.6])
arr_int = arr.astype(int)
print(arr_int)  # Output: [1 1 1]
```

Here, the `astype(int)` method truncates the decimal part of each element.

#### Rounding

To round elements to the nearest integer, use the `np.around()` function. You can then cast the result to an integer data type if needed.

```python
arr = np.array([1.2, 1.5, 1.6, 2.5, 3.5, 4.5])
rounded_arr = np.around(arr)
print(rounded_arr)  # Output: [1. 2. 2. 2. 4. 4.]
```

#### Data Type Sizes

NumPy offers various integer and floating-point data types with different sizes. The size determines the range of values that can be stored.

**Integers:**

* **Signed:** `np.int8`, `np.int16`, `np.int32`, `np.int64`
* **Unsigned:** `np.uint8`, `np.uint16`, `np.uint32`, `np.uint64`

**Floating-Point:**

* `np.float32`, `np.float64`

**Complex:**

* `np.complex64`, `np.complex128`

**Example:**

```python
print(np.iinfo(np.int32).max)  # Output: 2147483647
```

#### Choosing Data Types

When selecting a data type, consider the following factors:

* **Range of values:** Ensure the data type can accommodate the expected values.
* **Memory usage:** Smaller data types require less memory.
* **Performance:** Some operations may be faster with certain data types.

**Note:** In most cases, using the default `np.int64` and `np.float64` data types is sufficient. Only consider using smaller data types when memory or performance is a critical concern.

### Structured Data in NumPy

This section explores structured data, a powerful way to organize diverse data within NumPy arrays.

**Creating Structured Arrays:**

Structured arrays resemble tables with named columns of different data types. Here's how to create them:

* Define a compound data type with field names and their corresponding data types.
* Use `np.zeros` to create the array with the desired shape.

```python
samples = np.zeros((6,), dtype=[('sensor_code', 'S4'), ('position', float), ('value', float)])
print(samples.dtype.names)  # Output: ('sensor_code', 'position', 'value')
```

**Accessing Fields:**

* Access individual fields by their names using square brackets:

```python
print(samples['sensor_code'])   # Array of sensor codes
print(samples['value'])        # Array of values
```

* Access a single element's fields using its index:

```python
print(samples[0])  # Tuple containing all fields for the first element
```

* Modify field values directly:

```python
samples[0]['sensor_code'] = 'TAU'  # Update sensor code of the first element
```

**Advanced Operations:**

* Select multiple fields at once:

```python
positions_values = samples[['position', 'value']]  # Array containing position and value columns
```

* Use boolean indexing to filter based on field values:

```python
alfa_samples = samples[samples['sensor_code'] == b'ALFA']  # Select rows with sensor code 'ALFA'
```

**Masked Arrays (Bonus):**

* These arrays handle missing data explicitly using a mask alongside the data.
* Missing data is represented by `NaN` (Not a Number) or masked out completely.
* Masked arrays enable efficient calculations while considering missing values.

**Best Practices:**

* Use descriptive variable names for clarity.
* Follow consistent code formatting (spaces around operators, etc.).
* Refer to style guides like PEP 8 for improved code readability and maintainability.

**Note:** This summary focuses on structured data and masked arrays. NumPy offers other specialized array types for specific use cases.
