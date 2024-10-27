# 02 hypothesis testing

### Hypothesis Testing: Comparing Two Groups

**Hypothesis Testing** involves making inferences about populations based on sample data. In this section, we'll explore the Student's t-test, a common statistical test used to compare means between two groups.

#### 1. Student's t-test

**1-Sample t-test:**

* **Purpose:** Tests if the population mean of a sample is significantly different from a specified value.
* **Assumptions:** Data follows a normal distribution.
* **Function:** `scipy.stats.ttest_1samp(data, popmean)`

**Example:**

```python
from scipy import stats

# Test if the population mean of VIQ is significantly different from 0
t_statistic, p_value = stats.ttest_1samp(data['VIQ'], 0)
print("T-statistic:", t_statistic)
print("P-value:", p_value)
```

**2-Sample t-test:**

* **Purpose:** Tests if the means of two independent populations are significantly different.
* **Assumptions:** Data follows a normal distribution, equal variances in the two populations.
* **Function:** `scipy.stats.ttest_ind(sample1, sample2)`

**Example:**

```python
# Test for differences in mean VIQ between males and females
female_viq = data[data['Gender'] == 'Female']['VIQ']
male_viq = data[data['Gender'] == 'Male']['VIQ']

t_statistic, p_value = stats.ttest_ind(female_viq, male_viq)
print("T-statistic:", t_statistic)
print("P-value:", p_value)
```

**Interpretation:**

* **P-value:** A small p-value (typically less than 0.05) indicates a statistically significant difference between the means.
* **T-statistic:** Measures the magnitude of the difference between the means relative to the variability of the data.

**Exercise:**

1. **Paired t-test:** Use `scipy.stats.ttest_rel()` to perform a paired t-test if you have paired data (e.g., measurements before and after an intervention).
2. **Welch's t-test:** Use `scipy.stats.ttest_ind(sample1, sample2, equal_var=False)` if you suspect unequal variances between the two populations.

**Additional Considerations:**

* **Normality:** Check for normality using methods like the Shapiro-Wilk test (`scipy.stats.shapiro`). If data is not normally distributed, consider non-parametric alternatives like the Mann-Whitney U test.
* **Effect Size:** Calculate effect size measures (e.g., Cohen's d) to quantify the practical significance of the difference.
* **Multiple Comparisons:** If you're conducting multiple t-tests, adjust the significance level to account for the increased chance of false positives (e.g., Bonferroni correction).

By understanding these concepts and applying the appropriate t-test, you can effectively analyze and draw meaningful conclusions from your data.

### Paired t-tests: Analyzing Repeated Measurements

When dealing with data where the same individuals are measured multiple times, paired t-tests are appropriate. Unlike independent t-tests, paired t-tests account for the correlation between measurements within individuals, providing a more accurate analysis.

#### Example: Comparing IQ Measures

Consider a dataset with three IQ measures (FSIQ, VIQ, and PIQ) for the same individuals. To test if FSIQ and PIQ are significantly different, we can use:

**Independent t-test (incorrect):**

```python
from scipy import stats

# Independent t-test
t_statistic, p_value = stats.ttest_ind(data['FSIQ'], data['PIQ'])
print("T-statistic:", t_statistic)
print("P-value:", p_value)
```

**Paired t-test (correct):**

```python
# Paired t-test
t_statistic, p_value = stats.ttest_rel(data['FSIQ'], data['PIQ'])
print("T-statistic:", t_statistic)
print("P-value:", p_value)
```

**Equivalent to a 1-sample t-test:**

```python
# 1-sample t-test on the difference
t_statistic, p_value = stats.ttest_1samp(data['FSIQ'] - data['PIQ'], 0)
print("T-statistic:", t_statistic)
print("P-value:", p_value)
```

#### Non-Parametric Alternative: Wilcoxon Signed-Rank Test

If you're unsure about the normality assumption of the data, the Wilcoxon signed-rank test provides a non-parametric alternative to the paired t-test.

```python
# Wilcoxon signed-rank test
statistic, p_value = stats.wilcoxon(data['FSIQ'], data['PIQ'])
print("Statistic:", statistic)
print("P-value:", p_value)
```

#### Exercise

1. **Test for gender differences in weight:** Use a paired t-test (or Wilcoxon signed-rank test if assumptions are not met) to compare the weights of males and females, considering the data is paired (same individuals).
2. **Explore other IQ measures:** Conduct similar analyses for other combinations of IQ measures (e.g., FSIQ vs. VIQ, VIQ vs. PIQ).

**Conclusion:**

By using paired t-tests or Wilcoxon signed-rank tests, you can appropriately analyze repeated measurements and draw more accurate conclusions about differences within the same individuals.
