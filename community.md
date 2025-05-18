---
layout: inner
title: "Community Clusters and Socioeconomic Disparities in California"
permalink: /community/
---
<br><br>
# Andris et al. (2023): Human-network regions as effective geographic units for disease mitigation
<br><br>
## 💡 1. Research Question and Research Gap

#### To what extent do human mobility-based regions serve as more effective geographic units for mitigating the spread of COVID-19 than administrative boundaries?

Administrative units (state boundaries) often fail to capture the actual scope of human activity. This study defines functional regions by applying community detection algorithms to networks of human movement and social connections (such as commutes, GPS-based trips, and social media ties), and compares how effectively these alternative boundaries mitigate the spread of infectious diseases.

---
<br><br>
## 🌊 2. Introduction

The COVID-19 pandemic has highlighted the impact of interregional movement on the spread of infectious diseases, which has raised the issue that it is difficult to design effective quarantine policies only with existing administrative boundaries. In particular, if the same living area spans multiple administrative districts, different quarantine guidelines may conflict and lead to inefficiency. As an alternative to overcome these limitations, this study proposes functional areas based on human movement as a new policy unit.

---
<br><br>
## 🌐 3. Data and Methodology

### 📦 Human-Network Datasets

Five networks were constructed at the county level in the contiguous U.S.:

- **Commutes** 
- **Trips** 
- **Migration**
- **Twitter** 
- **Facebook** 

Nodes represent U.S. counties. <br>
Edges represent human connections (e.g., mobility flows or social media ties) between counties. <br>
Each network was partitioned into communities using the **Louvain method** for modularity maximization.

---

### 🦠 COVID-19 Case Data

- Weekly county-level case counts (May 2020 – May 2022) from *The New York Times*
- Metrics calculated between neighboring counties:
  - **C**: Total case count
  - **CR**: Mutual case rate per 1,000 people
  - **CD**: Difference in case rates

---
<br><br>
## 🔧 4. Network Analysis & Statistical Tests
<br>

### 1. Community Detection Algorithms
To group counties into meaningful regions, five community detection algorithms were tested: Fast Greedy, InfoMap, Louvain, REDCAP, and WalkTrap. Among them, the Louvain method performed best, showing the highest modularity (Q) in all networks Modularity measures how well a network is divided into separate communities. A high Q value means nodes are mostly connected within their own group, with fewer links to other groups. This shows clear boundaries, which helps when studying things like disease spread. A low Q value means the network is messy, with weak or unclear community structure

---
<br>

### 2. Node and Edge

- **CRw**: Within-region case rate (should be high)
- **CRb**: Between-region case rate (should be low)
- **CDw / CDb**: Within/between region case-rate differences

---
<br>

### 3. Statistical Analysis

To check how well each type of region (based on human networks like commuting, social media, etc.) explains the spread of COVID-19, the study used three main statistical methods:

---

**(1) Permutation Test**
This test checks if the differences in case count (C), case rate (CR), and case rate difference (CD) inside and between regions are meaningful, or just happened by chance. The method randomly changes the region boundaries 1,000 times to create a "baseline" of what random results would look like. Then it compares the real results to this random baseline. If the real results are very different, the region boundaries actually reflect real disease spread patterns.


**(2) Granger Causality Test**
This test looks at whether case rates in one county can predict case rates in a neighboring county over time. If past case data in one place helps guess future data in the next county, it may mean the disease spread across counties. If the connection is strong (with p < 0.001), it means that there's a possible causal link. This helps check if the regions follow real infection patterns over time.


**(3) Kolmogorov–Smirnov (KS) Test**
The KS test compares how different types of regions (like commute-based vs Twitter-based vs state boundaries) show changes in infection rates over time. It measures how far apart the distributions of infection rates are inside and between regions. A bigger difference means the region boundary does a better job of separating places with different infection patterns.

---

<br><br>
## 🎯 5. Result and Interpretation

Figure 2 visualizes the regional boundaries that divide the mainland United States in six different ways. In addition to the existing state boundaries, functional regions were generated using the Louvain algorithm based on networks derived from commuting, migration, travel, Twitter, and Facebook data. The commuting network resulted in the most granular division with 75 regions, while the Twitter and migration networks produced broader partitions with 26 and 28 regions.


![Figure2](/img/posts/p1.png)

---


