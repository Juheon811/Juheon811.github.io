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


![Table3&5](/img/posts/topic2.png)


### 🔹 Table 3: Topic Coherence & Diversity by Number of Topics

This table compares the performance of three topic modeling methods — **LDA**, **BERTopic**, and **QualIT** — in terms of **Topic Coherence** and **Topic Diversity**, evaluated across different numbers of topics (10 to 50).

#### ✅ LDA
- Best coherence: **57.0%** at 20 topics  
- Best diversity: **79.1%** at 40 topics  
- Average performance: **51.4%** coherence, **72.7%** diversity  
- As a traditional approach, LDA shows the lowest scores overall in both coherence and diversity.

#### ✅ BERTopic
- Best coherence: **65.0%** at 20 topics  
- Best diversity: **88.8%** at 40 topics  
- Average performance: **61.0%** coherence, **86.3%** diversity  
- With embedding-based clustering, BERTopic outperforms LDA and offers moderate diversity and coherence.

#### ✅ QualIT
- Best coherence: **70.0%** at 20 topics  
- Best diversity: **95.5%** at 20 topics  
- Average performance: **64.4%** coherence, **93.7%** diversity  
- QualIT consistently performs the best across all topic counts. It is especially optimized for 20 topics, which matches the dataset’s ground-truth structure.

---

### 👥 Table 4: Human Evaluation Agreement

This table shows how often **human evaluators (4 total)** agreed on categorizing topic outputs from each model into one of the 20 ground-truth classes.

#### ✅ QualIT
- 80% agreement with at least 2 evaluators  
- 50% agreement with at least 3 evaluators  
- 35% full agreement (all 4 evaluators)  
- QualIT provides topic outputs that are much clearer and easier for humans to interpret and classify consistently.

#### ✅ BERTopic & LDA
- LDA: 50% (2 evaluators), 25% (3 evaluators), 20% (all 4)  
- BERTopic: 45%, 25%, 20% respectively  
- Both LDA and BERTopic yield lower agreement scores, indicating more ambiguous or inconsistent topic groupings.

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
 
---
<br><br>
# A Comparative Study in Topic Modeling

## 📦 1. Dataset and Preprocessing

### 🔹 Source
Video_Games.jsonl from Amazon Reviews dataset <br>

### 🔹 Preprocessing
Filtered only 1-star reviews with `helpful_votes >= 1` <br>
Text length between 20 and 200 characters <br>
Removed stopwords, applied lemmatization <br>
Final dataset prepared for topic modeling

1. Preprocess Text Data

```python
def preprocess_text(text):
    text = re.sub('\s+', ' ', text)  # Remove extra spaces
    text = re.sub('\S*@\S*\s?', '', text)  # Remove emails
    text = re.sub('\'', '', text)  # Remove apostrophes
    text = re.sub('[^a-zA-Z]', ' ', text)  # Remove non-alphabet characters
    text = text.lower()  # Convert to lowercase
    return text
```

2. Tokenize and Remove Stopwords

```python
# Download NLTK stopwords
nltk.download('stopwords')
stop_words = stopwords.words('english')

# Tokenize and remove stopwords
def tokenize(text):
    tokens = gensim.utils.simple_preprocess(text, deacc=True)
    tokens = [token for token in tokens if token not in stop_words]
    return tokens
```

3.  Lemmatize Tokens
```python
try:
    nltk.data.find('corpora/wordnet')
except LookupError:
    nltk.download('wordnet')


lemmatizer = WordNetLemmatizer()

def extract_lemmas(tokens):
    return [lemmatizer.lemmatize(token) for token in tokens]
```
4.   Create Dictionary and Corpus
```python
# Create dictionary and corpus
id2word = corpora.Dictionary(df['lemmas'])
texts = df['lemmas']
corpus = [id2word.doc2bow(text) for text in texts]
```
