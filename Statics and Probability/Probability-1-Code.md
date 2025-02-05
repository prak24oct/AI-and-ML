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

