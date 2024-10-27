# 03 Control Flow in Python

Control flow statements determine the order in which code is executed. Let's explore some of these statements with new examples and exercises.

## if/elif/else

These statements allow you to execute code based on conditions.

```python
>>> if 3 * 3 == 9:
...     print('Correct!')
...
Correct!
```

Blocks of code are defined by their indentation. In Python, indentation is crucial and must be consistent.

**Example:**

```python
>>> number = 5
>>> if number < 3:
...     print('Small')
... elif number == 5:
...     print('Equal')
... else:
...     print('Large')
Equal
```

**Exercise:** Write a script named `check_number.py` with the above logic and run it using `python check_number.py`.

## for/range

Use `for` loops to iterate over a sequence of numbers or items.

**Example with range:**

```python
>>> for i in range(3):
...     print(i)
0
1
2
```

**Example with values:**

```python
>>> for animal in ('cat', 'dog', 'bird'):
...     print('I have a %s' % animal)
I have a cat
I have a dog
I have a bird
```

## while/break/continue

`while` loops execute as long as a condition is true. Use `break` to exit the loop and `continue` to skip to the next iteration.

**Example:**

```python
>>> x = 0
>>> while x < 5:
...     if x == 3:
...         break
...     print(x)
...     x += 1
0
1
2
```

**Example with continue:**

```python
>>> numbers = [1, 2, 0, 4]
>>> for num in numbers:
...     if num == 0:
...         continue
...     print(10 / num)
10.0
5.0
2.5
```

## Conditional Expressions

Conditional expressions allow you to evaluate conditions directly within your code.

* **False Evaluations:** These include any number equal to zero (e.g., `0`, `0.0`, `0+0j`), empty containers (e.g., `[]`, `()`, `{}`, `''`), `False`, and `None`.
* **True Evaluations:** Everything else is considered true.

**Examples:**

```python
>>> 2 == 2.0
True
>>> 2 is 2.0
False
>>> a = 2
>>> b = 2
>>> a is b
True
```

* **Membership Testing:**

```python
>>> collection = [1, 2, 3]
>>> 2 in collection
True
>>> 5 in collection
False
```

If `collection` is a dictionary, the `in` operator checks for keys.

## Advanced Iteration

Python allows you to iterate over various sequences, such as strings, lists, dictionary keys, and file lines.

**Example: Iterating Over a String:**

```python
>>> vowels = 'aeiou'
>>> for char in 'education':
...     if char in vowels:
...         print(char)
e
u
a
i
o
```

**Example: Iterating Over Words in a Sentence:**

```python
>>> sentence = "Python is fun"
>>> for word in sentence.split():
...     print(word)
Python
is
fun
```

Python's ability to iterate over objects directly, rather than just indices, makes code more readable and concise.

**Tracking Enumeration:**

To iterate over a sequence while keeping track of the index, you can use `enumerate`.

**Example:**

```python
>>> items = ('apple', 'banana', 'cherry')
>>> for index, item in enumerate(items):
...     print((index, item))
(0, 'apple')
(1, 'banana')
(2, 'cherry')
```

## Looping Over a Dictionary

When iterating over a dictionary, you can access both keys and values, and using `sorted()` can help maintain a consistent order based on keys.

**Example:**

```python
>>> data = {'x': 10, 'y': 20, 'z': 30}
>>> for key, value in sorted(data.items()):
...     print('Key: %s has value: %s' % (key, value))
Key: x has value: 10
Key: y has value: 20
Key: z has value: 30
```

## List Comprehensions

Instead of creating a list by looping, Python offers a more concise way to generate lists using list comprehensions. This feature allows for a more readable and expressive syntax.

**Example:**

```python
>>> squares = [x**2 for x in range(5)]
>>> squares
[0, 1, 4, 9, 16]
```

## Exercise

**Calculate the Decimals of Pi Using Wallis' Formula:**

Wallis' formula is an infinite product that can be used to approximate π. Implement a Python script to calculate an approximation of π using this formula. Here's a basic structure to get you started:

```python
def calculate_pi(n_terms):
    pi_over_2 = 1.0
    for n in range(1, n_terms + 1):
        pi_over_2 *= (4 * n**2) / (4 * n**2 - 1)
    return pi_over_2 * 2

# Example usage
n_terms = 1000
approx_pi = calculate_pi(n_terms)
print(f"Approximation of π using {n_terms} terms: {approx_pi}")
```

This script defines a function `calculate_pi` that takes the number of terms `n_terms` as an argument and returns an approximation of π. The more terms you use, the closer the approximation will be to the actual value of π.
