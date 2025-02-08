# **📌 Python Examples for Probability & Distributions**

## **1️⃣ Basic Probability Calculation**
Let’s calculate the probability of rolling a **4** on a fair **six-sided die**.

```python
# Probability of rolling a 4 on a six-sided die
total_outcomes = 6  # 1,2,3,4,5,6
favorable_outcomes = 1  # Only one outcome is 4

probability = favorable_outcomes / total_outcomes
print(f"Probability of rolling a 4: {probability:.2f}")  # Output: 0.17 (1/6)
```

---

## **2️⃣ Probability of Independent Events**
If we toss a **coin twice**, what is the probability of getting **two heads**?

```python
# Independent event: Coin toss
P_head = 0.5  # Probability of getting heads

# Probability of two heads in two tosses
P_two_heads = P_head * P_head
print(f"Probability of getting two heads: {P_two_heads:.2f}")  # Output: 0.25 (1/4)
```

---

## **3️⃣ Probability of Dependent Events**
Let’s say we have **a bag with 5 red and 5 blue balls**. If we draw **two balls without replacement**, what is the probability that both are red?

```python
# Dependent events: Drawing two red balls
red_balls = 5
total_balls = 10

P_first_red = red_balls / total_balls  # First draw
P_second_red = (red_balls - 1) / (total_balls - 1)  # Second draw

P_both_red = P_first_red * P_second_red
print(f"Probability of drawing two red balls: {P_both_red:.2f}")  # Output: 0.22
```

---

## **4️⃣ Permutations & Combinations**
Let’s calculate:
- **Permutations**: Selecting 3 players from 5 for **Captain, Vice-Captain, and Treasurer**.
- **Combinations**: Selecting 3 players from 5 **without position**.

```python
from math import factorial

# Permutation: Order matters
n, r = 5, 3
permutation = factorial(n) / factorial(n - r)
print(f"Permutation (5P3): {int(permutation)}")  # Output: 60

# Combination: Order doesn't matter
combination = factorial(n) / (factorial(r) * factorial(n - r))
print(f"Combination (5C3): {int(combination)}")  # Output: 10
```

---

## **5️⃣ Binomial Distribution (Coin Toss Example)**
If you **flip a coin 4 times**, what is the probability of getting **exactly 2 heads**?

```python
from math import comb

# Binomial probability formula: P(X = k) = C(n, k) * (p^k) * ((1-p)^(n-k))
n, k = 4, 2  # 4 tosses, 2 heads
p = 0.5  # Probability of heads

P_x_equals_k = comb(n, k) * (p ** k) * ((1 - p) ** (n - k))
print(f"Probability of getting exactly 2 heads in 4 tosses: {P_x_equals_k:.3f}")  # Output: 0.375
```

---

## **6️⃣ Simulating Probability Distributions (Rolling a Die)**
Let’s **simulate rolling a fair die 10,000 times** and find the probability of rolling a **6**.

```python
import numpy as np

# Simulate rolling a die 10,000 times
rolls = np.random.randint(1, 7, 10000)  # Random numbers from 1 to 6
P_six = np.sum(rolls == 6) / len(rolls)

print(f"Experimental Probability of rolling a 6: {P_six:.2f}")  # Should be close to 1/6 ≈ 0.17
```

---

## **7️⃣ Visualizing a Probability Distribution**
Let’s **plot the probability distribution** for rolling a die.

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Count occurrences of each die roll
outcomes, counts = np.unique(rolls, return_counts=True)

# Normalize counts to get probability
probabilities = counts / len(rolls)

# Plot
sns.barplot(x=outcomes, y=probabilities, palette="Blues")
plt.xlabel("Die Face")
plt.ylabel("Probability")
plt.title("Probability Distribution of Rolling a Die")
plt.show()
```

---

## **8️⃣ Real-World AI/ML Example: Predicting Customer Churn**
A company wants to predict **customer churn** using a **binomial distribution**. If **10% of customers** leave each month, what is the probability that **exactly 3 out of 20** customers will churn?

```python
n, k = 20, 3  # 20 customers, 3 churning
p = 0.1  # 10% probability of churn

