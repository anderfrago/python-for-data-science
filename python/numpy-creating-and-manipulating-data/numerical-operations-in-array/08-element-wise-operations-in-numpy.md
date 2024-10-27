# 08 Element-wise Operations in NumPy

### Basic Arithmetic with Scalars

You can perform arithmetic operations on each element of a NumPy array using scalars:

```python
import numpy as np

arr = np.array([5, 10, 15, 20])
print(arr + 2)  # Output: array([ 7, 12, 17, 22])
print(3**arr)   # Output: array([   243, 59049, 14348907, 3486784401])
```

These operations are element-wise, meaning they apply to each element individually:

```python
b = np.full(4, 3) + 2
print(arr - b)  # Output: array([0, 5, 10, 15])
print(arr * b)  # Output: array([15, 30, 45, 60])

j = np.arange(6)
print(3**(j + 2) - j)  # Output: array([ 9, 26, 79, 244, 725, 2186])
```

These operations are significantly faster than equivalent operations in pure Python:

```python
arr = np.arange(10000)
%timeit arr + 2  # Example: 10000 loops, best of 3: 25.1 µs per loop

lst = list(range(10000))
%timeit [i + 2 for i in lst]  # Example: 1000 loops, best of 3: 900 µs per loop
```

### Matrix Multiplication

Be cautious: element-wise multiplication is not the same as matrix multiplication:

```python
c = np.ones((3, 3))
print(c * c)  # Element-wise multiplication

# For matrix multiplication, use the dot function
print(c.dot(c))  # Matrix multiplication
```

## Exercises: Element-wise Operations

* **Perform Arithmetic Operations**: Try adding even-indexed elements with odd-indexed elements in an array.
* **Benchmarking**: Use `%timeit` to compare the performance of NumPy operations with their pure Python equivalents. **Generate Sequences**: Create sequences like `[3**0, 3**1, 3**2, 3**3, 3**4]` and explore expressions such as `a_j = 3^(2*j) - j`.

## Other Element-wise Operations

### Comparisons

You can perform element-wise comparisons between arrays:

```python
a = np.array([2, 4, 6, 8])
b = np.array([8, 4, 4, 8])
print(a == b)  # Output: array([False,  True, False,  True])
print(a > b)   # Output: array([False, False,  True, False])
```

To check if two arrays are identical:

```python
c = np.array([2, 4, 6, 8])
print(np.array_equal(a, b))  # Output: False
print(np.array_equal(a, c))  # Output: True
```

### Logical Operations

Logical operations can also be applied element-wise:

```python
a = np.array([True, True, False, False], dtype=bool)
b = np.array([True, False, True, False], dtype=bool)
print(np.logical_or(a, b))   # Output: array([ True,  True,  True, False])
print(np.logical_and(a, b))  # Output: array([ True, False, False, False])
```

### Transcendental Functions

NumPy provides functions for transcendental operations:

```python
a = np.arange(5)
print(np.sin(a))  # Output: array([ 0.        ,  0.84147098,  0.90929743,  0.14112001, -0.7568025 ])
print(np.log(a))  # Output: array([       -inf, 0.        , 0.69314718, 1.09861229, 1.38629436])
print(np.exp(a))  # Output: array([ 1.        ,  2.71828183,  7.3890561 , 20.08553692, 54.59815003])
```

## Handling Shape Mismatches

When performing operations, ensure arrays have compatible shapes:

````python
a = np.arange(4)
try:
    print(a)
    ```python
a = np.arange(4)
try:
    print(a + np.array([1, 2]))
except ValueError as e:
    print(e)  # Output: ValueError: operands could not be broadcast together with shapes (4,) (2,)
````

## Transposition

Transposing an array changes its shape by swapping its dimensions:

```python
a = np.triu(np.ones((3, 3)), 1)
print(a)
# Output:
# array([[0., 1., 1.],
#        [0., 0., 1.],
#        [0., 0., 0.]])

print(a.T)
# Output:
# array([[0., 0., 0.],
#        [1., 0., 0.],
#        [1., 1., 0.]])
```

### Transposition is a View

Transposing an array returns a view, not a copy:

```python
a = np.arange(9).reshape(3, 3)
a.T[0, 2] = 999
print(a.T)
# Output:
# array([[  0,   3, 999],
#        [  1,   4,   7],
#        [  2,   5,   8]])

print(a)
# Output:
# array([[  0,   1,   2],
#        [  3,   4,   5],
#        [999,   7,   8]])
```

## Linear Algebra

The `numpy.linalg` submodule provides basic linear algebra operations, such as solving linear systems and singular value decomposition. For more efficient routines, consider using `scipy.linalg`.

## Exercises: Other Operations

* **Explore np.allclose**: Check the documentation for `np.allclose`. When might this function be useful?
* **Explore np.triu and np.tril**: Look into the functions `np.triu` and `np.tril` to understand their applications.

## Basic Reductions

### Calculating Sums

You can calculate the sum of elements in an array:

````python
x = np.array([2, 4, 6, 8])
#### Sum by Rows and Columns

You can also compute sums along specific axes, which is useful for multi-dimensional arrays:

```python
x = np.array([[2, 2], [4, 4]])
print(x.sum(axis=0))  # Sum by columns (first dimension): Output: array([6, 6])
print(x[:, 0].sum(), x[:, 1].sum())  # Output: (6, 6)

