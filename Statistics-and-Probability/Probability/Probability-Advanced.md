# 📈 Advanced Probability Concepts

## 1. Stochastic Processes

### Markov Chains

```python
import numpy as np
import matplotlib.pyplot as plt

class MarkovChain:
    def __init__(self, transition_matrix, states):
        self.transition_matrix = np.array(transition_matrix)
        self.states = states
        self.current_state = None

    def set_state(self, state):
        if state in self.states:
            self.current_state = state
        else:
            raise ValueError("Invalid state")

    def next_state(self):
        if self.current_state is None:
            raise ValueError("No current state set")

        current_index = self.states.index(self.current_state)
        next_index = np.random.choice(
            len(self.states),
            p=self.transition_matrix[current_index]
        )
        self.current_state = self.states[next_index]
        return self.current_state

# Example: Weather Markov Chain
weather_states = ['Sunny', 'Rainy', 'Cloudy']
transition_matrix = [
    [0.6, 0.2, 0.2],  # Sunny
    [0.3, 0.4, 0.3],  # Rainy
    [0.4, 0.1, 0.5]   # Cloudy
]

# Create and simulate Markov chain
mc = MarkovChain(transition_matrix, weather_states)
mc.set_state('Sunny')

# Simulate 100 days
days = 100
weather_sequence = []
for _ in range(days):
    weather_sequence.append(mc.next_state())

# Plot results
plt.figure(figsize=(10, 4))
plt.plot(range(days), weather_sequence, 'o-')
plt.title('Weather Simulation Over 100 Days')
plt.xlabel('Day')
plt.ylabel('Weather')
plt.yticks(range(len(weather_states)), weather_states)
plt.grid(True)
plt.show()
```

### Poisson Process

```python
def simulate_poisson_process(rate, time_interval):
    """Simulate a Poisson process with given rate over time interval"""
    events = []
    current_time = 0

    while current_time < time_interval:
        # Generate time until next event
        time_to_next = np.random.exponential(1/rate)
        current_time += time_to_next

        if current_time < time_interval:
            events.append(current_time)

    return events

# Simulate Poisson process
rate = 2  # events per unit time
time_interval = 10
events = simulate_poisson_process(rate, time_interval)

# Plot
plt.figure(figsize=(10, 2))
plt.eventplot(events, orientation='horizontal', colors='black')
plt.title('Poisson Process Simulation')
plt.xlabel('Time')
plt.yticks([])
plt.grid(True)
plt.show()
```

## 2. Monte Carlo Methods

### Monte Carlo Integration

```python
def monte_carlo_integration(f, a, b, n_samples=10000):
    """Estimate integral of f from a to b using Monte Carlo"""
    x = np.random.uniform(a, b, n_samples)
    y = f(x)
    integral = (b - a) * np.mean(y)
    return integral

# Example: Integrate sin(x) from 0 to π
def f(x):
    return np.sin(x)

true_integral = 2  # ∫sin(x)dx from 0 to π = 2
estimated_integral = monte_carlo_integration(f, 0, np.pi)
print(f"True integral: {true_integral:.3f}")
print(f"Estimated integral: {estimated_integral:.3f}")
```

### Importance Sampling

```python
def importance_sampling(f, p, q, n_samples=10000):
    """Estimate E[f(X)] where X ~ p using importance sampling with q"""
    x = q.rvs(n_samples)
    weights = p.pdf(x) / q.pdf(x)
    estimate = np.mean(f(x) * weights)
    return estimate

# Example: Estimate E[X²] where X ~ N(0,1)
from scipy.stats import norm

def f(x):
    return x**2

p = norm(0, 1)  # Target distribution
q = norm(1, 1)  # Proposal distribution

true_expectation = 1  # E[X²] = Var(X) + E[X]² = 1 + 0 = 1
estimated_expectation = importance_sampling(f, p, q)
print(f"True expectation: {true_expectation:.3f}")
print(f"Estimated expectation: {estimated_expectation:.3f}")
```

## 3. Bayesian Inference

### Conjugate Priors

```python
def bayesian_update(prior_alpha, prior_beta, data):
    """Update Beta prior with binomial data"""
    successes = sum(data)
    failures = len(data) - successes
    posterior_alpha = prior_alpha + successes
    posterior_beta = prior_beta + failures
    return posterior_alpha, posterior_beta

# Example: Coin flip experiment
prior_alpha = 1  # Uniform prior
prior_beta = 1
data = [1, 0, 1, 1, 0]  # 1 = heads, 0 = tails

posterior_alpha, posterior_beta = bayesian_update(prior_alpha, prior_beta, data)

# Plot prior and posterior
x = np.linspace(0, 1, 100)
prior = stats.beta(prior_alpha, prior_beta).pdf(x)
posterior = stats.beta(posterior_alpha, posterior_beta).pdf(x)

plt.plot(x, prior, label='Prior')
plt.plot(x, posterior, label='Posterior')
plt.title('Bayesian Update of Beta Distribution')
plt.xlabel('Probability of Heads')
plt.ylabel('Density')
plt.legend()
plt.grid(True)
plt.show()
```

## 4. Markov Chain Monte Carlo (MCMC)

### Metropolis-Hastings Algorithm

```python
def metropolis_hastings(target_pdf, proposal_pdf, proposal_rvs, n_samples=10000):
    """Metropolis-Hastings algorithm for MCMC sampling"""
    samples = []
    current = proposal_rvs()

    for _ in range(n_samples):
        # Propose new state
        proposed = proposal_rvs()

        # Calculate acceptance ratio
        ratio = (target_pdf(proposed) * proposal_pdf(current)) / \
                (target_pdf(current) * proposal_pdf(proposed))
        alpha = min(1, ratio)

        # Accept or reject
        if np.random.random() < alpha:
            current = proposed

        samples.append(current)

    return samples

# Example: Sample from N(0,1) using N(x,1) as proposal
target_pdf = lambda x: stats.norm(0, 1).pdf(x)
proposal_pdf = lambda x: stats.norm(x, 1).pdf(x)
proposal_rvs = lambda: np.random.normal(0, 1)

samples = metropolis_hastings(target_pdf, proposal_pdf, proposal_rvs)

# Plot results
plt.hist(samples, bins=50, density=True, alpha=0.5)
x = np.linspace(-4, 4, 100)
plt.plot(x, stats.norm(0, 1).pdf(x), 'r-')
plt.title('MCMC Sampling from Normal Distribution')
plt.xlabel('Value')
plt.ylabel('Density')
plt.grid(True)
plt.show()
```

## 5. Best Practices

### Stochastic Process Modeling

- Choose appropriate process type
- Validate model assumptions
- Check stationarity
- Consider multiple models

### Monte Carlo Methods

- Use appropriate sampling techniques
- Check convergence
- Consider variance reduction
- Validate results

### Bayesian Analysis

- Choose appropriate priors
- Check posterior convergence
- Validate model assumptions
- Consider model comparison

### Common Pitfalls

- Ignoring convergence issues
- Using inappropriate proposal distributions
- Not checking model assumptions
- Misinterpreting results

---

This file covers advanced probability concepts and their applications. For more basic topics, refer to the other modules in this series.
