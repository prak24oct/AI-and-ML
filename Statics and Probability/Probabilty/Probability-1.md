Here are the structured notes from the provided PDF on **Basic Probability & Probability Distributions**:

---

### 1️⃣ **Introduction to Probability**

- **Probability** is the measure of the likelihood that an event will occur.
  - **Classic Model**: 
    \[
    \text{Probability} = \frac{\text{Number of favorable outcomes}}{\text{Total number of possible outcomes}}
    \]

- **Relative Frequency**:
  \[
  \text{Relative Frequency} = \frac{\text{Number of times an event occurred}}{\text{Total number of opportunities for the event}}
  \]

- **Venn Diagrams** are used to visualize relationships between events. For example, in rolling a die:
  - Event A: Getting 1 or 4.
  - Event C: Getting 2, 3, 5, or 6.

### 2️⃣ **Types of Events**

- **Mutually Exclusive Events**: Events that cannot occur at the same time (e.g., getting 1 and 4 simultaneously when rolling a die).
- **Independent Events**: The occurrence of one event does not affect the probability of the other (e.g., flipping two coins).
- **Dependent Events**: The outcome of one event affects the probability of the other (e.g., drawing cards without replacement).
- **Complementary Events**: If an event A occurs, its complement \( P(A') \) represents the probability that A does *not* occur.

---

### 3️⃣ **Key Probability Rules**

- **Rule of Addition** (for non-mutually exclusive events):
  \[
  P(A \cup B) = P(A) + P(B) - P(A \cap B)
  \]

- **Rule of Multiplication** (for independent events):
  \[
  P(A \cap B) = P(A) \times P(B|A)
  \]

---

### 4️⃣ **Permutations & Combinations**

- **Factorial**:
  \[
  n! = n \times (n-1) \times (n-2) \times \dots \times 1
  \]
  - Example: \( 5! = 5 \times 4 \times 3 \times 2 \times 1 = 120 \)
  
- **Permutation**: A set of objects where order matters.
  - Example: Arranging 3 people as captain, vice-captain, and treasurer from 5 people.
  - Formula for permutation without repetition:
    \[
    P(n, r) = \frac{n!}{(n - r)!}
    \]
  
- **Combination**: A set of objects where order does not matter.
  - Example: Selecting 3 people from 5.
  - Formula for combination:
    \[
    C(n, r) = \frac{n!}{(n - r)! \times r!}
    \]

---

### 5️⃣ **Practice Questions**

- **Q1**: What is the probability of getting heads in two coin flips?
  - **Answer**: \( \frac{1}{4} \), as there are 4 possible outcomes (HH, HT, TH, TT), and only 1 is heads in both flips.
  
- **Q2**: What is the probability of getting a sum of 8 when rolling two dice?
  - **Answer**: The probability of getting a sum of 8 is \( \frac{5}{36} \) since there are 5 possible outcomes for a sum of 8 (2,6), (3,5), (4,4), (5,3), (6,2).

---

### 6️⃣ **Probability Distribution**

- **Discrete Probability Distribution**: A distribution where the outcomes are discrete (e.g., rolling a die).
- **Binomial Distribution**:
  - It describes the number of successes in a fixed number of independent trials, each with the same probability of success.
  - Example: If you flip a coin 4 times, what is the probability of getting exactly 1 head?
  - **Formula for Binomial Probability**:
    \[
    P(X = x) = \binom{n}{x} p^x (1-p)^{n-x}
    \]
    Where:
    - \( n \) = number of trials
    - \( p \) = probability of success on a single trial
    - \( x \) = number of successes
  
  - **Example**: For flipping a coin 4 times (n = 4, p = 0.5), the probability of 1 head is:
    \[
    P(X = 1) = \binom{4}{1} (0.5)^1 (0.5)^3 = 0.25
    \]

---

### 7️⃣ **Summary & Key Takeaways**

- **Probability** measures how likely an event is to occur, with values between 0 and 1.
- Key events like **independent, dependent, mutually exclusive, and complementary** shape the probability of occurrences.
- **Addition and multiplication rules** help calculate combined probabilities.
- **Permutations and combinations** help solve problems involving order and selection.
- **Binomial distribution** is crucial for modeling scenarios with two possible outcomes across several trials.

