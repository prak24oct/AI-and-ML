
# **📌 Python Examples for Probability Distributions**
Let’s implement **Poisson Distribution**, **Normal Distribution**, and **Z-Score Calculations** step by step.

---

## **🎯 1️⃣ Poisson Distribution (Rare Events Prediction)**

### **📌 Example 1: Predicting Visitors to a Booking Counter**
📍 **Scenario**: On average, **3.6 people** visit a booking counter every **10 minutes**. What’s the probability that **7 people** visit in the next 10 minutes?

#### **✅ Python Implementation:**
```python
from scipy.stats import poisson

# Given data
u = 3.6  # Average arrivals (mean)
x = 7  # Actual arrivals 

# Poisson probability
P_x = poisson.pmf(x, u)
print(f"Probability of exactly 7 people arriving: {P_x:.4f}")  # Output: ~0.0424 (4.24%)
```

---

### **📌 Example 2: Simulating Poisson Events**
📍 **Scenario**: Simulate **1,000 days** of email arrivals, where an average of **5 emails** arrive per hour.

```python
import numpy as np
import matplotlib.pyplot as plt

# Generate Poisson-distributed data
emails_per_hour = np.random.poisson(5, 1000)

# Plot histogram
plt.hist(emails_per_hour, bins=range(15), color='skyblue', edgecolor='black', alpha=0.7)
plt.xlabel("Number of Emails")
plt.ylabel("Frequency")
plt.title("Poisson Distribution of Email Arrivals per Hour")
plt.show()
```

🎯 **Takeaway**: Poisson Distribution **models rare events** like customer arrivals, accidents, or machine failures.

---

## **🔥 2️⃣ Normal Distribution (Gaussian Curve)**

### **📌 Example 3: Visualizing Normal Distribution**
📍 **Scenario**: Generate **100,000 random values** from a normal distribution with **mean = 70** and **std dev = 10**.

```python
import scipy.stats as stats

# Generate normal distribution data
mu, sigma = 70, 10  # Mean and standard deviation
data = np.random.normal(mu, sigma, 100000)

# Plot histogram
sns.histplot(data, bins=50, kde=True, color="purple")
plt.axvline(mu, color='red', linestyle='dashed', linewidth=2)  # Mean line
plt.xlabel("Test Scores")
plt.ylabel("Frequency")
plt.title("Normal Distribution of Test Scores")
plt.show()
```

🎯 **Takeaway**: Normal Distribution models **heights, IQ scores, exam results, stock prices**, etc.

---

## **📌 3️⃣ Z-Score Calculation (Probability of Above/Below a Value)**

### **📌 Example 4: Finding Z-Score & Probability**
📍 **Scenario**: A university’s test scores have **mean = 70** and **std dev = 5**. What percentage of students scored **above 80**?

#### **✅ Python Calculation**
```python
from scipy.stats import norm

# Given data
X = 80  # Test score
mu, sigma = 70, 5  # Mean and standard deviation

# Calculate Z-score
Z = (X - mu) / sigma

# Find probability of scoring above 80
P_above_80 = 1 - norm.cdf(Z)
print(f"Probability of scoring above 80: {P_above_80:.4f}")  # Output: ~0.0228 (2.28%)
```

🎯 **Takeaway**: The **Z-score** tells us how far a value is from the mean and helps estimate probabilities.

---

## **📝 4️⃣ Practice Questions**
💡 **Poisson Distribution**
1️⃣ A small café receives an average of **5 orders per minute**. What’s the probability of receiving **8 orders in the next minute**?

💡 **Normal Distribution**
2️⃣ A factory produces bolts with **mean length = 10cm** and **σ = 0.5cm**. What percentage of bolts are **longer than 11cm**?

---

## **🚀 5️⃣ Summary & Key Takeaways**
✔ **Poisson Distribution** predicts rare events over a fixed interval.  
✔ **Normal Distribution** is used for continuous data like heights and scores.  
✔ **Z-score** helps compare different distributions and calculate probabilities.  

🔍 Want **more ML applications** using probability? Let me know! 🚀
---
## Python Functions: Poisson and Normal Distributions

### Introduction to Probability Distributions
Probability distributions are essential in statistics for modeling random variables. The **Poisson Distribution** and **Normal Distribution** are two key distributions frequently used to model various real-world scenarios, including event occurrences and natural phenomena.

### 1. Poisson Distribution

The **Poisson distribution** models the number of events that happen in a fixed interval of time or space, given that the events occur with a constant rate and independently of each other.

#### Key Concepts:
- **Mean (λ)**: The average number of events per interval.
- **Probability Mass Function (PMF)**: Gives the probability of a specific number of events happening.
- **Cumulative Distribution Function (CDF)**: Gives the probability of a number of events less than or equal to a specific number.
- **Survival Function (SF)**: Gives the probability of more than a specific number of events.

