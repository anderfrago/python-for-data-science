# 03 linear models multiple factors and analysis of variance

### Linear Models, Multiple Factors, and Analysis of Variance

#### 1. Simple Linear Regression

**Hypothesis Testing:**

Given two sets of observations, `x` and `y`, we want to test the hypothesis that `y` is a linear function of `x`. This can be expressed as:

```
y = coef * x + intercept + e
```

Where:

* `coef` is the coefficient representing the relationship between `x` and `y`.
* `intercept` is the y-intercept of the linear model.
* `e` is the error term representing random noise or unexplained variation.

**Steps:**

1. **Generate Data:** Create simulated data according to the linear model.
2. **Create DataFrame:** Store the data in a pandas DataFrame for easier manipulation.
3. **Fit the Model:** Use `statsmodels.formula.api.ols` to fit the linear regression model.

```python
import numpy as np
import pandas as pd
import statsmodels.formula.api as smf

# Generate data
x = np.linspace(-5, 5, 20)
np.random.seed(1)
y = -5 + 3 * x + 4 * np.random.normal(size=x.shape)

# Create DataFrame
data = pd.DataFrame({'x': x, 'y': y})

# Fit the model
model = smf.ols("y ~ x", data=data).fit()
```

#### 2. Model Summary

The `model.summary()` method provides a comprehensive overview of the fitted model, including:

* **Coefficients:** Estimated values for the `coef` and `intercept`.
* **Standard Errors:** Estimates of the standard deviation of the coefficients.
* **T-statistics:** Calculated by dividing the coefficients by their standard errors.
* **P-values:** Probability of observing a t-statistic as extreme as the calculated one, assuming the null hypothesis (no relationship) is true.
* **R-squared:** Measures the proportion of variance in `y` explained by the model.

**Example:**

```python
print(model.summary())
```

#### 3. Retrieving Estimated Parameters

To access the estimated coefficients and their standard errors, you can use the following attributes:

```python
coef = model.params['x']  # Estimated coefficient for x
intercept = model.params['Intercept']  # Estimated intercept
std_err_coef = model.bse['x']  # Standard error for the coefficient
std_err_intercept = model.bse['Intercept']  # Standard error for the intercept
```

#### Exercise

1. **Experiment with different data:** Generate new data with varying `coef`, `intercept`, and noise levels. Observe how the model summary changes.
2. **Add more features:** Introduce additional features (e.g., `x2`) and fit a multiple linear regression model. Analyze the significance of each feature.
3. **Interpret the R-squared:** Discuss what a high or low R-squared value indicates about the model's fit.

### Analyzing Categorical Variables in Linear Models

Linear regression models can be extended to handle categorical variables, allowing us to compare groups or multiple categories.

#### Example: IQ Differences by Gender

We revisit the brain size dataset (`examples/brain_size.csv`) to compare VIQ scores between males and females.

**1. Fitting a Linear Model:**

```python
import pandas as pd
import statsmodels.formula.api as smf

# Read data
data = pd.read_csv('examples/brain_size.csv', sep=';', na_values=".")

# Model formula (VIQ ~ Gender + 1)
model = smf.ols("VIQ ~ Gender + 1", data).fit()

# Print model summary
print(model.summary())
```

**Interpretation:**

The R-squared value (0.015) indicates a weak relationship between VIQ and gender. The p-value for the `Gender[T.Male]` coefficient (0.445) is not significant, suggesting no statistically significant difference in VIQ between males and females based on this model.

**2. Treatment of Categorical Variables:**

* **Automatic Detection:** Statsmodels automatically detects categorical variables like `Gender`.
* **Dummy Variables:** Categorical variables are represented by K-1 dummy variables, where K is the number of categories. The remaining category is absorbed into the intercept.

**3. Specifying the Model:**

**a) Forcing Categorical Treatment:**

```python
model = smf.ols("VIQ ~ C(Gender)", data).fit()  # C(Gender) forces categorical treatment
```

**b) Intercept Control:**

* **Remove Intercept:** Use `- 1` in the formula (e.g., "VIQ \~ Gender - 1").
* **Force Intercept:** Use `+ 1` in the formula (e.g., "VIQ \~ Gender + 1").

**4. Comparing Multiple IQ Types:**

To compare FSIQ and PIQ, we can create a "long-form" table where each row represents an IQ measurement with its corresponding type.

```python
data_fisq = pd.DataFrame({'iq': data['FSIQ'], 'type': 'fsiq'})
data_piq = pd.DataFrame({'iq': data['PIQ'], 'type': 'piq'})
data_long = pd.concat((data_fisq, data_piq))

# Fit model with "type" as categorical variable
model = smf.ols("iq ~ type", data_long).fit()
print(model.summary())
```

**5. Comparison with Independent t-test:**

The model coefficients and p-values for the "type" variable should be similar to the results obtained from an independent t-test:

```python
from scipy import stats

t_statistic, p_value = stats.ttest_ind(data['FSIQ'], data['PIQ'])
print("T-statistic:", t_statistic)
print("P-value:", p_value)
```

**Conclusion:**

By using linear regression with categorical variables, you can analyze group differences and draw conclusions about the relationships between categorical factors and continuous dependent variables.
