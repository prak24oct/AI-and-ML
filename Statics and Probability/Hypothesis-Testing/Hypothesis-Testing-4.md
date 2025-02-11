# 📊 **Comprehensive Lecture Notes on Statistical Testing for AI & ML**  

These lecture notes cover **essential statistical tests used in AI & ML**, along with:  
✅ **Key concepts & assumptions**  
✅ **Mathematical formulas (LaTeX format)**  
✅ **Python implementations**  
✅ **Real-world AI & ML applications**  
✅ **Common mistakes & best practices**  

---

# **1️⃣ Introduction to Statistical Testing**  
Statistical tests are fundamental in **machine learning, data science, and AI**, helping us make **data-driven decisions** and **validate model performance**.  

### **Why Is Hypothesis Testing Important in AI & ML?**  
✔ **A/B Testing:** Comparing **two versions** of an ML model.  
✔ **Feature Selection:** Checking if a **new feature improves accuracy**.  
✔ **Algorithm Performance Comparison:** Testing whether a **new algorithm performs better** than the old one.  
✔ **Medical AI:** Validating if **an AI-powered diagnostic tool** is more accurate than doctors.  

---

# **2️⃣ One Proportion Test**  

### **✔ What Is It?**  
A **One Proportion Z-Test** is used to test whether a sample proportion is **significantly different** from a known population proportion.  

### **✔ Conditions for One Proportion Test**  
✅ Data consists of **binary outcomes** (e.g., Pass/Fail, Yes/No).  
✅ Sample size is large enough for **normal approximation**:  
   $$ np_0 \geq 10 \quad \text{and} \quad n(1 - p_0) \geq 10 $$  

### **✔ Formula for One Proportion Z-Test**  
\[
Z = \frac{p - p_0}{\sqrt{\frac{p_0(1 - p_0)}{n}}}
\]
Where:  
- $p$ = Sample proportion  
- $p_0$ = Hypothesized population proportion  
- $n$ = Sample size  

---

### **3️⃣ Python Implementation of One Proportion Test**  
#### **Case Study: Smoking Rate in a Town**  
A town had a smoking rate of **21%**. A new survey of **100 people** found **14 smokers**. Has the rate changed?  

```python
import numpy as np
from statsmodels.stats.proportion import proportions_ztest

# Given Data
p0 = 0.21  # Past smoking rate
p_hat = 14 / 100  # Sample proportion
n = 100  # Sample size

# Compute Z-Test
z_score, p_value = proportions_ztest(count=14, nobs=n, value=p0, alternative='two-sided')

# Decision
alpha = 0.05
if p_value < alpha:
    print(f"Reject H0: Smoking rate has changed (p = {p_value:.5f})")
else:
    print(f"Fail to Reject H0: No significant change in smoking rate (p = {p_value:.5f})")
```

✔ **If $p < 0.05$, reject $H_0$ and conclude the smoking rate has changed.**  

---

# **4️⃣ One Variance Test**  

### **✔ What Is It?**  
A **Chi-Square Test for Variance** checks if a sample variance is significantly different from a hypothesized population variance.  

### **✔ Conditions for One Variance Test**  
✅ Random samples  
✅ Normal distribution of data  

### **✔ Formula for One Variance Test**  
\[
\chi^2 = \frac{(n - 1) s^2}{\sigma^2}
\]
Where:  
- $s^2$ = Sample variance  
- $\sigma^2$ = Population variance  
- $n$ = Sample size  

---

### **5️⃣ Python Implementation of One Variance Test**  
#### **Case Study: Quality Control in a Factory**  
A bottle factory claims volume variation is **2cc**. A **sample of 51 bottles** has a standard deviation of **2.35cc**. Has the variation increased?  

```python
import scipy.stats as stats

# Given Data
s_squared = 2.35**2  # Sample variance
sigma_squared = 2**2  # Hypothesized variance
n = 51  # Sample size

# Compute Chi-Square Test Statistic
chi_square = ((n - 1) * s_squared) / sigma_squared

# Compute Critical Value (Right-tailed Test)
alpha = 0.10
chi_critical = stats.chi2.ppf(1 - alpha, df=n-1)

# Decision
if chi_square > chi_critical:
    print(f"Reject H0: Variance has increased (Chi-Square = {chi_square:.5f})")
else:
    print(f"Fail to Reject H0: No significant increase in variance (Chi-Square = {chi_square:.5f})")
```

✔ **If $\chi^2 > \chi_{\text{critical}}$, reject $H_0$ and conclude variance has increased.**  

---

# **6️⃣ Two Proportions Test**  

### **✔ What Is It?**  
A **Two Proportions Z-Test** compares two independent sample proportions.  

### **✔ Formula for Two Proportions Z-Test**  
\[
Z = \frac{(\hat{p}_1 - \hat{p}_2)}{\sqrt{p(1 - p) \left(\frac{1}{n_1} + \frac{1}{n_2} \right)}}
\]
Where:  
- $\hat{p}_1, \hat{p}_2$ = Sample proportions  
- $n_1, n_2$ = Sample sizes  
- $p$ = Pooled proportion  

---

### **7️⃣ Python Implementation of Two Proportions Test**  
#### **Case Study: Vendor Quality Analysis**  
Vendor A: **200 pieces**, **30 defectives**  
Vendor B: **100 pieces**, **10 defectives**  
At **95% confidence**, is there a difference in defect rates?  

```python
count = np.array([30, 10])  # Number of defectives
nobs = np.array([200, 100])  # Total samples

# Compute Z-Test
z_score, p_value = proportions_ztest(count, nobs, alternative='two-sided')

# Decision
alpha = 0.05
if p_value < alpha:
    print(f"Reject H0: Significant difference in defect rates (p = {p_value:.5f})")
else:
    print(f"Fail to Reject H0: No significant difference in defect rates (p = {p_value:.5f})")
```

✔ **If $p < 0.05$, reject $H_0$ and conclude vendors have different defect rates.**  

---

# **8️⃣ Common Mistakes & Best Practices**  
✔ **Using the wrong test:** Use **T-test** for means and **Z-test** for proportions.  
✔ **Ignoring normality assumptions:** Always check if data is **normally distributed** before using variance tests.  
✔ **Misinterpreting p-values:** $p < 0.05$ means evidence against $H_0$, but does **not** prove causation.  

---

# **9️⃣ Applications of Hypothesis Testing in AI & ML**  
✔ **A/B Testing:** Testing whether a **new recommendation algorithm** is better than the old one.  
✔ **Feature Selection:** Determining whether **a new feature improves model accuracy**.  
✔ **Fraud Detection:** Identifying whether **a pattern of transactions significantly differs from normal transactions**.  

---

# **🔟 Summary & Key Takeaways**  
✅ **One Proportion Z-Test** checks if a **sample proportion differs from the population proportion**.  
✅ **One Variance Test** verifies whether a **sample variance differs from a known variance**.  
✅ **Two Proportions Z-Test** compares **proportions from two independent samples**.  
✅ **Statistical testing is widely used in AI & ML** for **model validation, fraud detection, and feature selection**.  

---

🚀 **Would you like additional refinements, more examples, or explanations?** 😊