# Probability Distributions and Simulation in Python

This project contains theoretical and simulation-based solutions to problems involving discrete probability distributions, including:
- Binomial
- Negative Binomial
- Hypergeometric
- Poisson

Additionally, a simulation of a hypergeometric sampling process is implemented in Python.

---

### 🧠 Topics Covered

#### 📌 Q1: Binomial Distribution (Image Classification Accuracy)
- Scenario: Classifying 10 images independently with success probability `p = 0.8`
- Tasks:
  - PMF of Binomial distribution
  - P(X ≥ 8)
  - Expected Value (E[X]) and Variance (Var[X])
  - Probability of at least 9 correct classifications

#### 📌 Q2: Negative Binomial Distribution (Model Training Success)
- Scenario: Number of training attempts until second success (`p = 0.3`)
- Tasks:
  - PMF of Negative Binomial distribution
  - P(Y = 5)
  - Expected Value E[Y]

#### 📌 Q3: Hypergeometric Distribution (Sampling Spam Texts)
- Scenario: Sampling without replacement from a population with 120 spam out of 500
- Tasks:
  - PMF of Hypergeometric distribution
  - P(Z = 6)
  - E[Z] with and without replacement

#### 📌 Q4: Poisson Distribution (Helpdesk Ticket Arrival)
- Scenario: Tickets arrive at an average rate λ = 4/hour
- Tasks:
  - P(No tickets in 30 min)
  - P(More than 6 tickets in 1 hour)
  - Mean & Variance for 2-hour window

#### 📌 Q5: Simulation (Hypergeometric Sampling)
- Scenario: Draw 5 samples from a population of 20 with 7 successes
- Tasks:
  - Simulate 1000 trials
  - Plot histogram of outcomes
  - Overlay theoretical distribution

---

### 📊 Python Simulation (Q5 Snippet)
```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from math import comb

# Parameters
population_size = 20
num_successes = 7
sample_size = 5
num_simulations = 1000

# Simulate
results = np.random.hypergeometric(num_successes, population_size - num_successes, sample_size, num_simulations)

# Theoretical PMF
x = np.arange(0, min(num_successes, sample_size)+1)
pmf = [(comb(num_successes, k) * comb(population_size - num_successes, sample_size - k)) / comb(population_size, sample_size) for k in x]

# Plot
sns.histplot(results, bins=np.arange(-0.5, sample_size+1.5, 1), stat='probability', label='Simulation')
plt.scatter(x, pmf, color='red', label='Theoretical')
plt.legend()
plt.title("Hypergeometric Distribution Simulation")
plt.xlabel("Number of Successes")
plt.ylabel("Probability")
plt.grid(True)
plt.show()
