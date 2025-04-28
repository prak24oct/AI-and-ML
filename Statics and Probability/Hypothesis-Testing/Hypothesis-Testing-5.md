# 📚 Hypothesis Testing (Part 5)

---

# 1️⃣ Two Sample Variance Test (F-Test)

### ✨ What is it?

- **Purpose**: To test the **equality of two variances** from different populations.
- **Also Used For**: Testing equality of means across multiple populations using **ANOVA**.

---

### 📈 Example: Machine A vs Machine B

- **Samples**:
  - Machine A: 8 samples, **standard deviation = 1.1**
  - Machine B: 5 samples, **variance = 11**
- **Hypotheses**:

  - **H₀**: ơ²₁ = ơ²₂ (Variances are equal)
  - **Hₐ**: ơ²₁ ≠ ơ²₂ (Variances are different)

- **Important Rule**:
  > Always place the **higher variance in the numerator** during the F-test calculation!

---

# 2️⃣ Types of Tests Overview 🧪

| **Samples**   | **Test Type**                                                           | **Examples**         |
| ------------- | ----------------------------------------------------------------------- | -------------------- |
| One Sample    | Z-test, T-test, One Proportion Test, One Variance Test                  |
| Two Samples   | Z-test, T-test, Paired T-test, Two Proportions Test, Two Variances Test |
| More Than Two | **ANOVA**                                                               | Analysis of variance |

---

# 3️⃣ One Variance Test (Chi-Square)

### 📏 What is it?

- **Chi-Square Test** used for:

  - Testing **population variance** against a specified value.
  - Testing **goodness of fit**.
  - Testing **independence** in contingency tables.

- **Statistic Used**: **Chi-square (χ²)**

---

# 4️⃣ Comparing Means: T-Test vs ANOVA

### ⚡ Two-Sample T-Test

- **When**: Comparing **two population means**.
- **Hypotheses**:
  - **H₀**: μA = μB
  - **Hₐ**: μA ≠ μB

---

### 🌟 ANOVA (Analysis of Variance)

- **When**: Comparing **more than two means**.
- **Hypotheses**:
  - **H₀**: μA = μB = μC = μD = ... = μk
  - **Hₐ**: At least **one mean is different**.

---

### ❗ Why use ANOVA instead of multiple T-tests?

- Example: If comparing 4 groups:
  - Number of T-tests = 6
  - Confidence level drops:  
    \[
    (0.95)^6 = 0.735
    \]
    ➔ Only **73.5%** confidence (high error chance).
- **ANOVA** ➔ Only **one test** needed ➔ maintains 95% confidence.

---

# 5️⃣ ANOVA Example: Comparing Machine Outputs

**Machines and Readings:**

- Machine 1: [150, 151, 152, 152, 151, 150]
- Machine 2: [153, 152, 148, 151, 149, 152]
- Machine 3: [156, 154, 155, 156, 157, 155]

---

### 🎯 Understanding Variations:

- **Variation Between Treatments**: Differences between group means.
- **Variation Within Treatments (Error)**: Differences within each group.

> 📌 Larger within-group variations ➔ Harder to detect differences across groups.

---

# 6️⃣ Goodness of Fit Test (Chi-Square)

### 🎲 Purpose:

- To check if observed data **matches a theoretical distribution**.

### 📌 Hypotheses:

- **H₀**: Data follows the specified distribution.
- **Hₐ**: Data does not follow.

---

### 🧪 Example 1: Is the Coin Biased?

- A coin is flipped **100 times**.
- **Results**: 40 heads, 60 tails.
- **Alpha (α)**: 0.05
- **Test**: Right-tail Chi-square test.

---

### 👕 Example 2: T-shirt Sales Distribution

| Size        | Expected Proportion | Observed Sales | Expected Sales |
| ----------- | ------------------- | -------------- | -------------- |
| Small       | 0.1                 | 25             | 22.5           |
| Medium      | 0.2                 | 41             | 45             |
| Large       | 0.4                 | 91             | 90             |
| Extra Large | 0.3                 | 68             | 67.5           |

- **Hypotheses**:
  - **H₀**: Sales proportions match expectations.
  - **Hₐ**: Sales proportions differ.

---

# 7️⃣ Contingency Tables (Chi-Square Test for Independence)

### 📋 Purpose:

- Test if **two categorical variables** are related.

---

### 🛠 Example 1: Smoking Status

|           | Smoker | Non-Smoker | Total |
| --------- | ------ | ---------- | ----- |
| Male      | 60     | 40         | 100   |
| Female    | 35     | 40         | 75    |
| **Total** | 95     | 80         | 175   |

---

### 🛠 Example 2: Shift vs Operator

|           | Operator 1 | Operator 2 | Operator 3 | Total |
| --------- | ---------- | ---------- | ---------- | ----- |
| Shift 1   | 22         | 26         | 23         | 71    |
| Shift 2   | 28         | 62         | 26         | 116   |
| Shift 3   | 72         | 22         | 66         | 160   |
| **Total** | 122        | 110        | 115        | 347   |

