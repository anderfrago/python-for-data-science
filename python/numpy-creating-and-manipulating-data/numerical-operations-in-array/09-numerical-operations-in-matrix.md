# 09 numerical operations in matrix

#### Numerical Operations in Matrices

Broadcasting is a powerful feature in NumPy that allows you to perform operations on arrays of different shapes. This is particularly useful in network-based problems. For instance, if you want to compute the distance from the origin for points in a 5x5 grid, you can do the following:

```python
x, y = np.arange(5), np.arange(5)[:, np.newaxis]
distance = np.sqrt(x ** 2 + y ** 2)
print(distance)
# Output:
# array([[0.        , 1.        , 2.        , 3.        , 4.        ],
#        [1.        , 1.41421356, 2.23606798, 3.16227766, 4.12310563],
#        [2.        , 2.23606798, 2.82842712, 3.60555128, 4.47213595],
#        [3.        , 3.16227766, 3.60555128, 4.24264069, 5.        ],
#        [4.        , 4.12310563, 4.47213595, 5.        , 5.65685425]])
```

To visualize this in color:

```python
import matplotlib.pyplot as plt
plt.pcolor(distance)
plt.colorbar()
```

Using `np.ogrid` is beneficial for grid-based calculations:

```python
x, y = np.ogrid[0:5, 0:5]
distance = np.sqrt(x ** 2 + y ** 2)
```

For cases where broadcasting isn't applicable, `np.mgrid` can be used to create index-filled arrays:

```python
x, y = np.mgrid[0:4, 0:4]
```

#### Array Shape Manipulation

**Flattening**

Flattening an array converts it into a 1D array:

```python
a = np.array([[1, 2, 3], [4, 5, 6]])
print(a.ravel())  # Output: array([1, 2, 3, 4, 5, 6])
```

**Reshaping**

Reshaping is the reverse of flattening:

```python
b = a.ravel()
b = b.reshape
b = b.reshape((2, 3))
print(b)
# Output:
# array([[1, 2, 3],
#        [4, 5, 6]])
```

You can also use `-1` to let NumPy infer the dimension:

```python
a.reshape((2, -1))
# Output:
# array([[1, 2, 3],
#        [4, 5, 6]])
```

**Note**: `ndarray.reshape` may return a view or a copy of the array.

**Adding a Dimension**

You can add a new axis to an array using `np.newaxis`:

```python
z = np.array([1, 2, 3])
print(z[:, np.newaxis])
# Output:
# array([[1],
#        [2],
#        [3]])
```

**Dimension Shuffling**

You can rearrange the dimensions of an array using `transpose`:

```python
a = np.arange(4*3*2).reshape(4, 3, 2)
b = a.transpose(1, 2, 0)
print(b.shape)  # Output: (3, 2, 4)
```

**Resizing**

The size of an array can be changed with `ndarray.resize`:

```python
a = np.arange(4)
a.resize((8,))
print(a)
# Output: array([0, 1, 2, 3, 0, 0, 0, 0])
```

**Warning**: You cannot resize an array that is referenced elsewhere.

#### Exercises: Shape Manipulations

* Explore the documentation for `reshape`, especially the notes on copies and views.
* Use `flatten` as an alternative to `ravel`. Investigate the differences between them.
* Experiment with transposing arrays to shuffle dimensions.

#### Data Sorting

**Sorting Along an Axis**

You can sort an array along a specific axis:

```python
a = np.array([[4, 3, 5], [1, 2, 1]])
b = np.sort(a, axis=1)
print(b)
# Output:
# array([[3, 4, 5],
#        [1, 1, 2]])
```

**In-place Sorting**

You can sort an array in place:

```python
a.sort(axis=1)
print(a)

# Output:
# array([[3, 4, 5],
#        [1, 1, 2]])
```

**Sorting with Fancy Indexing**

You can use `argsort` to get the indices that would sort an array:

```python
a = np.array([4, 3, 1, 2])
j = np.argsort(a)
print(j)  # Output: array([2, 3, 1, 0])
print(a[j])  # Output: array([1, 2, 3, 4])
```

**Finding Extremes**

To find the indices of the maximum and minimum values:

```python
a = np.array([4, 3, 1, 2])
j_max = np.argmax(a)
j_min = np.argmin(a)
print(j_max, j_min)  # Output: (0, 2)
```

#### Exercises: Sorting

* Test both in-place and out-of-place sorting.
* Create arrays with different data types and sort them.
* Use `np.all` or `np.array_equal` to verify sorting results.
* Use `np.random.shuffle` to generate sortable arrays quickly.
* Combine `ravel`, `sort`, and `reshape` for complex sorting tasks.
* Explore the `axis` keyword in sorting and apply it to previous exercises.

#### Summary

**Key Concepts to Get Started**

* **Array Creation**: Use functions like `array`, `arange`, `ones`, and `zeros`.
* **Shape and Slicing**: Understand array shapes with `array.shape` and use slicing to view different parts of an array, e.g., `array[::2]`.
* **Reshaping and Flattening**: Adjust array shapes with `reshape` or flatten them with `ravel`.
* **Element Selection and Modification**: Use masks to select and modify array elements, e.g., `a[a < 0] = 0`.
* **Matrix Operations**: Perform operations like finding the mean or maximum with functions like `matrix.max()` or `matrix.mean()`.
* **Advanced Techniques**: Master integer array indexing and broadcasting for complex operations.

**Quick Read**

If you're eager to dive into the SciPy ecosystem, you can skip ahead to the next chapter on Matplotlib for plotting. However, make sure to revisit this chapter to solidify your understanding and complete additional exercises.
