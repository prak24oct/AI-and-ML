# 📖 Lecture Notes: Hypothesis Testing in AI & ML

---

## 1️⃣ Introduction to Hypothesis Testing in AI & ML
Hypothesis testing is a fundamental statistical tool used in AI & ML to make data-driven decisions. It helps in validating machine learning models, assessing statistical significance, and ensuring the reliability of results. Hypothesis testing is essential in A/B testing, feature selection, and model evaluation.

---

## 2️⃣ Hypothesis Testing Steps
1. **State the Null Hypothesis (H₀)**: The assumption that there is no effect or no difference.
2. **State the Alternative Hypothesis (H₁ or Ha)**: The assumption that there is a significant effect or difference.
3. **Select the Significance Level (α)**: Typically set at **0.05**.
4. **Compute the Test Statistic**: Calculate the relevant test statistic (Z, T, etc.).
5. **Determine the Critical Value**: Use statistical tables to find the threshold value.
6. **Compare and Make Decision**:
   - If test statistic > critical value, **reject H₀**.
   - Otherwise, **fail to reject H₀**.

---

## 3️⃣ Key Concepts Explained
### ❖ Null & Alternative Hypothesis
- **Null Hypothesis (H₀)**: Assumes no effect or no difference in the population.
- **Alternative Hypothesis (H₁ or Ha)**: Assumes a significant effect or difference.

### ❖ Significance Level (α)
- Typically set at **0.05** or **0.01**.
- Represents the probability of rejecting the null hypothesis when it is actually true.

### ❖ p-Value
- The probability of obtaining the observed data assuming the null hypothesis is true.
- If **p < α**, reject H₀; otherwise, fail to reject H₀.

### ❖ Type I & Type II Errors
- **Type I Error (False Positive)**: Rejecting a true null hypothesis.
- **Type II Error (False Negative)**: Failing to reject a false null hypothesis.

### ❖ Critical Value & Test Statistic
- **Critical Value**: The threshold value that defines the rejection region.
- **Test Statistic**: A calculated value (e.g., z-score, t-score) used to compare against the critical value.

---

## 4️⃣ Mathematical Formulas & Key Definitions
### **Z-Test Formula** (When Population Standard Deviation is Known)
$$Z = \frac{\bar{x} - \mu}{\sigma / \sqrt{n}}$$

### **T-Test Formula** (When Population Standard Deviation is Unknown)
$$t = \frac{\bar{x} - \mu}{s / \sqrt{n}}$$

### **p-Value Calculation**
For a Z-score:
$$p = \text{norm.sf} (Z)$$

For a two-tailed test:
$$p = 2 \times \text{norm.sf} (Z)$$

---

## 5️⃣ Real-World AI & ML Applications
- **A/B Testing in AI Models**: Testing two versions of a model to see which performs better.
- **Feature Selection**: Determining whether a feature significantly impacts model performance.
- **Anomaly Detection**: Identifying outliers in datasets using hypothesis testing.
- **Model Validation**: Checking if a new model performs significantly better than a baseline model.

---

## 6️⃣ Case Studies & Examples with Python Code
### Example 1: Perfume Bottle Filling Process (Z-Test)
#### Hypothesis:
- **H₀:** µ = 150cc
- **H₁:** µ ≠ 150cc

#### Given:
$$(\sigma = 2 ), ( n = 100 ), ( \bar{x} = 150.2)$$

#### Python Code:
```python
import scipy.stats as stats
import numpy as np

mu = 150  # Population mean
sigma = 2  # Population standard deviation
n = 100  # Sample size
x_bar = 150.2  # Sample mean

z_score = (x_bar - mu) / (sigma / np.sqrt(n))
p_value = 2 * stats.norm.sf(abs(z_score))

print(f"Z-Score: {z_score}, P-Value: {p_value}")
```

### Example 2: EMS Response Time (Z-Test)
#### Hypothesis:
- **H₀:** µ ≤ 12 min
- **H₁:** µ > 12 min

#### Given:
$$( \sigma = 3.2 ), ( n = 40 ), ( \bar{x} = 13.25 )$$

#### Python Code:
```python
mu = 12
sigma = 3.2
n = 40
x_bar = 13.25

z_score = (x_bar - mu) / (sigma / np.sqrt(n))
p_value = stats.norm.sf(z_score)

print(f"Z-Score: {z_score}, P-Value: {p_value}")
```

---

## 7️⃣ Visualizations & Graphs (If Applicable)
- **Z & T-Distributions**: Show confidence intervals and rejection regions.
- **Boxplots**: Visualizing sample distributions and outliers.
- **Histograms**: Checking normality assumptions.

---

## 8️⃣ Common Mistakes & Best Practices
### ❌ Mistakes
- Misinterpreting p-values (p < α doesn’t mean practical significance).
- Ignoring assumptions (normality, independence, equal variances).
- Incorrectly choosing between Z-test and T-test.

### ✅ Best Practices
- Always check data distribution before applying tests.
- Use two-tailed tests unless there’s a strong reason for a one-tailed test.
- Report effect size along with p-values.

---

## 9️⃣ Practice Questions & Exercises
### ❖ Question 1: Toothpaste Tube Filling Process
- Given: $( \bar{x} = 6.1 ), ( \sigma = 0.2 ), ( n = 30 )$
- **Formulate H₀ and Ha.**
- **Compute Z-score and p-value.**

### ❖ Question 2: Breaking Strength of Steel Rods
- Given: Sample strengths: **32,000, 36,000, 34,000, 34,500**
- **Identify the correct hypothesis.**

### ❖ Conceptual Questions
1. How do you interpret a p-value of 0.03 in a two-tailed test?
2. What happens if the sample size is too small in hypothesis testing?

---

## 🔟 Summary & Key Takeaways
- **Hypothesis Testing** is crucial for validating AI & ML models.
- **p-Value** determines statistical significance.
- **Z-Test** is used when population standard deviation is known, while **T-Test** is used when it’s unknown.
- **Real-world applications** include A/B testing, feature selection, and model validation.
- **Avoid common pitfalls** like misinterpreting p-values and violating assumptions.

---

📌 **End of Lecture Notes**