P_churn_3 = comb(n, k) * (p ** k) * ((1 - p) ** (n - k))
print(f"Probability of exactly 3 customers churning: {P_churn_3:.3f}")  # Output: 0.19
```

---

# **🔑 Key Takeaways**
✅ **Basic probability** helps us predict outcomes in games, AI, and real life.  
✅ **Independent & dependent events** affect probability calculations.  
✅ **Permutations & combinations** are useful in counting problems.  
✅ **Binomial distribution** is used in AI models for classification problems.  
✅ **Simulation & visualization** help validate theoretical probabilities.  

---

### **🚀 Next Steps**
Would you like to see **more advanced ML applications** using probability? Let me know! 😊

---

# Python Functions: Generating Random Numbers and Simulating Probability

## 1. Introduction to Random Number Generation

Random numbers are widely used in simulations, cryptography, and statistical modeling. In Python, the `numpy` library provides powerful functions to generate random numbers.

### Importing Required Library
```python
import numpy as np
```

## 2. Generating Random Numbers

### Standard Uniform Distribution
The `np.random.rand()` function generates random numbers from the uniform distribution between 0 and 1.
```python
np.random.rand()  # Generates a random number between 0 and 1
```

### Setting Seed for Reproducibility
Setting a seed ensures that the same sequence of random numbers is generated every time.
```python
np.random.seed(555)  # Ensures reproducibility
np.random.rand()
```

### Generating Multiple Random Numbers
```python
np.random.rand(5)  # Generates an array of 5 random numbers
```

### Simulating Coin Flips
```python
np.random.rand(5) > 0.5  # Returns a boolean array where True is considered as heads (1)
```

### Counting Number of Heads
```python
sum(np.random.rand(5) > 0.5)  # Returns the number of heads
```

## 3. Generating Random Integers

### Random Integer Generation
```python
np.random.randint(0, 2, 10)  # Generates 10 random integers (0 or 1), simulating 10 coin flips
```

### Simulating Dice Rolls
```python
np.random.randint(1, 7, 100)  # Rolls a dice 100 times
```

### Visualizing Dice Rolls
```python
import matplotlib.pyplot as plt
import seaborn as sns

np.random.seed(555)
a = np.random.randint(1, 7, 6000)
sns.countplot(x=a)
plt.xlabel("Dice Face")
plt.ylabel("Frequency")
plt.title("Distribution of Dice Rolls")
plt.show()
```

## 4. Probability of Rolling Two Dice

The probability of rolling a sum greater than 7 when rolling two dice is calculated using simulations:
```python
die1 = np.random.randint(1, 7, 1000000)
die2 = np.random.randint(1, 7, 1000000)
die_sum = die1 + die2
sum(die_sum > 7) / 1000000  # Approximates P(sum > 7)
```

## 5. Binomial Distribution

The binomial distribution models the number of successes in `n` independent Bernoulli trials with success probability `p`.
```python
np.random.binomial(1, 0.5)  # Flipping 1 coin with p(success) = 0.5
np.random.binomial(2, 0.5)  # Flipping 2 coins with p(success) = 0.5
```

### Simulating Multiple Binomial Trials
```python
np.random.binomial(2, 0.5, 1000)  # Flipping 2 coins 1000 times
```

### Visualizing Binomial Distribution
```python
sns.set_theme(style="whitegrid")
two_coins = np.random.binomial(2, 0.5, 1000)
sns.countplot(x=two_coins)
plt.xlabel("Number of Heads")
plt.ylabel("Frequency")
plt.title("Binomial Distribution of Coin Flips")
plt.show()
```

## 6. Using Scipy for Probability Calculations

### Importing `binom` from `scipy.stats`
```python
from scipy.stats import binom
```

### Understanding Key Functions
- `binom.pmf(x, n, p)`: Probability of exactly `x` successes in `n` trials.
- `binom.cdf(x, n, p)`: Probability of at most `x` successes in `n` trials.
- `binom.sf(x, n, p)`: Probability of more than `x` successes.
- `binom.mean(n, p)`: Mean of the distribution.
- `binom.var(n, p)`: Variance of the distribution.
- `binom.std(n, p)`: Standard deviation.

### Example: Acceptance Test for Defective Items
A manufacturer has a 12% defect rate. A buyer tests 20 random pieces and will accept the shipment if there are at most 2 defective items.
```python
binom.cdf(2, 20, 0.12)  # Probability of acceptance
```

### Visualizing Probability Mass Function
```python
a_ax = np.arange(0, 21)
y_ax = binom.pmf(a_ax, 20, 0.12)
sns.barplot(x=a_ax, y=y_ax)
plt.xlabel("Number of Defective Items")
plt.ylabel("Probability Mass Function")
plt.title("PMF of Defective Items in Sample")
plt.show()
```

### Exercises
1. **Flipping a fair coin 10 times:** What is the probability of getting exactly 7 heads?
   ```python
   binom.pmf(7, 10, 0.5)
   ```
2. **Probability of getting at least 7 heads in 10 flips:**
   ```python
   binom.sf(6, 10, 0.5)  # or 1 - binom.cdf(6, 10, 0.5)
   ```
3. **Defective Rate in a Selection:** Given a 10% defect rate, what is the probability of getting 0 defective pieces in a sample of 4?
   ```python
   binom.pmf(0, 4, 0.10)
   ```

## 7. Debugging Tips
- Ensure the correct use of `np.random.seed()` for reproducibility.
- Use `np.random.randint()` for discrete random variables (e.g., coin flips, dice rolls).
- Check the shape of arrays when performing vectorized operations.
- Validate theoretical probabilities with simulations.

These notes provide a structured approach to understanding probability simulations and binomial distributions in Python.

