---
layout: inner
title: "Multi-Model Comparison of Topic Modeling: LDA, BERTopic, and LLM-Enhanced Clustering"
permalink: /topic/
---
<br><br>
# Kapoor et al (2024): Qualitative Insights Tool (QualIT): LLM Enhanced Topic Modeling
<br><br>
## 💡 1. Research Question and Research Gap

#### To what extent can LLM-based topic modeling outperform LDA and BERTopic in extracting coherent and diverse topics from large text datasets?

To answer this question, the research team proposes Qualitative Insights Tool (QualIT), a novel LLM-based thematic modeling framework, and conducts comparative experiments with LDA and BERTopic based on the 20 NewsGroups dataset.

---
<br><br>
## 🌊 2. Introduction

Topic modeling is a representative NLP technique for automatically extracting latent topics from documents. Traditional methods like LDA generate topics based on word co-occurrence patterns, but they have limitations in capturing subtle contextual or semantic nuances within sentences. Recently, approaches leveraging large language models (LLMs) such as BERT and GPT have enabled more sophisticated semantic understanding, and embedding-based techniques like BERTopic have gained attention. However, BERTopic also has limitations, as it typically assigns only a single topic to each document, making it insufficient for capturing multiple topics within a single document. To address this issue, this paper proposes LLM-enhanced Topic Modeling, which combines the semantic understanding capabilities of LLMs with clustering techniques.

---
<br><br>
## 🛠️ 3. Data and Methodology

### 📂 Dataset  
- **20 NewsGroups**: A public dataset containing 20,000 news articles  
- **Preprocessing**: Lowercasing, stopword removal, and lemmatization  

### 🧠 Models for Comparison  
- **LDA (Latent Dirichlet Allocation)**: Implemented using Gensim with default parameters  
- **BERTopic**: Utilizes embedding vectors and HDBSCAN-based clustering  
- **QualIT (LLM-based approach)**: Based on Claude-2.1 with parameters `top_k=50`, `top_p=0`  

## 
