# 02 Basic Data Types

## Numeric Types

Python offers several numeric and scalar types:

1.  **Integers**

    ```python
    >>> 2 + 3
    5
    >>> num = 7
    >>> type(num)
    <class 'int'>
    ```
2.  **Floats**

    ```python
    >>> pi = 3.14
    >>> type(pi)
    <class 'float'>
    ```
3.  **Complex Numbers**

    ```python
    >>> z = 2.0 + 3.0j
    >>> z.real
    2.0
    >>> z.imag
    3.0
    >>> type(2.0 + 0j)
    <class 'complex'>
    ```
4.  **Booleans**

    ```python
    >>> 5 < 2
    False
    >>> result = (5 < 2)
    >>> result
    False
    >>> type(result)
    <class 'bool'>
    ```

Python can serve as a substitute for a basic calculator with operations like addition, subtraction, multiplication, division, and modulus:

```python
>>> 9 * 2
18
>>> 3**4
81
>>> 10 % 4
2
```

Type Conversion (Casting):

```python
>>> float(2)
2.0
```

Integer Division

In Python 2:

```python
>>> 5 / 2
2
```

In Python 3:

```python
>>> 5 / 2
2.5
```

To ensure consistent behavior, use floats:

```python
>>> 5 / 2.0
2.5
>>> x = 5
>>> y = 2
>>> x / y  # In Python 2
2
>>> x / float(y)
2.5
```

To always use Python 3 division behavior:

```python
>>> from __future__ import division
>>> 5 / 2
2.5
```

For explicit integer division, use `//`:

```python
>>> 5 // 2
2
```

## Containers

Python provides various efficient container types for storing collections of objects.

**Lists**\
A list is an ordered collection of items, which can be of different types:

```python
>>> fruits = ['apple', 'banana', 'cherry', 'date', 'elderberry']
>>> type(fruits)
<class 'list'>
```

**Indexing**: Access individual elements in the list:

```python
>>> fruits[1]
'banana'
```

**Negative Indexing**: Count from the end:

```python
>>> fruits[-1]
'elderberry'
>>> fruits[-3]
'cherry'
```

**Slicing**: Obtain sublists:

```python
>>> fruits[1:3]
['banana', 'cherry']
```

**Stride in Slicing**:

```python
>>> fruits[::2]
['apple', 'cherry', 'elderberry']
```

Lists are mutable, meaning they can be changed:

```python
>>> fruits[0] = 'apricot'
>>> fruits
['apricot', 'banana', 'cherry', 'date', 'elderberry']
```

For collections of numeric data of the same type, using the `array` type from the `numpy` module is often more efficient. NumPy arrays allow for faster operations due to their memory layout and the use of optimized C functions.

Python provides numerous functions for modifying and querying lists. Here are some examples:

**Adding and Removing Items**:

```python
>>> fruits.append('fig')
>>> fruits
['apricot', 'banana', 'cherry', 'date', 'elderberry', 'fig']
>>> fruits.pop()
'fig'
>>> fruits
['apricot', 'banana', 'cherry', 'date', 'elderberry']
```

**Reversing a List**:

```python
>>> reversed_fruits = fruits[::-1]
>>> reversed_fruits
['elderberry', 'date', 'cherry', 'banana', 'apricot']
```

**Concatenating and Repeating Lists**:

```python
>>> fruits + ['grape', 'honeydew']
['apricot', 'banana', 'cherry', 'date', 'elderberry', 'grape', 'honeydew']
>>> fruits * 2
['apricot', 'banana', 'cherry', 'date', 'elderberry', 'apricot', 'banana', 'cherry', 'date', 'elderberry']
```

**Sorting Lists**:

You can sort a list in place or create a new sorted list:

*   **In-place Sorting**: This modifies the original list.

    ```python
    >>> fruits.sort()
    >>> fruits
    ['apricot', 'banana', 'cherry', 'date', 'elderberry']
    ```
*   **Creating a New Sorted List**: This leaves the original list unchanged.

    ```python
    >>> sorted_fruits = sorted(fruits, reverse=True)
    >>> sorted_fruits
    ['elderberry', 'date', 'cherry', 'banana', 'apricot']
    >>> fruits
    ['apricot', 'banana', 'cherry', 'date', 'elderberry']
    ```

**Other Common List Operations**:

*   **Finding the Length**:

    ```python
    >>> len(fruits)
    5
    ```
*   **Checking for Existence**:

    ```python
    >>> 'banana' in fruits
    True
    >>> 'fig' in fruits
    False
    ```
*   **Counting Occurrences**:

    ```python
    >>> fruits.count('banana')
    1
    ```
*   **Finding the Index of an Item**:

    ```python
    >>> fruits.index('cherry')
    2
    ```

**Tuples**:

Tuples are similar to lists but are immutable, meaning they cannot be changed after creation. They are often used to represent fixed collections of items.

```python
>>> point = (3, 4)
>>> type(point)
<class 'tuple'>
```

**Accessing Tuple Elements**:

```python
>>> point[0]
3
```

**Unpacking Tuples**:

```python
>>> x, y = point
>>> x
3
>>> y
4
```

**Sets**:

Sets are unordered collections of unique items. They are useful for membership testing and eliminating duplicate entries.

```python
>>> basket = {'apple', 'banana', 'cherry', 'apple'}
>>> basket
{'apple', 'banana', 'cherry'}
```

**Set Operations**:

*   **Intersection**:

    ```python
    >>> a & b
    {3}
    ```
*   **Difference**:

    ```python
    >>> a - b
    {1, 2}
    ```
*   **Symmetric Difference**:

    ```python
    >>> a ^ b
    {1, 2, 4, 5}
    ```

**Dictionaries**:

Dictionaries are collections of key-value pairs. They are unordered and mutable, allowing for fast retrieval of values based on keys.

```python
>>> phonebook = {'Alice': '123-4567', 'Bob': '987-6543'}
>>> type(phonebook)
<class 'dict'>
```

**Accessing and Modifying Dictionary Entries**:

*   **Accessing Values**:

    ```python
    >>> phonebook['Alice']
    '123-4567'
    ```
*   **Adding or Updating Entries**:

    ```python
    >>> phonebook['Charlie'] = '555-0000'
    >>> phonebook
    {'Alice': '123-4567', 'Bob': '987-6543', 'Charlie': '555-0000'}
    ```
*   **Removing Entries**:

    ```python
    >>> del phonebook['Bob']
    >>> phonebook
    {'Alice': '123-4567', 'Charlie': '555-0000'}
    ```

**Dictionary Methods**:

*   **Keys, Values, and Items**:

    ```python
    >>> phonebook.keys()
    dict_keys(['Alice', 'Charlie'])
    >>> phonebook.values()
    dict_values(['123-4567', '555-0000'])
    >>> phonebook.items()
    dict_items([('Alice', '123-4567'), ('Charlie', '555-0000')])
    ```
*   **Checking for Key Existence**:

    ```python
    >>> 'Alice' in phonebook
    True
    >>> 'Bob' in phonebook
    False
    ```

These basic data types and operations form the foundation of Python programming, allowing you to store, manipulate, and retrieve data efficiently. As you become more familiar with these concepts, you'll be able to tackle more complex programming tasks and data structures.
