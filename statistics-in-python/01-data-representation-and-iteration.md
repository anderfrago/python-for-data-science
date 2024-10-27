# 01 data representation and iteration

### Data Organization: Tables and DataFrames

In statistics, we often analyze data sets containing multiple observations (samples) described by various characteristics (features). Imagine this data as a two-dimensional table, much like a spreadsheet. This table has:

* **Columns:** Represent the different features or attributes of the data points.
* **Rows:** Each row represents a single observation or sample.

For instance, consider a dataset (available in `examples/brain_size.csv`) containing brain size and weight measurements for individuals alongside their IQ scores. This data can be visualized as a table with columns for:

| Column Name | Description           |
| ----------- | --------------------- |
| Gender      | Male or Female        |
| FSIQ        | Full-Scale IQ Score   |
| VIQ         | Verbal IQ Score       |
| PIQ         | Performance IQ Score  |
| Weight      | Weight in kilograms   |
| Height      | Height in centimeters |
| MRI\_Count  | MRI scan voxel count  |

### Introducing pandas DataFrames

The `pandas` library provides a powerful data structure called a DataFrame, which acts as the Python equivalent of a spreadsheet table. Here's why DataFrames are a preferred choice over standard NumPy arrays for data analysis:

* **Named Columns:** DataFrames have named columns, making data interpretation and manipulation more intuitive.
* **Mixed Data Types:** Unlike NumPy arrays, DataFrames can hold columns with different data types (e.g., strings, numbers).
* **Selection and Operations:** DataFrames offer sophisticated mechanisms for selecting and manipulating data subsets based on specific criteria.

### Creating DataFrames

There are two primary ways to create DataFrames:

**1. Reading from Files:**

* **CSV Files:** DataFrames can be easily read from comma-separated values (CSV) files using the `pandas.read_csv` function. In our example, the separator is a semicolon (`;`).

```python
import pandas as pd

# Read data from CSV file
data = pd.read_csv('examples/brain_size.csv', sep=';', na_values=".")
```

**2. Creating from Arrays:**

* **Combining Arrays:** You can combine multiple NumPy arrays into a DataFrame by treating them as a dictionary of one-dimensional series.

```python
import numpy as np
import pandas as pd

# Create sample arrays
t = np.linspace(-6, 6, 20)
sin_t = np.sin(t)
cos_t = np.cos(t)

# Create DataFrame from arrays
data = pd.DataFrame({'t': t, 'sin': sin_t, 'cos': cos_t})
```

### Working with DataFrames

DataFrames offer various functionalities for exploring and manipulating your data:

* **Shape:** Check the number of rows and columns using `data.shape`.
* **Columns:** Access columns by name (e.g., `data['Gender']`).
* **Selection:** Select rows or columns based on conditions.
* **Summary Statistics:** Calculate summary statistics like mean and standard deviation using methods like `describe()`.
* **Grouping:** Group data based on categorical variables using `groupby`. This allows you to perform operations like calculating means or counts for each group separately.

```python
# Get average VIQ for the entire population
data['VIQ'].mean()

# Count males and females
data['Gender'].value_counts()

# Group by gender and calculate mean VIQ
groupby_gender = data.groupby('Gender')
print(groupby_gender['VIQ'].mean())
```

### Data Visualization with pandas

pandas offers basic plotting tools (`pandas.plotting`) that leverage Matplotlib behind the scenes. You can create visualizations like scatter matrices to explore relationships between variables:

```python
from pandas.plotting import scatter_matrix

# Scatter matrix for weight, height, and MRI count
scatter_matrix(data[['Weight', 'Height', 'MRI_Count']])

# Scatter matrix for IQ scores
scatter_matrix(data[['PIQ', 'VIQ', 'FSIQ']])
```

### Exercise

1. Explore the `data.describe()` method to get an overview of the data's statistical properties.
2. Analyze the distribution of VIQ scores across genders using the `groupby` function. Does it suggest the presence of sub-populations?
3. Try creating scatter matrices to visualize relationships between different variables, focusing on males and females separately. Does gender seem to influence these relationships?