#### Code Example for Poisson Distribution
```python
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
from scipy.stats import poisson

# Generating 1000 numbers that follow a Poisson distribution with mean 3.6
q_size = np.random.poisson(3.6, 1000)

# Plotting the distribution
sns.countplot(x=q_size)
plt.show()

# Using the theoretical Poisson formulas
print(poisson.pmf(7, 3.6))  # Probability of exactly 7 events
print(poisson.cdf(7, 3.6))  # Probability of 7 or fewer events
print(poisson.sf(7, 3.6))   # Probability of more than 7 events
```

#### Expected Output:
- The `countplot` will display the frequency of different event counts (Poisson-distributed).
- `poisson.pmf(7, 3.6)` gives the probability of exactly 7 events.
- `poisson.cdf(7, 3.6)` gives the probability of getting 7 or fewer events.
- `poisson.sf(7, 3.6)` gives the probability of getting more than 7 events.

#### Real-World Application Example
If a company receives on average 4.6 calls per hour, we can calculate:
- **Probability of exactly 8 calls**: `poisson.pmf(8, 4.6)`
- **Probability of more than 6 calls**: `poisson.sf(6, 4.6)`

```python
p8 = poisson.pmf(8, 4.6)  # Exact probability of 8 calls
p_gt_6 = poisson.sf(6, 4.6)  # Probability of more than 6 calls
print(f"Probability of exactly 8 calls: {p8}")
print(f"Probability of more than 6 calls: {p_gt_6}")
```

### 2. Normal Distribution

The **Normal distribution** (also known as Gaussian distribution) describes data that is symmetrically distributed around the mean, where most observations cluster around the central peak.

#### Key Concepts:
- **Mean (µ)**: The center of the distribution.
- **Standard Deviation (σ)**: A measure of the spread of the distribution.
- **Probability Density Function (PDF)**: The probability of the variable taking a specific value.
- **Cumulative Distribution Function (CDF)**: The probability of the variable being less than or equal to a specific value.
- **Survival Function (SF)**: The probability of the variable being greater than a specific value.

#### Code Example for Normal Distribution
```python
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
from scipy.stats import norm

# Drawing 1000 samples from a normal distribution with mean=100 and std=2
a = np.random.normal(100, 2, 1000)

# Plotting the histogram and Kernel Density Estimation (KDE)
sns.histplot(a, kde=True)
plt.show()

# Finding the percentage of values above 98
print(f"Percentage of data above 98: {sum(a > 98) / len(a) * 100}%")
```

#### Expected Output:
- The `histplot` will display a histogram of the normal distribution with a smooth KDE curve.
- The calculation of values greater than 98 shows that 84% of data points are to the right of -1 standard deviation (σ).

#### Real-World Application Example: Perfume Bottle Volumes
Given that perfume bottles have a mean volume of 150cc and a standard deviation of 2cc, we can calculate:
- **Percentage of bottles with more than 153cc**: `norm.sf(153, 150, 2)`
- **Percentage of bottles with volumes between 148cc and 152cc**: `norm.cdf(152, 150, 2) - norm.cdf(148, 150, 2)`

```python
# Probability of getting more than 153cc
prob_more_than_153 = norm.sf(153, 150, 2)
print(f"Probability of volume > 153cc: {prob_more_than_153 * 100}%")

# Probability of getting a volume between 148cc and 152cc
prob_between_148_152 = norm.cdf(152, 150, 2) - norm.cdf(148, 150, 2)
print(f"Probability of volume between 148cc and 152cc: {prob_between_148_152 * 100}%")
```

#### Z-Table and PDF
The **Z-table** helps calculate the cumulative probability for a standard normal distribution. For example, to find the probability of getting exactly 153cc, we can use the `norm.pdf(153, 150, 2)` function, which gives the probability density function value.

```python
# Z-table value for 153cc
z_value = norm.pdf(153, 150, 2)
print(f"Z-value for 153cc: {z_value}")

# Plotting the probability density
x_vals = np.linspace(144, 156, 1300)
y_vals = norm.pdf(x_vals, 150, 2)
sns.lineplot(x=x_vals, y=y_vals)
plt.axvline(152, color='red')  # Marking the value at 152cc
plt.show()
```

#### Debugging Tips:
1. **Check distribution parameters**: Ensure that the mean (`μ`) and standard deviation (`σ`) values are correct and appropriate for your data.
2. **Sampling size**: Ensure you are drawing a sufficient number of samples for accurate representation, especially when visualizing distributions.
3. **Edge cases**: Be cautious of outliers or extreme values that could distort your distribution's shape or probability calculations.
4. **Overflow or underflow**: When using extreme values in calculations, such as very large or small inputs, numerical instability might occur. Use logarithms for handling such cases.
5. **Use appropriate functions**: Use `pmf` for exact probabilities in discrete distributions (like Poisson) and `pdf` for continuous distributions (like Normal).

### Conclusion:
- The **Poisson distribution** is ideal for modeling event counts in fixed intervals, such as the number of calls a company receives.
- The **Normal distribution** is useful for modeling continuous data like the volume of liquid in a bottle, with most data points clustering around the mean.
- By understanding and applying the principles of these distributions, you can better model and analyze real-world data in Python using libraries like `numpy`, `matplotlib`, `seaborn`, and `scipy`.

