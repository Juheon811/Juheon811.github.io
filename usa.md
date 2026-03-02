---
layout: inner
title: "U.S. vs OECD: GDP, Employment, and Income Inequality (2015–2022)"
permalink: /usa/
---

# 📊 GDP Growth, Employment, and Income Inequality  
## A Comparison of the United States (2015–2022) and the OECD

---
<br><br>

## 💡 1. Research Question 
### How did the relationship between GDP growth, employment rate, and income inequality in the United States from 2015 to 2022 differ from the OECD?

The OECD countries experienced different paths of growth, employment, and inequality between 2015 and 2022. The United States is often described as having strong economic growth but higher inequality than other countries.

Did the relationship between GDP growth, employment, and inequality in the United States follow the OECD pattern, or did it diverge in a unique way?

---

<br><br>

## 🌊 2. Introduction
This study examines the relationship between GDP growth, employment rate (ages 15–64), and income inequality (Gini) from 2015 to 2022. During this period, the global economy experienced steady growth, the shock of COVID-19, and a rapid recovery.In general, economic growth is expected to create jobs and reduce inequality. However, it is not clear whether this pattern applies to the United States. In particular, even if employment increases, inequality may not always decrease. Therefore, this study directly compares the United States and the OECD average using the same period and the same indicators. By analyzing the three variables together, this research examines whether the U.S. follows the OECD pattern or shows a different structural trend. It focuses on clearly showing how growth, employment, and inequality moved during 2015–2022 and how the United States differs from the OECD.

---

<br><br>

## 📚 3. Background Context
Previous research suggests that income inequality can weaken long-term economic growth, especially when lower-income groups fall behind in education, investment opportunities, and consumption. At the same time, many studies argue that employment expansion may help reduce inequality by increasing labor income and improving access to economic opportunities. However, most existing research tends to analyze these relationships separately focusing either on growth and inequality, or employment and inequality — rather than examining all three variables together. In addition, many major studies were conducted before the COVID-19 pandemic, meaning they do not fully capture the structural shocks and recovery patterns between 2020 and 2022. Few studies directly compare the United States and the OECD using harmonized indicators over the same time frame. This leaves an important gap in understanding whether the U.S. follows the broader OECD pattern, or whether it operates under a structurally different economic dynamic.

---

<br><br>

## 📦 4. Data Overview 

The dataset used in this study comes from the OECD Data Explorer portal, the offical statistical platform of the Organisation for Economic Co-operation and Development (OECD). The OECD Data Explorer provides comparable economic, labor, and social statistics from all member countries. This study focuses on three key annual indicators which are GDP growth, employment rate, and income inequality (Gini) from 2015 to 2022. 

The GDP growth is calculated based on national accounts compiled by OECD member countries and represents the annual percentage change in real Gross Domestic Product (GDP). It reflects economic expansion or contraction. The employment rate is calculated from labor force survey data in each country using standard definitions adjusted by the OECD and represents the percentage of the working age population aged 15 to 64. The Gini coefficient is an indicator of income inequality and is calculated from household income survey data adjusted for comparison between countries. This value is located between 0 (complete equality) and 1 (maximum inequality) and reflects the degree of imbalance in the distribution of disposable income.

All datasets were downloaded in CSV format directly from the OECD Data Explorer and merged using R by matching the country and year variables. The final cleaned dataset includes 37 OECD member countries from 2015 to 2022, resulting in a total of approximately 273 country-year observations. 

---

<br><br>

## 📊 5. Descriptive Patterns and Correlation Analysis

<br>

### 🔹 5.1 Standardized boxplot 

<p align="left">
  <img src="/img/posts/bbb.png" width="650">
</p>

To allow meaningful comparison across variables measured in different units, all indicators were standardized into z-scores. The boxplot therefore reflects relative dispersion rather than absolute magnitude. Among the three variables, GDP growth exhibits the widest interquartile range and the most pronounced tails. Several extreme observations extend beyond ±3 standard deviations, indicating substantial short-term volatility within the sample. Employment rates show a comparatively narrower dispersion. While some outliers are present, the central mass of observations remains more tightly clustered around the mean. The Gini coefficient also displays cross-country variation, but its distribution appears more compact relative to GDP growth, suggesting that inequality varies across OECD economies within a more structurally bounded range. Overall, the standardized distribution indicates that GDP growth captures greater short-term fluctuation, whereas employment and income inequality demonstrate comparatively more stable cross-country patterns.

<br>

### 🔹 5.2 Employment Rate and GDP Growth

<p align="left">
  <img src="/img/posts/ca.png" width="650">
</p>

The scatter plot shows a **weak positive relationship** between employment rate and GDP growth across OECD countries. As employment increases, GDP growth tends to rise slightly. However, the relationship is not strong, and there is considerable dispersion in growth outcomes even among countries with similar employment levels. This suggests that while labor market expansion may support economic growth, employment alone does not fully explain variations in GDP performance across countries.

---

<br>

### 🔹 5.3 Income Inequality (Gini) and GDP Growth

<p align="left">
  <img src="/img/posts/cb.png" width="650">
</p>

The relationship between income inequality and GDP growth appears **close to neutral or slightly negative**. The regression line is relatively flat, indicating that higher inequality does not systematically correspond to higher or lower growth during this period. This finding challenges the assumption that growth automatically reduces inequality or that inequality necessarily drives growth. Instead, growth dynamics seem to operate somewhat independently from income distribution patterns.

---

<br>

### 🔹 5.4 Employment Rate and Income Inequality

<p align="left">
  <img src="/img/posts/cc.png" width="650">
</p>


In contrast, the relationship between employment rate and income inequality reveals a **clear negative association**. Countries with higher employment rates generally tend to exhibit lower Gini coefficients. This suggests that labor market participation plays an important role in moderating income inequality within OECD economies.

This pattern represents the broader OECD structural tendency:  

> Higher employment → Lower inequality

This OECD-wide relationship serves as a baseline for evaluating whether the United States follows the same structural pattern or diverges from it.

---

