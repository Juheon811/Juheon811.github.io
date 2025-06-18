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

---
<br><br>
## 🧠 2. Topic Modeling with LDA, BERTopic, and QualIT

## LDA
```python
lda_model = gensim.models.ldamodel.LdaModel(corpus=corpus,
                                            id2word=id2word,
                                            num_topics=20, 
                                            random_state=100,
                                            update_every=1,
                                            chunksize=100,
                                            passes=10,
                                            alpha='auto',
                                            per_word_topics=True)
```

**Compute coherence score**

```python
coherence_model_lda = CoherenceModel(model=lda_model, texts=df['lemmas'], dictionary=id2word, coherence='c_v')

coherence_lda = coherence_model_lda.get_coherence()
print('\nCoherence Score: ', coherence_lda)
```

Coherence Score:  0.30031160118766986

**Compute diversity score**

```python
top_n_words = 20
topic_words = []

for i in range(lda_model.num_topics):
    words_with_probs = lda_model.show_topic(i, topn=top_n_words)
    words = [word for word, prob in words_with_probs]
    topic_words.append(words)

# top n words from every topic to a list
all_words_in_topics = [word for topic in topic_words for word in topic]
total_words_count = len(all_words_in_topics)
unique_words_count = len(set(all_words_in_topics))

# diversity score
diversity_score = unique_words_count / total_words_count

print(f"Total words across all topics: {total_words_count}")
print(f"Unique words across all topics: {unique_words_count}")
print(f"Diversity Score (N={top_n_words}): {diversity_score:.4f}")
```

Total words across all topics: 400  <br>
Unique words across all topics: 385 <br>
Diversity Score (N=20): 0.9625

---
<br><br>


## BERTopic

```python
nlp = spacy.load("en_core_web_sm")

def spacy_tokenizer(text):
    return [token.lemma_ for token in nlp(text) if not token.is_stop and not token.is_punct and not token.is_space]


english_stopwords = stopwords.words('english')
vectorizer_model = CountVectorizer(tokenizer = spacy_tokenizer,
                                   stop_words=english_stopwords, 
                                   min_df=5, 
                                   max_df=0.9, 
                                   ngram_range=(1, 1))
```

```python
model = BERTopic(verbose=True, 
                 embedding_model='all-MiniLM-L6-v2',  # all-MiniLM-L12-v2, paraphrase-MiniLM-L12-v2
                 vectorizer_model=vectorizer_model, 
                 language='english', 
                 nr_topics = 20,
                 top_n_words = 20,
                 calculate_probabilities=True
                )
topics, probs = model.fit_transform(df.text)
```

![topic](/img/posts/topic3.png)
