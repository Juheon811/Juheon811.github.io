---
layout: inner
title: "Multi-Model Comparison of Topic Modeling: LDA, BERTopic, and LLM-Enhanced Clustering"
permalink: /topic/
---

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

---
<br><br>
## 🔍 4. LLM-Enhanced Topic Modeling Method

### 🔹 Step 1: Extract Keyphrases  
Each document is processed by an LLM to extract multiple meaningful keyphrases. Unlike traditional models (e.g., LDA, BERTopic) that assume a single topic per document, this step captures multiple thematic cues within one text. The extracted phrases serve as essential features for topic classification.

### 🔹 Step 2: Hallucination Verification  
A coherence score based on cosine similarity is calculated to assess how well each keyphrase aligns with the document content. Keyphrases with low scores are identified as "AI hallucinations" and removed, leaving only contextually valid and reliable terms for further analysis.

### 🔹 Step 3: Clustering (Main & Sub-Topics)  
Refined keyphrases are grouped using a K-Means clustering algorithm.  

Clustering is conducted in two stages:

- **Main Topics**: Documents with similar keyphrase patterns are grouped to identify overarching themes.  
- **Sub-Topics**: Within each main topic, a second clustering step is applied to extract more detailed and specific themes.  

For each sub-cluster, the LLM is prompted again to analyze compressed content and generate representative sub-topics.

---
<br><br>
## ✅ 5. Experimental Setup & Results

### 🔹 Dataset and Model Configuration  
- The experiments were conducted using the **20 NewsGroups** dataset, which contains approximately 20,000 news articles categorized into 20 topics.  
- **LDA** and **BERTopic** were run with default parameters, while the **LLM-based method (QualIT)** used the **Claude-2.1** model.  
  - Key parameters: `top_k = 50`, `top_p = 0` (optimized for document-level semantic coherence)

### 🔹 Evaluation Metrics  
- **Topic Coherence**: Measures how semantically similar the top-ranked words in each topic are.  
- **Topic Diversity**: The percentage of unique words across all topic outputs (from 0 to 1).

### 🔹 Summary of Results  

| Model     | Avg. Coherence | Avg. Diversity |
|-----------|----------------|----------------|
| LDA       | 51.4%          | 72.7%          |
| BERTopic  | 61.0%          | 86.3%          |
| **QualIT**| **64.4%**      | **93.7%**      |

- QualIT achieved the **highest average coherence and diversity** across all models.  
- The **best performance occurred at 20 topics**, which matches the ground-truth structure of the dataset.  
- Human evaluators manually categorized topic word lists into 20 predefined classes, showing that QualIT produced **the clearest and most interpretable topics**.

| Evaluation Criteria        | LDA  | BERTopic | **QualIT** |
|---------------------------|------|----------|------------|
| At least 2 evaluators agreed | 50%  | 45%      | **80%**    |
| At least 3 evaluators agreed | 25%  | 25%      | **50%**    |
| All 4 evaluators agreed      | 20%  | 20%      | **35%**    |

---
<br><br>
## ⚠️ 6. Limitations & Future Work

- **Processing Time**  
  - QualIT takes approximately **2–3 hours** per run  
  - BERTopic completes in about **30 minutes**  
  → Reducing runtime is essential for large-scale deployments.

- **Clustering Algorithm Improvements**  
  - Currently uses **K-Means**, which requires predefined cluster numbers  
  - **HDBSCAN**, used in BERTopic, may provide more adaptive and nuanced topic boundaries  
  - Future work may explore replacing K-Means with HDBSCAN to improve granularity and accuracy

---
<br><br>
## 🧾 7. Conclusion

- **QualIT** integrates the semantic understanding of LLMs with the structural power of clustering algorithms, delivering **more coherent and diverse topics** than traditional methods like LDA and BERTopic.  
- Especially useful in **qualitative text analysis** scenarios where interpretability and depth matter.  
- Future directions may include:
  - **Multilingual support**
  - **Efficiency improvements**
  - **Advanced clustering**

QualIT is not just an automation tool, but a powerful assistant for researchers and practitioners seeking to uncover meaningful insights from large-scale unstructured text data.

