---
layout: inner
title: "💧 Virtual Water Trade and Global Water Scarcity"
permalink: /virtualwater/
---
<br><br>
# Deng et al.(2021): Social network analysis of virtual water trade among major countries in the world
<br><br>
## 💡 1. Research Question and Research Gap

### **What is the structure of the virtual water trade network between major countries in the world?**

Previous studies have primarily focused on virtual water trade related to **agricultural products**. Also, most of them have simply compared the total import and export volumes by country. This study introduces a methodology called **Social Network Analysis** to quantitatively analyze the structural characteristics of virtual water trade and provides an integrated analysis of virtual water trade networks across the entire industrial structure.

---
<br><br>
## 🌊 2. Introduction

### **Why is virtual water trade important?**

Water is a key resource that supports all industries, agriculture, and daily life. However, the problem is that water is very disproportionately distributed among countries. That’s where the concept of Virtual Water Trade comes in. It refers to the idea that when we trade goods, we are also indirectly trading the water used to produce them. This study shows how virtual water trade plays a role in solving water shortages between countries and explores how the global trade network is connected in terms of virtual water flows.

---
<br><br>
## 🔧 3. Methods and Data Sources

### 💡 How is *Virtual Water* calculated?

This study estimates inter-country virtual water flows using a **Multi-Regional Input–Output (MRIO) model**.  

#### Direct Water Coefficient

\\[
w_i^r = \frac{W_i^r}{X_i^r}
\\]

- \\(W_i^r\\): Water consumed by industry *i* in country *r*  
- \\(X_i^r\\): Total output of industry *i* in country *r*  
-> how much water is used to produce one unit of output

---

#### Input–Output Balance Equation

\\[
AX + Y = X
\\]

- \\(A\\): Input coefficient matrix (inter-industry consumption)  
- \\(X\\): Total output vector  
- \\(Y\\): Final demand vector  
-> Total output equals intermediate + final consumption

---

#### Leontief Inverse Matrix

\\[
X = (I - A)^{-1}Y = LY
\\]

- \\(L = (I - A)^{-1}\\): Leontief inverse matrix  
-> Both direct and indirect production requirements

---

#### Virtual Water Trade Matrix

\\[
H = \hat{W} \cdot L \cdot Z
\\]

- \\(\hat{W}\\): Diagonal matrix of direct water coefficients  
- \\(L\\): Leontief inverse  
- \\(Z\\): Final goods traded between countries  
-> estimate indirect virtual water flows across borders

---

#### Virtual Water Network Matrix

\\[
T = H
\\]

- \\(t_{rs}\\): Virtual water *exported* from country *r* to country *s*  
-> Off-diagonal elements show bilateral virtual water trade

---

## 📊 4. Network Analysis: How Virtual Water Trade is Structured

To analyze the structure of the virtual water trade, this study applies **social network metrics**:

---

#### Density (Network Connectivity)

\\[
D = \frac{\sum_{r \neq s} \sum_{s=1}^{m} t_{rs}}{m(m - 1)}
\\]

- Measures how densely connected the virtual water network is  
- Higher values = more active trade across countries

---

#### Asymmetry (Trade Imbalance)

\\[
S = \frac{\sum_{r \neq s} \sum_{s=1}^{m} |t_{rs} - t_{sr}|}{m(m - 1)}
\\]

- Capture the imbalance between exports and imports  
- High values = unidirectional or one-sided trade

---

#### Out-Degree (Virtual Water Exports)

\\[
OD_r = \sum_{s \neq r} t_{rs}
\\]

- Total virtual water exported by country r 
- Indicates water-exporting hubs

---

#### In-Degree (Virtual Water Imports)

\\[
ID_r = \sum_{s \neq r} t_{sr}
\\]

- Total virtual water imported into country r 
- High values suggest greater water dependency

---

## 🎯 5. Result and Interpretation

Global virtual water trade has continuously increased from 2006 to 2015. Both virtual water exports and imports increased significantly from 2006 to 2015, showing a clear growth in global trade among major countries.

**<Network by Out-Degree (2015)>**  
![Out-Degree Network](/img/posts/fig2.png)

- The Out-Degree network shows countries that exported large amounts of virtual water to others.
- China and India had the largest outflows, shown by the largest node sizes and thick outbound links.
- This indicates that these countries acted as central suppliers in the global virtual water trade network.


**<Network by In-Degree (2015)>**  
![In-Degree Network](/img/posts/fig3.png)

- The In-Degree network focuses on countries with high virtual water imports.
- The United States and Japan had the biggest consumers, shown by the largest node sizes and thick incoming links.
- These countries had strong dependencies on foreign water resources embedded in traded goods.

---

## 📍 6. Conclusions

- Virtual water trade can be an important way to reduce water resource differences between countries around the world
- Using Social Network Analysis, this study identifies key structural features of virtual water flows and highlights central players in the trade network.
- As a result of the analysis, China is a major exporter and the United States is a major importer, serving as a key hub for the virtual water network.
- In particular, virtual water trade was the most active in the agricultural sector, suggesting that trade strategies in the agricultural sector are important in policy.

---
<br><br>

## A Network Analysis of Global Wine🍷 and Beer🍺 Trade


## 📦 Data Introduction

#### Data Sources
- The dataset was obtained from the [FAOSTAT](https://www.fao.org/faostat/en/#data) platform.
- Trade Data:
  `Trade_DetailedTradeMatrix_E_All_Data_(Normalized).csv` <br>
  Wine & Beer made from malt <br>
  Used to construct the edges of the network <br>

  
- Node Data:  
  - `Population_E_All_Data_(Normalized).csv`  
    → Selected element: `Total Population - Both sexes`  
  - `Macro-Statistics_Key_Indicators_E_All_Data_(Normalized).csv`  
    → Selected element: `Value US$ per capita (GDP per Capita)`  
  - `Investment_ForeignDirectInvestment_E_All_Data_(Normalized).csv`  
    → Selected item: `Total FDI inflows`, element: `Value US$`

These datasets were merged to add economic and demographic context to each country (node) in the network.


