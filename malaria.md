---
layout: inner
title: "Malaria Risk Area Identification and Contributing Factor Analysis in South Korea"
permalink: /malaria/
---

<br><br>
# Malaria Risk Area Identification and Contributing Factor Analysis in South Korea
<br><br>

## 🌍 1. Background

In 2023, malaria cases in South Korea increased sharply, and infections were reported even in Seoul. At the same time, the World Health Organization (WHO) warned that climate change is making malaria elimination more difficult.


### 📈 1.1 Increase in Malaria Cases

The total number of confirmed malaria cases reached **747 in 2023**, representing a **77.9% increase** compared to 420 cases in 2022.

Although malaria cases had generally declined over the past decade, the trend reversed after 2021 and began to rise rapidly. The sharp increase between 2022 and 2023 indicates a meaningful change, emphasizing the need for strengthened malaria prevention and management.


### 🗺 1.2 Expansion of Affected Areas

Malaria cases have begun to appear in Seoul.

As of August 2024, a total of **15 malaria cases** were reported in Seoul, and **three of them** were estimated to have been locally transmitted. For the first time this year, Seoul was included in the official malaria alert areas, and five districts were newly designated as high-risk areas, leading to the implementation of response measures.


### 🌡 1.3 Increase in Mosquito Activity Due to Climate Change

With climate change, mosquito activity has increased, and malaria has become a serious global issue. According to the World Health Organization (WHO), there were **249 million malaria cases worldwide in 2022**, representing a **6.9% increase** compared to 2019 before the COVID-19 pandemic.

The WHO has warned that climate change is making malaria elimination increasingly difficult.

---


## 💡 2. Research Question

Which districts in South Korea are structurally high-risk for malaria, and what climatic and regional factors explain their spatial distribution?

This study aims to move beyond simple case counts and identify whether malaria risk follows identifiable structural patterns across districts.

---

## 🎯 3. Research Motivation & Objective

Malaria control in South Korea faces several emerging challenges.

First, studies have reported increasing resistance to insecticides among mosquito populations, suggesting that traditional control strategies may become less effective over time.

Second, more than 90% of domestic malaria cases are concentrated in specific regions, particularly near northern border areas. This strong geographic concentration indicates that malaria risk is not randomly distributed.

Third, the government recently announced the *Second National Malaria Elimination Plan (2024–2028)*, aiming to strengthen nationwide surveillance and prevention strategies. However, more precise district-level risk identification is required to allocate resources efficiently.

Based on these considerations, this study seeks to:

- Identify key contributing factors of malaria incidence at the district level  
- Structurally classify high-risk regions  
- Provide evidence for targeted prevention and resource allocation  

---

## 🔎 4. Analytical Framework

The overall analytical process consists of two major stages:

### 4.1 Data Collection and Preprocessing

- Collection of district-level data including population, land use, agricultural area, temperature, precipitation, humidity, malaria incidence, income, mobility, and healthcare resources  
- Integration of datasets into a unified panel structure  
- Removal of outliers and missing values  
- Application of scaling techniques  
- Construction of derived variables (e.g., ratios and density measures)

### 4.2 Data Analysis

The analysis proceeds in three steps:

1. **Spatial Shift Analysis**  
   - Calculation of annual mean geographic centers (2001–2023)  
   - Visualization of movement patterns over time  

2. **Regional and Temporal Factor Analysis (2017 vs 2023)**  
   - Principal Component Analysis (PCA) for dimensionality reduction  
   - Clustering using K-Means and DBSCAN  
   - Decision tree and multiple regression analysis by cluster  

3. **Risk Index Construction**  
   - Standardization of relevant indicators  
   - Calculation of a malaria risk index  
   - Identification of top and bottom five districts  

This framework allows for both structural interpretation and policy-relevant insight.

---

## 📦 5. Dataset Overview

Based on the analytical framework presented in this study, three final datasets were constructed.

Each dataset corresponds directly to one of the three analytical components:

1. Spatial movement analysis  
2. Risk area selection  
3. Determinant analysis  

These datasets were prepared separately according to their specific analytical purposes.

---

### 🗺 5.1 Spatial Movement Analysis

**Structure:**

- Province  
- District  
- Annual malaria cases (2014–2023)  
- Latitude  
- Longitude  

This dataset contains yearly malaria incidence data and geographic coordinates for each district.

It was used to examine changes in spatial distribution over time.

---

### ⚠ 5.2 Risk Area Selection

**Structure:**

- Province  
- District  
- Malaria cases (2023)  
- Healthcare workforce (2022)  
- Floating population (2020)  

This dataset includes recent incidence data and selected structural indicators.

It was used to compare districts and identify risk areas.

---

### 📈 3.3 Determinant Analysis

**Structure:**

- Province  
- District  
- Livestock count  
- Sex ratio  
- Population density  
- Average temperature  
- Precipitation  
- Paddy field area  
- Regional area  
- Malaria cases  
- Paddy field ratio  
- Latitude  
- Longitude  

This dataset integrates environmental, demographic, and agricultural variables with malaria incidence data.


