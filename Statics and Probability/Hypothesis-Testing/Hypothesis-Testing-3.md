# 📊 **Hypothesis Testing in AI & ML**  

## **1️⃣ Introduction to Hypothesis Testing**  
Hypothesis testing is a **statistical method** used to determine whether there is enough evidence in a **sample** to infer a condition for the **entire population**. It is widely used in **AI & ML model validation, A/B testing, medical research, and data-driven decision-making**.  

✔ **Example in AI & ML**:  

- Comparing the accuracy of **two ML models**.  
- Testing if a **new AI recommendation algorithm** is more effective than the existing one.  

---

## **2️⃣ Key Terms in Hypothesis Testing**  

### **✔ Null & Alternative Hypothesis**
- **Null Hypothesis ($H_0$):** Assumes no significant difference between two groups.  
- **Alternative Hypothesis ($H_a$):** Assumes a significant difference between two groups.  

### **✔ Significance Level ($\alpha$)**  
- Typically **0.05** (5%), meaning we accept **5% probability of making a Type I error** (false positive).  

### **✔ P-value Interpretation**  
- If **$p < \alpha$**, reject $H_0$ (significant difference exists).  
- If **$p \geq \alpha$**, fail to reject $H_0$ (no evidence for difference).  

---

## **3️⃣ Two-Sample Hypothesis Tests**  
When comparing two groups, we use:  
✔ **Z-test** (for **large sample sizes**, $n \geq 30$)  
✔ **T-test** (for **small sample sizes**, $n < 30$)  

---

## **4️⃣ Two-Sample Z-Test**  

### **✔ Conditions for Z-Test**  
✅ Random samples  
✅ Independent observations  
✅ Sample size $n \geq 30$  
✅ Population standard deviation is **known**  

### **✔ Formula for Two-Sample Z-Test**  
\[
Z = \frac{(\bar{X_1} - \bar{X_2})}{\sqrt{\frac{\sigma_1^2}{n_1} + \frac{\sigma_2^2}{n_2}}}
\]
Where:  
- $\bar{X_1}$, $\bar{X_2}$ = Sample means  
- $\sigma_1, \sigma_2$ = Population standard deviations  
- $n_1, n_2$ = Sample sizes  

---

### **5️⃣ Python Implementation of Z-Test**
#### **Case Study: Comparing Two Machines Producing Bottles**  

**Problem:**  
- Machine 1 produces bottles with a mean volume of **151.2 ml**, std **2.1 ml**, sample size **100**.  
- Machine 2 produces bottles with a mean volume of **151.9 ml**, std **2.2 ml**, sample size **100**.  
- At **95% confidence**, test if the machines are significantly different.  

```python
import numpy as np
from scipy import stats

# Given Data
mean1, std1, n1 = 151.2, 2.1, 100
mean2, std2, n2 = 151.9, 2.2, 100

# Compute Z-Score
z_score = (mean1 - mean2) / np.sqrt((std1**2 / n1) + (std2**2 / n2))

# Compute P-Value
p_value = 2 * (1 - stats.norm.cdf(abs(z_score)))

# Decision
alpha = 0.05
if p_value < alpha:
    print(f"Reject H0: Machines produce significantly different bottle volumes (p = {p_value:.5f})")
else:
    print(f"Fail to Reject H0: No significant difference in machine output (p = {p_value:.5f})")
```

✔ If **$p < 0.05$**, reject $H_0$ (the machines produce significantly different outputs).  

---

## **6️⃣ Two-Sample T-Test**  

### **✔ Conditions for T-Test**  
✅ Random samples  
✅ Independent observations  
✅ Sample size **$n < 30$**  
✅ Population standard deviation is **unknown**  

### **✔ Formula for Two-Sample T-Test**  
\[
T = \frac{(\bar{X_1} - \bar{X_2})}{\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}}
\]
Where:  
- $\bar{X_1}$, $\bar{X_2}$ = Sample means  
- $s_1, s_2$ = Sample standard deviations  
- $n_1, n_2$ = Sample sizes  

---

### **7️⃣ Python Implementation of T-Test**  
#### **Case Study: Comparing Student Test Scores**  

**Problem:**  
- School A: [78, 85, 82, 88, 90]  
- School B: [76, 80, 79, 85, 89]  
- Test if School A students perform significantly better than School B at **95% confidence**.  

```python
from scipy.stats import ttest_ind

# Given Data
school_A = [78, 85, 82, 88, 90]
school_B = [76, 80, 79, 85, 89]

# Perform T-Test
t_stat, p_value = ttest_ind(school_A, school_B)

# Decision
alpha = 0.05
if p_value < alpha:
    print(f"Reject H0: The two schools have significantly different scores (p = {p_value:.5f})")
else:
    print(f"Fail to Reject H0: No significant difference in student scores (p = {p_value:.5f})")
```

✔ If **$p < 0.05$**, reject $H_0$ (significant difference in student performance).  

---

## **8️⃣ Common Mistakes & Best Practices**  
✔ **Using the wrong test:** Use **T-test** when sample size is small ($n < 30$) and **Z-test** for large samples ($n \geq 30$).  
✔ **Interpreting p-values incorrectly:** $p < 0.05$ means there is evidence against $H_0$, but does not prove causation.  
✔ **Ignoring assumptions:** Always check for **normality, independence, and equal variance**.  

---

## **9️⃣ Applications of Hypothesis Testing in AI & ML**  
✔ **A/B Testing:** Testing whether a new ML model performs better than an existing model.  
✔ **Feature Selection:** Checking if a new feature significantly improves model accuracy.  
✔ **Medical AI Applications:** Testing if an AI-powered diagnostic tool is significantly better than human doctors.  

---

## **🔟 Summary & Key Takeaways**  
✅ **Z-Test** is used for **large samples ($n \geq 30$)** and when **population standard deviation is known**.  
✅ **T-Test** is used for **small samples ($n < 30$)** when **population standard deviation is unknown**.  
✅ **If $p < 0.05$**, we reject $H_0$ and conclude a **statistically significant difference** exists.  
✅ **Hypothesis testing is widely used in AI & ML** for model evaluation, A/B testing, and feature importance analysis.  

---

## **📌 Practice Questions**  
1️⃣ **Which test should be used if comparing two ML models on a dataset with 50 samples?**  
   - ✅ **Answer:** Two-Sample **T-Test** (since population std is unknown).  

2️⃣ **A study finds $p = 0.02$ when comparing two fraud detection algorithms. What does this mean?**  
   - ✅ **Answer:** Reject $H_0$, meaning the two fraud detection models perform significantly differently.  

---

🚀 **Would you like additional refinements or further examples?** 😊