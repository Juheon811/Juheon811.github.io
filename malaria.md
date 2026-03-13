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

The data used in this study were collected from official Korean statistical and public data sources, including malaria incidence records, meteorological statistics, agricultural land data, livestock statistics, demographic data, mobility data, healthcare workforce statistics, and geographic coordinate data.

The analysis focuses on district-level observations within Seoul, Gyeonggi, Incheon, and Gangwon, where the majority of domestic malaria cases are concentrated.


### 🗺 5.1 Spatial Movement Analysis

**Structure:**

- Province  
- District  
- Annual malaria cases (2014–2023)  
- Latitude  
- Longitude  

This dataset contains yearly malaria incidence data and geographic coordinates for each district.

It was used to examine changes in spatial distribution over time.


### ⚠ 5.2 Risk Area Selection

**Structure:**

- Province  
- District  
- Malaria cases (2023)  
- Healthcare workforce (2022)  
- Floating population (2020)  

This dataset includes recent incidence data and selected structural indicators.

It was used to compare districts and identify risk areas.



### 📈 5.3 Determinant Analysis

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

---

## 📊 6. Analysis

### 🗺️ 6.1 Spatial Shift of Malaria Incidence Over Time

<p align="left">
  <img src="/img/posts/mal1.png" width="450">
</p>

To identify temporal changes in the spatial concentration of malaria incidence, the annual weighted mean center was calculated from 2001 to 2023 using district-level case counts and geographic coordinates. In 2001, the weighted mean center was clearly located in the northeastern inland area, around the Yangju region. This indicates that malaria cases were strongly concentrated in the northern border-adjacent districts at the beginning of the study period. From 2002 to around 2010, the centroid shifted southwest toward the Uijeongbu–northern Goyang corridor. The movement during this period shows a gradual transition away from the far northeastern inland area and toward the northwestern part of the Seoul metropolitan region. Around 2012, the centroid moved further west compared to previous years, reaching its most southwestern position in the observed period. This suggests a temporary increase in case concentration toward the western Gyeonggi area. After 2013, the mean center shifted back slightly eastward and became more tightly clustered around the Goyang–Eunpyeong boundary area. From 2014 onward, the annual centroids appear concentrated within a relatively small spatial range, indicating stabilization of the core incidence zone. By 2023, although total malaria cases increased nationally, the weighted mean center remained within this northwestern metropolitan corridor rather than returning to the original northeastern inland position observed in 2001. Overall, the enlarged map confirms a clear long-term spatial shift: malaria incidence moved from a northeastern border-focused concentration toward a more stable northwestern metropolitan-adjacent cluster.


### 📅 6.2 Selection Criteria for Reference Years (2017 and 2023)

<p align="left">
  <img src="/img/posts/mal2.png" width="450">
</p>

To examine structural differences in malaria incidence under contrasting conditions, two reference years were selected: 2017 and 2023. As shown in the annual trend graph, malaria cases remained relatively stable between 2014 and 2019, followed by a sharp decline during 2020–2021, likely associated with reduced mobility and public health interventions during the COVID-19 pandemic. In 2017, malaria incidence was comparatively low within the pre-pandemic period, representing a stable baseline condition before major external disruptions. In contrast, 2023 shows a dramatic surge in cases, marking the highest level in the observed period. This sharp increase reflects a post-pandemic rebound and suggests the influence of structural and environmental factors beyond temporary mobility restrictions. Therefore, 2017 and 2023 were selected as analytical reference points to compare malaria determinants under stable versus outbreak conditions.

### 🧩 6.3 Regional Structural Classification

To identify structural differences in malaria incidence across districts, dimensionality reduction and clustering analysis were conducted. First, **Principal Component Analysis (PCA)** was applied to reduce the dimensionality of the dataset and capture the major variance structure among environmental, demographic, and agricultural variables. The cumulative explained variance analysis showed that **five principal components explain approximately 92% of the total variance**, indicating that the main structure of the dataset can be represented with a reduced number of components. Based on these transformed features, clustering analysis was performed to identify districts with similar structural characteristics.

Two clustering algorithms, **K-Means and DBSCAN**, were tested. The **Elbow Method** was used to determine the optimal number of clusters for K-Means, and the results indicated that **three clusters (k = 3)** provided the most appropriate grouping of districts. Although DBSCAN was also applied, it produced only a single cluster under the selected parameter settings, making it unsuitable for distinguishing meaningful regional patterns.
The **Silhouette Score of the K-Means model was approximately 0.26**, suggesting a moderate but interpretable level of separation among clusters. Therefore, **K-Means clustering with three clusters was selected for the final regional classification**, and the characteristics of each cluster are analyzed in the following section.

### 📍 6.4 Cluster 1: Urban-Adjacent Regions

<p align="center">
  <img src="/img/posts/mall1.png" width="45%">
  <img src="/img/posts/malll1.png" width="45%">
</p>

<p align="center">
  <em>2017</em> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <em>2023</em>
</p>

Cluster 1 mainly consists of districts located near the Seoul metropolitan area. These regions represent urban-adjacent environments where malaria incidence is influenced more strongly by climatic conditions rather than agricultural land-use factors. Decision tree analysis shows that **precipitation is the most important variable determining malaria incidence in this cluster**. Other environmental variables such as average temperature and population density also contribute to the variation in case counts. Multiple linear regression analysis was conducted to examine the relationship between malaria incidence and explanatory variables within this cluster. The regression model indicates that climatic variables, particularly precipitation, play a more significant role compared to agricultural variables such as paddy field area. Overall, the results suggest that malaria occurrence in urban-adjacent regions is primarily associated with **climatic conditions and urban environmental factors**, rather than agricultural landscape structure.

### 📍 6.5 Cluster 2: Agricultural Regions

<p align="center">
  <img src="/img/posts/mall2.png" width="45%">
  <img src="/img/posts/malll2.png" width="45%">
</p>


Cluster 2 includes districts characterized by extensive agricultural land use, particularly areas with large paddy field coverage.Decision tree analysis indicates that **paddy field area is the most influential variable explaining malaria incidence in this cluster**. Paddy fields provide favorable breeding environments for mosquitoes, which increases the potential risk of malaria transmission.Multiple linear regression analysis further supports this finding. Among the explanatory variables, the **paddy field ratio shows the strongest relationship with malaria case counts**, indicating that agricultural landscape structure plays a key role in malaria occurrence within these regions. These results suggest that malaria risk in agricultural districts is strongly associated with **environmental conditions related to rice cultivation and mosquito habitat formation**.

### 📍 6.6 Cluster 3: Livestock and Socioeconomic Regions

<p align="center">
  <img src="/img/posts/mall3.png" width="45%">
  <img src="/img/posts/malll3.png" width="45%">
</p>

Cluster 3 consists of districts where livestock-related and socioeconomic variables appear to be associated with malaria incidence.Decision tree analysis indicates that **livestock count and income level are the most influential variables explaining malaria incidence in this cluster**. This suggests that regions with higher livestock populations and certain socioeconomic conditions may provide ecological environments that influence mosquito activity and malaria transmission.Multiple linear regression analysis shows that variables such as **population density and sex ratio also exhibit relationships with malaria case counts**. However, these variables alone are not sufficient to fully explain malaria incidence patterns.Therefore, the decision tree results suggest that **livestock distribution and income-related socioeconomic factors play a more significant role** in explaining malaria occurrence within this cluster.Overall, the results indicate that malaria incidence in these regions is associated with **livestock distribution and broader socioeconomic characteristics**.
