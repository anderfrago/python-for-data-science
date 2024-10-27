# 04 multiple regression

### Multiple Regression and Analysis of Variance

#### 1. Multiple Regression

Multiple regression extends simple linear regression to include multiple predictor variables (independent variables). This allows us to model how a dependent variable is influenced by a combination of factors.

**Example: Predicting Sepal Width**

Consider predicting sepal width using petal length and species as predictors.

```python
import pandas as pd
import statsmodels.formula.api as smf

# Read data
data = pd.read_csv('examples/iris.csv')

# Fit the model
model = smf.ols('sepal_width ~ name + petal_length', data).fit()

# Print model summary
print(model.summary())
```

**Interpretation:**

* **Coefficients:** The coefficients represent the change in the dependent variable (sepal width) for a unit increase in the corresponding predictor variable, holding other predictors constant.
* **P-values:** Assess the statistical significance of each predictor variable.
* **R-squared:** Indicates the proportion of variance in the dependent variable explained by the model.

#### 2. Analysis of Variance (ANOVA)

ANOVA tests the overall significance of the model, determining if the predictors collectively explain a significant amount of variation in the dependent variable.

**Example:**

To test if the effect of species on sepal width is significant after accounting for petal length, we can perform an F-test on the model coefficients:

```python
# F-test for the effect of species
f_statistic, p_value = model.f_test([0, 1, -1, 0])
print("F-statistic:", f_statistic)
print("P-value:", p_value)
```

#### 3. Post-hoc Comparisons

If the overall model is significant, you can conduct post-hoc comparisons to identify which specific predictors are significantly different.

**Example:**

To compare the sepal width of versicolor and virginica after controlling for petal length, you can use the model coefficients and their standard errors to calculate t-statistics and p-values.

#### Exercise

1. **Add more predictors:** Include additional features (e.g., sepal length) in the model and analyze their significance.
2. **Interaction terms:** Explore the effects of interactions between predictors by including interaction terms (e.g., `name*petal_length`) in the model.
3. **Model validation:** Use techniques like cross-validation to assess the model's performance on new data.

#### 4. Visualization with Seaborn

Seaborn provides convenient functions for visualizing data and statistical relationships.

**Example: Pairplot**

Create a scatterplot matrix to visualize the relationships between variables:

```python
import seaborn as sns

sns.pairplot(data, vars=['WAGE', 'AGE', 'EDUCATION'], kind='reg')
```

**Customization:**

* **Hue:** Use `hue` to color scatterplots based on a categorical variable (e.g., `SEX`).
* **Regression lines:** The `kind='reg'` argument adds regression lines to the scatterplots.

**Remember:** Seaborn's default settings can be customized to match your preferred style. Use `plt.rcdefaults()` to reset to Matplotlib defaults.

By combining multiple regression analysis with visualization techniques, you can gain deeper insights into the relationships between variables and interpret the results more effectively.

### More visualization: seaborn for statistical exploration

**Seaborn** combines simple statistical fits with plotting on pandas dataframes. Let us consider a data giving wages and many other personal information on 500 individuals (Berndt, ER. The Practice of Econometrics. 1991. NY: Addison-Wesley). Tip: The full code loading and plotting of the wages data is found in corresponding example.

```python
>>> print(data)
EDUCATION SOUTH SEX EXPERIENCE UNION WAGE AGE RACE
0 8 0 1 21 0 0.707570 35 2
1 9 0 1 42 0 0.694605 57 3
2 12 0 0 1 0 0.824126 19 3
3 12 0 0 4 0 0.602060 22 3
...
```

**Pairplot: scatter matrices**

We can easily have an intuition on the interactions between continuous variables using seaborn. `pairplot()` to display a scatter matrix:

```python
>>> import seaborn
>>> seaborn.pairplot(data, vars=['WAGE', 'AGE', 'EDUCATION'],
... kind='reg')
```

Categorical variables can be plotted as the hue:

```python
>>> seaborn.pairplot(data, vars=['WAGE', 'AGE', 'EDUCATION'],
... kind='reg', hue='SEX')
```

**Look and feel and matplotlib settings**

Seaborn changes the default of matplotlib figures to achieve a more “modern”, “excel-like” look. It does that upon import. You can reset the default using:

```python
>>> from matplotlib import pyplot as plt
>>> plt.rcdefaults()
```

Tip: To switch back to seaborn settings, or understand better styling in seaborn, see the relevent section of the seaborn documentation.

### lmplot: Plotting a Univariate Regression

**Seaborn's `lmplot()`** provides a convenient way to visualize the relationship between two variables and fit a regression line.

```python
import seaborn as sns

# Plot a regression between WAGE and EDUCATION
sns.lmplot(y='WAGE', x='EDUCATION', data=data)
```

**Robust Regression:**

If you suspect outliers might be influencing the regression line, you can use a robust regression method that is less sensitive to outliers. Seaborn offers `robust=True` in its plotting functions, while statsmodels provides robust regression models.

**Example:**

```python
# Use robust regression in seaborn
sns.lmplot(y='WAGE', x='EDUCATION', data=data, robust=True)
```

**Additional Customization:**

* **Hue:** Color the points based on a categorical variable (e.g., `SEX`).
* **Jitter:** Add jitter to scatterplot points to reduce overplotting.
* **Fit\_reg:** Set `fit_reg=False` to remove the regression line.
* **Order:** Control the order of polynomial regression (e.g., `order=2` for quadratic).

**Exercise:**

1. **Explore other variables:** Use `lmplot` to visualize relationships between other pairs of variables in the dataset.
2. **Robustness:** Compare the results of standard and robust regression to assess the impact of outliers.
3. **Polynomial regression:** Experiment with different polynomial orders to capture more complex relationships.
