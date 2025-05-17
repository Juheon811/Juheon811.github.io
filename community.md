---
layout: inner
title: "Community Clusters and Socioeconomic Disparities in California"
permalink: /community/
---
<br><br>
# Andris et al. (2023): Human-network regions as effective geographic units for disease mitigation
<br><br>
## 💡 1. Research Question and Research Gap

### To what extent do human mobility-based regions serve as more effective geographic units for mitigating the spread of COVID-19 than administrative boundaries?

Administrative units (state boundaries) often fail to capture the actual scope of human activity. This study defines functional regions by applying community detection algorithms to networks of human movement and social connections (such as commutes, GPS-based trips, and social media ties), and compares how effectively these alternative boundaries mitigate the spread of infectious diseases.

---
<br><br>
## 🌊 2. Introduction

The COVID-19 pandemic has highlighted the impact of interregional movement on the spread of infectious diseases, which has raised the issue that it is difficult to design effective quarantine policies only with existing administrative boundaries. In particular, if the same living area spans multiple administrative districts, different quarantine guidelines may conflict and lead to inefficiency. As an alternative to overcome these limitations, this study proposes functional areas based on human movement as a new policy unit.

---
<br><br>
## 🔧 3. Methods and Data Sources

### 📦 Human-Network Datasets

Five networks were constructed at the county level in the contiguous U.S.:

- **Commutes** (LODES data, 2015)
- **Trips** (SafeGraph GPS data, Jan–Feb 2020)
- **Migration** (ACS migration estimates, 2013–2017)
- **Twitter** (Co-mention network, 2014–2015)
- **Facebook** (Social Connectedness Index)

Each network was partitioned into communities using the **Louvain method** for modularity maximization.

---

### 🦠 COVID-19 Case Data

- Weekly county-level case counts (May 2020 – May 2022) from *The New York Times*
- Metrics calculated between neighboring counties:
  - **C**: Total case count
  - **CR**: Mutual case rate per 1,000 people
  - **CD**: Difference in case rates

---

## 🔧 3. Network Analysis & Statistical Tests

### 🔍 Modularity (Q)

\[
Q = \sum (e_{\mu\mu} - b_{\mu}^2)
\]

Higher Q implies more well-separated communities, ideal for defining policy regions.

---

### 🔎 Case Spread Metrics

- **CRw**: Within-region case rate (should be high)
- **CRb**: Between-region case rate (should be low)
- **CDw / CDb**: Within/between region case-rate differences

### 🔬 Statistical Analysis

To check how well each type of region (based on human networks like commuting, social media, etc.) explains the spread of COVID-19, the study used three main statistical methods:

🧪 **Permutation Test**
This test checks if the differences in case count (C), case rate (CR), and case rate difference (CD) inside and between regions are meaningful, or just happened by chance. The method randomly changes the region boundaries 1,000 times to create a "baseline" of what random results would look like. Then it compares the real results to this random baseline. If the real results are very different, the region boundaries actually reflect real disease spread patterns.

🔁 **Granger Causality Test**
This test looks at whether case rates in one county can predict case rates in a neighboring county over time. If past case data in one place helps guess future data in the next county, it may mean the disease spread across counties. If the connection is strong (with p < 0.001), it means that there's a possible causal link. This helps check if the regions follow real infection patterns over time.

🧪 **Kolmogorov–Smirnov (KS) Test**
The KS test compares how different types of regions (like commute-based vs Twitter-based vs state boundaries) show changes in infection rates over time. It measures how far apart the distributions of infection rates are inside and between regions. A bigger difference means the region boundary does a better job of separating places with different infection patterns.


#### Data Pre-processing

**1. Link** 
