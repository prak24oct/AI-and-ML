Here’s a structured, detailed, and engaging summary of the **"Basic Probability & Probability Distributions"** document in a simplified format:

---

## 📌 **1️⃣ Probability Distributions: An Overview**  
Probability distributions describe how outcomes of a random variable are distributed. Two major types:  
- **Discrete Probability Distributions**: Countable outcomes (e.g., rolling dice, coin flips).  
- **Continuous Probability Distributions**: Infinite possible values (e.g., height, temperature).  

The document focuses on **Poisson Distribution** and **Normal Distribution**.

---

## 🎯 **2️⃣ Poisson Distribution**  

### **🔹 Definition**  
The **Poisson Distribution** models the probability of a given number of events happening in a fixed interval (time or space) when:  
- Events are **independent**.  
- The **average number** of occurrences (mean **u**) is known.  
- The number of events is **random**.  

🔸 **Real-World Examples**:  
- People arriving at a ticket counter per hour.  
- Number of car accidents at an intersection per day.  
- Number of emails received per hour.  

### **🔹 Formula**
\[
P(X, u) = \frac{e^{-u} \cdot u^X}{X!}
\]
Where:  
- **e ≈ 2.718** (Euler’s constant).  
- **u** = average number of successes per interval.  
- **X** = actual number of occurrences.  
- **P(X, u)** = probability of exactly **X** occurrences.  

### **🔹 Key Properties**  
✅ The **mean (u) and variance (u) are the same**.  
✅ Works well for **rare events** occurring over time or space.  

### **🔹 Example Calculation**  
📌 **Scenario**: On average, 3.6 people visit a booking counter every **10 minutes**. What’s the probability that **7 people** visit in the next 10 minutes?  
- **Given**:  
  - \( X = 7 \), \( u = 3.6 \).  
  - Using the Poisson formula:  
  - **P(7, 3.6) ≈ 0.0424 (4.24%)**  

🎯 **Takeaway**: Poisson is useful for predicting the likelihood of specific events happening in a given timeframe.  

---

## 🔥 **3️⃣ Normal Distribution (Gaussian Distribution)**  

### **🔹 Definition**  
A **Normal Distribution** describes **continuous** data where values cluster symmetrically around the mean. It follows a **bell-shaped curve**.  

🔹 **Examples**:
- Heights of people.  
- Exam scores in a large class.  
- Daily temperature variations.  

### **🔹 Properties**  
✅ **Symmetric** around the mean.  
✅ **Mean = Median = Mode** (for perfectly normal distributions).  
✅ Defined by **two parameters**:  
  - **Mean (μ)** → The central value.  
  - **Standard Deviation (σ)** → How much data spreads from the mean.  

### **🔹 68-95-99.7 Rule (Empirical Rule)**  
This rule tells how much data falls within standard deviations:  
- **68%** within **1σ**.  
- **95%** within **2σ**.  
- **99.7%** within **3σ**.  

### **🔹 Z-Score (Standard Score)**
A **Z-score** standardizes values to compare different normal distributions.

\[
Z = \frac{X - \mu}{\sigma}
\]
Where:  
- **X** = observed value.  
- **μ** = mean.  
- **σ** = standard deviation.  

📌 **Example**  
Perfume bottles have an **average volume** of **150cc** and a **standard deviation of 2cc**.  
What percentage of bottles have a volume **greater than 153cc**?  

- Given: \( X = 153, \mu = 150, \sigma = 2 \)  
- **Z-score Calculation**:
  \[
  Z = \frac{153 - 150}{2} = 1.5
  \]
- **Interpretation**: Find **P(Z > 1.5)** in a Z-table to get the probability.

🎯 **Takeaway**: The Z-score helps determine how far a value is from the mean and estimate probabilities.

---

## ✏️ **4️⃣ Practice Questions**  
💡 **Poisson Distribution**  
1️⃣ A small café receives an average of **5 orders per minute**. What’s the probability of receiving **8 orders in the next minute**?  

💡 **Normal Distribution**  
2️⃣ A university’s test scores have a **mean of 70** and **σ = 5**. What percentage of students scored **above 80**?  

---

## 🚀 **5️⃣ Summary & Key Takeaways**  
✔ **Poisson Distribution** is used for **discrete rare events** in a fixed interval. Mean and variance are equal.  
✔ **Normal Distribution** is used for **continuous data**, forming a symmetric bell curve.  
✔ **Z-score** helps compare and calculate probabilities for normal distributions.  

These probability distributions play a crucial role in **data science, machine learning, and real-world predictions**! 🎯

---

Let me know if you need any modifications! 🚀