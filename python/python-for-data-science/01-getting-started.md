# 01 Getting Started

To begin, open the IPython shell, which is an enhanced interactive Python environment, by typing "ipython" in a Linux/Mac terminal or in the Windows command prompt.

If IPython is not installed on your system, you can use other Python shells, such as the basic Python shell by typing "python" in a terminal, or the IDLE interpreter. However, we recommend using the IPython shell due to its advanced features, particularly beneficial for interactive scientific computing.

Once the interpreter is running, enter the following command:

```python
>>> print("Hello, world!")
```

This will display the message "Hello, world!" on the screen. Congratulations, you've just executed your first Python command!

To continue, try the following sequence of commands:

```python
>>> a = 3
>>> b = 2 * a
>>> type(b)
<class 'int'>
>>> print(b)
6
>>> a * b
18
>>> b = 'hello'
>>> type(b)
<class 'str'>
>>> b + b
'hellohello'
>>> 2 * b
'hellohello'
```

In the example above, two variables, `a` and `b`, are defined. Notice that the type of `a` is not specified before assigning it a value. In contrast, in C, you would write:

```c
int a = 3;
```

Moreover, the type of a variable in Python can change. Initially, `b` is an integer, but it becomes a string when assigned the value 'hello'. Python natively supports integer operations (e.g., `b = 2 * a`) and some string operations like addition and multiplication, which correspond to concatenation and repetition, respectively.
