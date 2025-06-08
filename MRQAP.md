---
layout: inner
title: "A Network-Based MRQAP Analysis of County-to-County Migration in California"
permalink: /MRQAP/
---
<br><br>
In the previous post on community analysis in California counties, migration patterns were examined and a network was constructed. This post extends the analysis by applying the MR-QAP method.

---

## ❓ MR-QAP

Multiple Regression Quadratic Assignment Procedure (MR-QAP) is a specialized regression analysis method designed to analyze network data. Traditional regression analysis operates on the assumption that each data point is independent of each other, but network data is not. For example, the number of people moving from county A to county B can be affected by the movement from county A to county A or their relationship with other counties, so all observations have an interdependent structure. Because of these characteristics, applying general regression analysis as it is can significantly reduce statistical reliability.


To address these issues, MR-QAP performs a regression analysis between the dependent and independent variable matrices, and then evaluates the significance of the regression results using a permutation-based test. A permutation test is a method of randomly mixing rows and columns of a dependent variable matrix, repeating the same regression analysis thousands of times to create a random distribution, and then comparing how extreme the actual regression results are in that distribution. This allows you to calculate the p-value and test whether the influence of that variable is statistically significant. 


This method is particularly effective when dealing with data on relationships in matrix form, such as population movement between regions, social networks, and interactions between organizations. In this analysis, MR-QAP was used to evaluate what socioeconomic factors might explain population movement between 58 counties in California.

## 📦 Data Introduction

#### Data Sources

**1. County shapefile**  
`COUNTY_2019_US_SL050_Coast_Clipped.shp`  
Used to get county boundaries and calculate distances between centroids.

**2. Socioeconomic data**  
`R13859119_SL050.csv` with `R13859119.txt`  
Includes population, income, education, unemployment, race, and commute time.  
Used to compare differences between counties.

**3. Migration flow data**  
`county-to-county-2016-2020-ins-outs-nets-gross.xlsx`  
Filtered for California-only flows (weight > 50).  
Used to build the migration network for MR-QAP.

---
<br><br>
#### Data Pre-processing

**1. Link** 

Read the "California" sheet from the Excel file and select the first 9 columns

```python
link = pd.read_excel('county-to-county-2016-2020-ins-outs-nets-gross.xlsx', sheet_name='California', skiprows=2)
link = link.iloc[:, 0:9]
link.columns = [
    'O_state_cd', 'O_county_cd', 'D_state_cd', 'D_county_cd',
    'O_state_nm', 'O_county_nm', 'D_state_nm', 'D_county_nm', 'weight'
]
```

Filter only within-California migration flows greater than 50

```python
link2 = link[
    (link['O_state_nm'] == 'California') &
    (link['D_state_nm'] == 'California') &
    (link['weight'] > 50)
]
```

Convert code columns to integer type

```python
link2['O_state_cd'] = link2['O_state_cd'].astype(int)
link2['O_county_cd'] = link2['O_county_cd'].astype(int)
link2['D_state_cd'] = link2['D_state_cd'].astype(int)
link2['D_county_cd'] = link2['D_county_cd'].astype(int)
```


**2. Node** 

Load socioeconomic data and filter for California counties

```python
node = pd.read_csv('R13859119_SL050.csv')
node = node[node['Geo_STATE'] == 6]
```

Select relevant variables

```python
node2 = node[[
    'Geo_FIPS',
    'Geo_QName',
    'Geo_STATE',
    'Geo_COUNTY',
    'SE_A00001_001',  # Total population
    'SE_A03001_002',  # White Alone
    'SE_A03001_003',  # Black Alone
    'SE_A03001_005',  # Asian Alone
    'SE_A00002_002',  # Population density
    'SE_A12001_005',  # Bachelor's degree
    'SE_A17005_003',  # Unemployed
    'SE_A14006_001',  # Median household income
    'SE_A09003_001'   # Average commute time
]]
```

---