---

### 🔎 Hypotheses:

- **H₀**: No relationship between rows and columns.
- **Hₐ**: A relationship exists (type unspecified).

---

# 8️⃣ Bonus: Tukey’s HSD Test (linked in your PDF)

### 🧠 What is Tukey’s HSD?

- After an **ANOVA** tells us that differences exist, **Tukey’s HSD (Honestly Significant Difference)** tells us **which groups differ**.
- **Post-hoc test** ➔ Used after rejecting ANOVA’s null hypothesis.
- **Python Libraries**:
  - `scipy.stats.tukey_hsd`
  - Tutorials: [Statology Tukey Test](https://www.statology.org/tukey-test-python/)

---

# 📜 Formulas & Key Definitions

---

### ⭐ F-Test Statistic

\[
F = \frac{\text{Variance}\_1}{\text{Variance}\_2}
\]
(_Higher variance in numerator_)

---

### ⭐ Chi-Square Statistic

\[
\chi^2 = \sum \frac{(O - E)^2}{E}
\]

- O = Observed frequency
- E = Expected frequency

---

### ⭐ ANOVA Variances

- **Between Groups**:
  \[
  \text{MS}_{\text{Between}} = \frac{\text{SS}_{\text{Between}}}{\text{df}\_{\text{Between}}}
  \]

- **Within Groups**:
  \[
  \text{MS}_{\text{Within}} = \frac{\text{SS}_{\text{Within}}}{\text{df}\_{\text{Within}}}
  \]

---

# 📊 Data Visualization Techniques

- **ANOVA** ➔ Group means plotted.
- **Goodness of Fit** ➔ Bar graphs: observed vs expected.
- **Contingency Tables** ➔ Heatmaps or cross-tab charts.

---

# 🧠 Practice Questions

### 1. Conceptual

👉 Why should higher variance be placed in the numerator for F-test?

- **Answer**: To ensure correct comparison with the F-distribution (right-skewed).

---

### 2. Numerical

👉 Calculate F-statistic:

- Variance A = 8, Variance B = 2
- **Answer**:
  \[
  F = \frac{8}{2} = 4
  \]

---

### 3. Conceptual

👉 Why not use multiple T-tests instead of ANOVA for 5 groups?

- **Answer**: Multiple tests inflate Type I error. ANOVA controls error rate.

---

### 4. Numerical

👉 A coin flipped 100 times has 40 heads. Expected = 50 heads. What is the χ² contribution?

- **Answer**:
  \[
  \chi^2 = \frac{(40-50)^2}{50} = 2
  \]

---

# ✨ Summary & Key Takeaways

- **F-Test** ➔ Compare **two variances**.
- **Chi-Square** ➔ Test **one variance**, **goodness of fit**, **independence**.
- **T-Test** ➔ Compare **two means**.
- **ANOVA** ➔ Compare **more than two means**.
- **Goodness of Fit** ➔ Only **right-tail test**.
- **Contingency Table Test** ➔ Check relationship between categorical variables.
- **Tukey’s HSD** ➔ Identify specifically **which groups differ** after ANOVA.

---

Perfect!  
You're asking for **two clean deliverables**:

- 📚 First Part: Structured **theory notes** (already prepared ✅)
- 🛠 Second Part: **All concepts converted into Python coding problems** separately as a **Jupyter Notebook-ready note** ✅✅

---

### 📋 Let's now build the second part:

# 🛠 Hypothesis Testing — Python Coding Problems for Jupyter Notebook

---

# 1️⃣ Two Sample Variance Test (F-Test)

## Problem Statement:

You are given two sets of sample data from two machines. Test if their variances are significantly different at 90% confidence level.

## Python Code:

```python
import scipy.stats as stats

# Machine A
std_dev_machineA = 1.1
nA = 8

# Machine B
var_machineB = 11
nB = 5

# Step 1: Calculate variances
var_machineA = std_dev_machineA ** 2

# Step 2: Calculate F-statistic (higher variance on top)
F = var_machineB / var_machineA
df1 = nB - 1
df2 = nA - 1

# Step 3: Get p-value
p_value = 2 * min(stats.f.cdf(F, df1, df2), 1 - stats.f.cdf(F, df1, df2))

# Step 4: Conclusion
alpha = 0.10  # 90% confidence

print(f"F-statistic: {F:.4f}")
print(f"P-value: {p_value:.4f}")

if p_value < alpha:
    print("✅ Reject H₀: Variances are different.")
else:
    print("❌ Fail to Reject H₀: Variances are equal.")
```

---

# 2️⃣ One Variance Test (Chi-Square)

## Problem Statement:

Suppose you expect the variance of a manufacturing process to be 4. You collect 20 samples and calculate sample variance = 5.5. Test if the variance is significantly different at 5% level.

## Python Code:

```python
# Chi-Square Test for One Variance

import scipy.stats as stats

sample_variance = 5.5
expected_variance = 4
n = 20

chi_square_stat = (n - 1) * sample_variance / expected_variance
df = n - 1

# Two-tailed test
p_value = 2 * min(stats.chi2.cdf(chi_square_stat, df), 1 - stats.chi2.cdf(chi_square_stat, df))

alpha = 0.05

print(f"Chi-Square Statistic: {chi_square_stat:.4f}")
print(f"P-value: {p_value:.4f}")

if p_value < alpha:
    print("✅ Reject H₀: Variance is different.")
else:
    print("❌ Fail to Reject H₀: Variance is not significantly different.")
```

---

# 3️⃣ Goodness of Fit Test (Chi-Square)

## Problem Statement:

Flip a coin 100 times. You get 40 heads and 60 tails. Check if the coin is biased at 95% confidence.

## Python Code:

```python
# Goodness of Fit Test

import scipy.stats as stats

# Observed frequencies
observed = [40, 60]

# Expected frequencies (fair coin)
expected = [50, 50]

# Chi-square test
chi2_stat, p_value = stats.chisquare(f_obs=observed, f_exp=expected)

alpha = 0.05

print(f"Chi-Square Statistic: {chi2_stat:.4f}")
print(f"P-value: {p_value:.4f}")

if p_value < alpha:
    print("✅ Reject H₀: The coin is biased.")
else:
    print("❌ Fail to Reject H₀: The coin is not biased.")
```

---

# 4️⃣ Contingency Table Test (Chi-Square Test for Independence)

## Problem Statement:

Check if there is any association between smoking status and gender.

## Python Code:

```python
# Contingency Table Test

import scipy.stats as stats

# Contingency Table
# Rows: Gender (Male, Female)
# Columns: Smoker, Non-Smoker
data = [[60, 40],  # Male
        [35, 40]]  # Female

chi2_stat, p_value, dof, expected = stats.chi2_contingency(data)

alpha = 0.05

print(f"Chi-Square Statistic: {chi2_stat:.4f}")
print(f"P-value: {p_value:.4f}")
print("Expected Frequencies Table:")
print(expected)

if p_value < alpha:
    print("✅ Reject H₀: Smoking status and gender are related.")
else:
    print("❌ Fail to Reject H₀: No relationship between smoking and gender.")
```

---

# 5️⃣ ANOVA (One-Way ANOVA Test)

## Problem Statement:

You collected test scores from 3 different machines. Check if there is a significant difference in their mean outputs.

## Python Code:

```python
# One-Way ANOVA

import scipy.stats as stats

# Machine readings
machine1 = [150, 151, 152, 152, 151, 150]
machine2 = [153, 152, 148, 151, 149, 152]
machine3 = [156, 154, 155, 156, 157, 155]

# Perform ANOVA
F_stat, p_value = stats.f_oneway(machine1, machine2, machine3)

alpha = 0.05

print(f"F-statistic: {F_stat:.4f}")
print(f"P-value: {p_value:.4f}")

if p_value < alpha:
    print("✅ Reject H₀: At least one machine has a different mean.")
else:
    print("❌ Fail to Reject H₀: No significant difference in machine outputs.")
```

---

# 6️⃣ Post-ANOVA: Tukey’s HSD Test

## Problem Statement:

After ANOVA, find out which specific machines differ.

## Python Code:

```python
# Tukey HSD Test

import pandas as pd
import statsmodels.api as sm
from statsmodels.stats.multicomp import pairwise_tukeyhsd

# Combine data
data = machine1 + machine2 + machine3
labels = (['Machine1'] * len(machine1)) + (['Machine2'] * len(machine2)) + (['Machine3'] * len(machine3))

# Create a DataFrame
df = pd.DataFrame({'Score': data, 'Machine': labels})

# Perform Tukey's HSD
tukey = pairwise_tukeyhsd(endog=df['Score'], groups=df['Machine'], alpha=0.05)
print(tukey.summary())
```

---

# 📝 Summary Table

| **Test**                | **Python Function**                               | **Package** |
| ----------------------- | ------------------------------------------------- | ----------- |
| F-Test                  | `scipy.stats.f.cdf()`                             | SciPy       |
| One Variance Chi-Square | `scipy.stats.chi2.cdf()`                          | SciPy       |
| Goodness of Fit         | `scipy.stats.chisquare()`                         | SciPy       |
| Contingency Table       | `scipy.stats.chi2_contingency()`                  | SciPy       |
| One-Way ANOVA           | `scipy.stats.f_oneway()`                          | SciPy       |
| Tukey’s HSD             | `statsmodels.stats.multicomp.pairwise_tukeyhsd()` | statsmodels |

---
