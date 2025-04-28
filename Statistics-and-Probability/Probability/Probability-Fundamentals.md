# 🎲 Probability Fundamentals

## 1. Introduction to Probability

### What is Probability?

- Probability is the measure of the likelihood that an event will occur
- Ranges from 0 (impossible) to 1 (certain)
- Essential for understanding uncertainty and making predictions

### Key Concepts

- Sample Space and Events
- Probability Axioms
- Basic Probability Rules
- Independence and Dependence

## 2. Basic Probability

### Probability Rules

```python
import numpy as np

# Sample space
sample_space = {'H', 'T'}  # Coin toss

# Probability of an event
def probability(event, sample_space):
    return len(event) / len(sample_space)

# Example: Probability of heads
event = {'H'}
p_heads = probability(event, sample_space)  # 0.5
```

### Addition Rule

```python
# P(A or B) = P(A) + P(B) - P(A and B)
def addition_rule(p_a, p_b, p_a_and_b):
    return p_a + p_b - p_a_and_b

# Example: Probability of rolling 1 or 2 on a die
p_1 = 1/6
p_2 = 1/6
p_1_and_2 = 0  # Mutually exclusive
p_1_or_2 = addition_rule(p_1, p_2, p_1_and_2)  # 1/3
```

## 3. Conditional Probability

### Basic Conditional Probability

```python
# P(A|B) = P(A and B) / P(B)
def conditional_probability(p_a_and_b, p_b):
    return p_a_and_b / p_b

# Example: Probability of drawing a heart given it's red
p_heart_and_red = 13/52  # All hearts are red
p_red = 26/52
p_heart_given_red = conditional_probability(p_heart_and_red, p_red)  # 0.5
```

### Bayes' Theorem

```python
# P(A|B) = P(B|A) * P(A) / P(B)
def bayes_theorem(p_b_given_a, p_a, p_b):
    return (p_b_given_a * p_a) / p_b

# Example: Disease testing
p_disease = 0.01
p_positive_given_disease = 0.99
p_positive_given_no_disease = 0.05
p_positive = (p_positive_given_disease * p_disease +
             p_positive_given_no_disease * (1 - p_disease))
p_disease_given_positive = bayes_theorem(p_positive_given_disease, p_disease, p_positive)
```

## 4. Random Variables

### Discrete Random Variables

```python
from scipy import stats

# Binomial Distribution
n, p = 10, 0.5
binomial = stats.binom(n, p)
print(binomial.pmf(5))  # Probability of 5 successes

# Poisson Distribution
lambda_ = 3
poisson = stats.poisson(lambda_)
print(poisson.pmf(2))  # Probability of 2 events
```

### Continuous Random Variables

```python
# Normal Distribution
mu, sigma = 0, 1
normal = stats.norm(mu, sigma)
print(normal.pdf(0))  # Probability density at 0

# Exponential Distribution
lambda_ = 1
exponential = stats.expon(scale=1/lambda_)
print(exponential.pdf(1))  # Probability density at 1
```

## 5. Expected Value and Variance

### Expected Value

```python
# Discrete case
def expected_value(values, probabilities):
    return np.sum(values * probabilities)

# Example: Expected value of a die roll
values = np.array([1, 2, 3, 4, 5, 6])
probabilities = np.array([1/6] * 6)
e_x = expected_value(values, probabilities)  # 3.5
```

### Variance

```python
def variance(values, probabilities, expected_value):
    return np.sum(probabilities * (values - expected_value)**2)

# Example: Variance of a die roll
var_x = variance(values, probabilities, e_x)  # 2.92
```

## 6. Best Practices

### Probability Calculations

- Define sample space clearly
- Check for independence
- Use appropriate probability rules
- Validate calculations

### Common Pitfalls

- Confusing independence with mutual exclusivity
- Misapplying probability rules
- Ignoring conditional probabilities
- Not checking assumptions

---

This file covers fundamental probability concepts. For more advanced topics, refer to the other modules in this series.
