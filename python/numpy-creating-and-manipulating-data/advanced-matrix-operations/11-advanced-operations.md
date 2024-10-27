# 11 advanced operations

### Polynomials in NumPy

NumPy provides tools for working with polynomials in various bases.

**Basic Polynomials:**

* The `np.poly1d` class represents polynomials in the standard basis (powers of x).
* Create a polynomial with coefficients:

```python
p = np.poly1d([3, 2, -1])  # Represents 3x^2 + 2x - 1
```

* Evaluate the polynomial at a specific value:

```python
print(p(0))  # Output: -1 (evaluates 3 * 0^2 + 2 * 0 - 1)
```

* Find the roots of the polynomial:

```python
print(p.roots)  # Output: array([-1.,  0.33333333])
```

* Get the degree of the polynomial (highest power of x):

```python
print(p.order)  # Output: 2
```

**Fitting Polynomials to Data:**

* Use `np.polyfit` to fit a polynomial of a given degree to a set of data points.
* Example: Fit a cubic polynomial (degree 3) to cosine data with noise:

```python
x = np.linspace(0, 1, 20)
y = np.cos(x) + 0.3 * np.random.rand(20)
p = np.poly1d(np.polyfit(x, y, 3))
```

* Plot the original data and the fitted polynomial.

**Chebyshev Polynomials:**

* `np.polynomial.Chebyshev` class represents polynomials in the Chebyshev basis.
* Coefficients may be provided in a different order than the standard basis.
* Example: Fit a Chebyshev polynomial of degree 90 to noisy cosine data in the range \[-1, 1]:

```python
x = np.linspace(-1, 1, 2000)
y = np.cos(x) + 0.3 * np.random.rand(2000)
p = np.polynomial.Chebyshev.fit(x, y, 90)
```

* Plot the original data and the fitted Chebyshev polynomial.

### Uploading Data Files

**Text Files:**

* Use `np.loadtxt` to load data from text files with delimiter-separated values.
* Example: Load data from "poblaciones.txt" and drop unnecessary columns:

```python
data = np.loadtxt('data/poblaciones.txt', skiprows=1, usecols=(1, 2))  # Skip header, select columns 2 & 3
print(data)

np.savetxt('pop2.txt', data)  # Save the filtered data
```

**Images:**

* Use `matplotlib.pyplot.imread` to read image data.
* The output is a 3D array representing color channels.
* Manipulate and save images using Matplotlib functions.

**NumPy Binary Format (npy):**

* NumPy offers its own efficient binary format for storing arrays:

```python
datos = np.ones((3, 3))
np.save('pop.npy', datos)

data3 = np.load('pop.npy')  # Load the saved array
```

**Other File Formats:**

* NumPy doesn't natively handle all formats. There are external libraries for formats like HDF5, NetCDF, and Matlab.

### Exercise: Text Data Files

Write a Python script that:

1. Loads data from "poblaciones.txt".
2. Drops the first and last columns.
3. Saves the resulting data (5 rows, 2 columns) to "pop2.txt".

**Hint:** Use `skiprows` and `usecols` arguments in `np.loadtxt`.
