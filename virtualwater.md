---
layout: inner
title: "💧 Virtual Water Trade and Global Water Scarcity"
permalink: /virtualwater/
---


# 💡 1. Research Question and Research Gap
<br><br>
### **What is the structure of the virtual water trade network between major countries in the world?**
<br><br>
Previous studies have primarily focused on virtual water trade related to **agricultural products**.  
Also, most of them have simply compared the total import and export volumes by country.
This study introduces a methodology called **Social Network Analysis**  
to quantitatively analyze the structural characteristics of virtual water trade,  
and provides an integrated analysis of virtual water trade networks across the **entire industrial structure**.


---
<br><br>
# 🌊 2. Introduction

### **Why is virtual water trade important?**

Water is a key resource that supports all industries, agriculture, and daily life.  
However, the problem is that water is very disproportionately distributed among countries.

That’s where the concept of Virtual Water Trade comes in.  
It refers to the idea that when we trade goods, we are also indirectly trading the water used to produce them.

This study shows how virtual water trade plays a role in solving water shortages between countries  
and explores how the global trade network is connected in terms of virtual water flows.

---
<br><br>
# 🔧 3. Methods and Data Sources

## 💡 How is *Virtual Water* calculated?

This study estimates inter-country virtual water flows using a **Multi-Regional Input–Output (MRIO) model**.  
Here’s how it works:

### 📌 Step 1. Direct Water Coefficient

\\[
w_i^r = \frac{W_i^r}{X_i^r}
\\]

- \\(W_i^r\\): Water consumed by industry *i* in country *r*  
- \\(X_i^r\\): Total output of industry *i* in country *r*  
👉 Indicates **how much water is used to produce one unit of output**

---

### 📌 Step 2. Input–Output Balance Equation

\\[
AX + Y = X
\\]

- \\(A\\): Input coefficient matrix (inter-industry consumption)  
- \\(X\\): Total output vector  
- \\(Y\\): Final demand vector  
➡️ Ensures that total output equals intermediate + final consumption

---

### 📌 Step 3. Leontief Inverse Matrix

\\[
X = (I - A)^{-1}Y = LY
\\]

- \\(L = (I - A)^{-1}\\): Leontief inverse matrix  
➡️ Captures both **direct and indirect** production requirements

---

### 📌 Step 4. Virtual Water Trade Matrix

\\[
H = \hat{W} \cdot L \cdot Z
\\]

- \\(\hat{W}\\): Diagonal matrix of direct water coefficients  
- \\(L\\): Leontief inverse  
- \\(Z\\): Final goods traded between countries  
➡️ This matrix estimates **indirect virtual water flows** across borders

---

### 📌 Step 5. Virtual Water Network Matrix

\\[
T = H
\\]

- \\(t_{rs}\\): Virtual water *exported* from country *r* to country *s*  
➡️ **Off-diagonal elements** show bilateral virtual water trade

---

## 📊 4. Network Analysis: How Virtual Water Trade is Structured

To analyze the structure of the virtual water trade, this study applies **social network metrics**:

---

### ✅ Density (Network Connectivity)

\\[
D = \frac{\sum_{r \neq s} \sum_{s=1}^{m} t_{rs}}{m(m - 1)}
\\]

- Measures how densely connected the virtual water network is  
- **Higher values = more active trade across countries**

---

### ✅ Asymmetry (Trade Imbalance)

\\[
S = \frac{\sum_{r \neq s} \sum_{s=1}^{m} |t_{rs} - t_{sr}|}{m(m - 1)}
\\]

- Captures the **imbalance** between exports and imports  
- High values = unidirectional or one-sided trade

---

### ✅ Out-Degree (Virtual Water Exports)

\\[
OD_r = \sum_{s \neq r} t_{rs}
\\]

- Total virtual water **exported** by country *r*  
- Indicates water-exporting hubs

---

### ✅ In-Degree (Virtual Water Imports)

\\[
ID_r = \sum_{s \neq r} t_{sr}
\\]

- Total virtual water **imported** into country *r*  
- High values suggest **greater water dependency**

---

## 🌍 5. Data Source

The analysis uses the **EORA Global MRIO Database**:

- 🧭 **Countries**: 190  
- 🏭 **Sectors**: 26 industries  
- 📅 **Years**: 1990–2015  
- 💧 **Water Types**: Green, Blue, and Grey water  
- 🎯 **Focus**: 2006–2015, **G20 countries** (excluding the EU)

🔗 [EORA Official Site](https://worldmrio.com/)

➡️ The data provides water use by sector and country, enabling detailed mapping of **virtual water embedded in trade**.

---

🧩 **In summary**, this methodology quantifies the hidden water flows behind global trade  
and visualizes them as a **network**, enabling analysis of structure, dependencies, and imbalance.