According to Table 3, the commuting-based regions exhibited the highest number of within-region infections (Cw) and the largest differences in infection rates between regions (CDb), effectively capturing a structure in which disease transmission remained confined within boundaries. In contrast, although the migration-based regions had the highest CDb values due to clear separations between regions, the internal coherence was weaker, as reflected in the relatively small within-region infection rate differences (CDw). The Facebook-based regions showed minimal differences in infection rates both within and between regions and had lower Cw values, indicating limited effectiveness as functional boundaries.

![Table3](/img/posts/p3.png)

---

This pattern was also supported by the permutation test results in Table 4. For the commuting, migration, and trip-based regions, the actual Cw values were significantly higher than the expected values under random assignment (p < 0.001), while CDw values were consistently lower—suggesting that these regions formed tightly connected internal structures. In contrast, Facebook-based and random regions showed few statistically significant differences, confirming that they did not function as effective transmission boundaries.

Table 5 further evaluated temporal transmission dynamics using Granger causality and the Kolmogorov–Smirnov (KS) test. In the commuting regions, Granger causality was high within regions (CRw) but low between regions (CRb), indicating that infections tended to propagate internally rather than across boundaries. Twitter regions demonstrated a similar temporal trend but with weaker spatial separation. The KS test also showed the largest D-statistic values for commuting and Twitter-based regions, highlighting a clear difference in infection rate distributions inside versus across regional boundaries.

![Table4&5](/img/posts/p2.png)

Taken together, the analysis shows that commuting-based regions performed best as functional units for delineating the spread of infectious diseases. Trip- and state-based regions also showed moderate boundary effectiveness, while Facebook-based and random regions were ineffective in structurally separating transmission patterns.

---
<br><br>

# Community Detection California

## 📦 Data Introduction

#### Data Sources

**1. County shapefile**  
`COUNTY_2019_US_SL050_Coast_Clipped.shp`  <br>
Used for visualizing county-level community partitions on a choropleth map

**2. MSA shapefile (Metropolitan Statistical Areas)**  
`CBSA_MSA_2019_US_SL310_Coast_Clipped.shp`   
Used to compare community-detected regions with official administrative boundaries

**3. Socioeconomic data**  
`R13859119_SL050.csv` with data dictionary `R13859119.txt`  
Includes variables such as population, income, education, unemployment, and more  
Aggregated by community cluster to analyze group differences

**4. Migration flow data**  
`county-to-county-2016-2020-ins-outs-nets.xlsx`  
Includes in-migration, out-migration, net, and gross flow between counties  

---
<br><br>
#### Data Pre-processing

**1. Link** 

Read Excel file from the "California" sheet and keep only the first 9 columns.

```python
link = pd.read_excel('county-to-county-2016-2020-ins-outs-nets-gross.xlsx', sheet_name='California', skiprows=2)

link = link.iloc[:, 0:9]

link.columns = [
    'state_code_a',
    'county_code_a',
    'state_code_b',
    'county_code_b',
    'state_name_a',
    'county_name_a',
    'state_name_b',
    'county_name_b',
    'weight'
]
```

Filter out flows with weight less than or equal to 50 to reduce noise

```python
link = link[(link['state_name_a'] == 'California') & (link['state_name_b'] == 'California') & (link['weight'] > 50)]
```

---

**2. Node** 

Filter for California counties only (Geo_STATE == 6)

```python
node = node[node['Geo_STATE'] == 6]
```

Select only the columns required to compare community-level differences in population, race, education, income, and commuting patterns.

```python
node = node[[
    'Geo_FIPS',
    'Geo_QName', 
    'Geo_STATE',
    'Geo_COUNTY',
    'SE_A00001_001',  # Total population
    'SE_A03001_002',  # White Alone
    'SE_A03001_003',  # Black or African American Alone
    'SE_A03001_005',  # Asian Alone
    'SE_A00002_002',  # Population density
    'SE_A12001_005',  # Bachelor's degree
    'SE_A17005_003',  # Unemployed
    'SE_A14006_001',  # Median household income
    'SE_A09003_001'   # Average commute time
]]
```

---

## 🧭 California County-to-County Migration Network

The network displays the strongest migration links among California’s 58 counties, rather than the full set of connections. <br>

Los Angeles County appears as the largest node by far, indicating that it serves as the most active migration hub within California <br>
→ It plays a central role with high volumes of both in-migration and out-migration


Riverside, Orange, San Diego, and San Bernardino Counties, all located in Southern California, are densely connected around Los Angeles <br>
→ This reflects strong migration flows within the greater metropolitan area

![California](/img/posts/ca.png)

---
<br><br>

## 💡 Algorithms