print(x.sum(axis=1))  # Sum by rows (second dimension): Output: array([4, 8])
print(x[0, :].sum(), x[1, :].sum())  # Output: (4, 8)
````

### Higher Dimensions

The same concept applies to arrays with more dimensions:

```python
x = np.random.rand(2, 2, 2)
print(x.sum(axis=2)[0, 1])  # Example output: 1.14764...
print(x[0, 1, :].sum())     # Example output: 1.14764...
```

## Other Reductions

Reductions like finding minimums, maximums, and logical operations work similarly:

### Extremes

```python
x = np.array([2, 5, 3])
print(x.min())     # Output: 2
print(x.max())     # Output: 5
print(x.argmin())  # Index of minimum: Output: 0
print(x.argmax())  # Index of maximum: Output: 1
```

### Logical Operations

```python
print(np.all([True, True, False]))  # Output: False
print(np.any([True, True, False]))  # Output: True

# Matrix comparisons
a = np.zeros((100, 100))
print(np.any(a != 0))  # Output: False
print(np.all(a == a))  # Output: True

a = np.array([1, 2, 3, 2])
b = np.array([2, 2, 3, 2])
c = np.array([6, 4, 4, 5])
print(((a <= b) & (b <= c)).all())  # Output: True
```

### Statistics

NumPy provides statistical functions:

````python
```python
x = np.array([2, 4, 6, 8])
print(x.mean())  # Output: 5.0
print(x.std())   # Standard deviation: Output: 2.23606797749979
print(x.var())   # Variance: Output: 5.0
````

## Exercises: Basic Reductions

* **Sum of Elements**: Calculate the sum of elements in a 3x3 matrix along different axes.
* **Find Extremes**: Determine the minimum and maximum values in a random 4x4 matrix and their indices.
* **Logical Checks**: Create a boolean array and use `np.all` and `np.any` to check conditions.
* **Statistics**: Compute the mean, standard deviation, and variance of a 1D array.

## Broadcasting

Broadcasting is a powerful mechanism that allows NumPy to work with arrays of different shapes during arithmetic operations. It eliminates the need for explicit loops and makes code more concise and efficient.

### Basic Broadcasting

When performing operations on arrays of different shapes, NumPy automatically expands the smaller array to match the shape of the larger one:

```python
a = np.array([1, 2, 3])
b = np.array([[10], [20], [30]])
print(a + b)
# Output:
# array([[11, 12, 13],
#        [21, 22, 23],
#        [31, 32, 33]])
```

### Broadcasting Rules

1. **Trailing Dimensions**: If the arrays have different numbers of dimensions, the shape of the smaller array is padded with ones on its left side.
2. **Size of 1**: Arrays with a size of 1 along a particular dimension can be stretched to match the other array's size in that dimension.

### Practical Example

Broadcasting is useful for operations like centering data:

```python
X = np.random.random((10, 3))
X_mean = X.mean(axis=0)
X_centered = X - X_mean
```

## Exercises: Broadcasting

*   **Array Expansion**: Use broadcasting to add a 1D array to each row of a 2D array.

    ```python
    a = np.array([1, 2, 3])
    b = np.array([[10], [20], [30]])
    result = a + b
    print(result)
    # Output:
    # array([[11, 12, 13],
    #        [21, 22, 23],
    #        [31, 32, 33]])
    ```
*   **Data Normalization**: Normalize a dataset by subtracting the mean and dividing by the standard deviation using broadcasting.

    ```python
    X = np.random.random((10, 3))
    X_mean = X.mean(axis=0)
    X_std = X.std(axis=0)
    X_normalized = (X - X_mean) / X_std
    print(X_normalized)
    ```
*   **Element-wise Operations**: Perform element-wise operations on arrays of different shapes.

    ```python
    a = np.array([1, 2, 3])
    b = np.array([[1], [2], [3]])
    result = a * b
    print(result)
    # Output:
    # array([[1, 2, 3],
    #        [2, 4, 6],
    #        [3, 6, 9]])
    ```

## Conclusion

Broadcasting is a powerful feature in NumPy that simplifies array operations by automatically expanding smaller arrays to match the shape of larger ones. This allows for efficient and concise code, especially when dealing with large datasets or complex mathematical operations. By understanding and utilizing broadcasting, you can perform a wide range of operations without the need for explicit loops, leading to cleaner and more efficient code.
