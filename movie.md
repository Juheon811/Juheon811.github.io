---
layout: inner
title: "Movie Review Text Mining: Sentiment Analysis of Avengers: Endgame"
permalink: /movie/
---
# 🎬 Movie Review Text Mining: Sentiment Analysis of Avengers: Endgame

---
<br><br>
## 🎥 1. Introduction

*Avengers: Endgame* was one of the most globally successful films of the last decade.  
Both Korean and American audiences rated the movie extremely highly.

- 🇺🇸 **Rotten Tomatoes (U.S.)**: 8.4 / 10  
- 🇰🇷 **Naver Movie (Korea)**: 9.5 / 10  

At first glance, the conclusion seems simple -> Both countries loved the movie.

But here’s the real question 👇

> If both countries gave similarly high ratings, does a high rating always mean strong positive emotion in text?

This project investigates that question using Natural Language Processing (NLP)

---
<br><br>
## 🎯 2. Research Objective

The goal of this project is to analyze and compare movie reviews of *Avengers: Endgame* from the United States and Korea using text mining techniques.

More specifically, this study aims to:

1. 🔍 Compare frequently used words in U.S. and Korean reviews  
2. 📊 Analyze sentiment distributions in both countries  
3. 🤔 Examine why high ratings may still produce different sentiment patterns  
4. 🌏 Explore whether cultural communication styles influence sentiment detection  

Although both countries rated the movie highly, the distribution of textual sentiment may reveal deeper structural differences.

This is not just about whether people liked the movie. 
It is about **how emotion is linguistically encoded across cultures.**

---
<br><br>
## 📚 3. Theoretical Background

### 3.1 ⭐ Star Ratings vs Textual Sentiment

Prior research suggests that star ratings and textual sentiment do not always align.

Wan & Nakayama (2022) demonstrated that numerical ratings reflect overall satisfaction, while textual reviews often capture more nuanced emotional expression.

This means:

- Two countries may assign similar ratings  
- But differ in emotional intensity within the text  

So relying solely on rating scores may hide cross-cultural variation in how emotions are expressed.

---

### 3.2 🌏 Cultural Communication Styles

Cultural communication theory provides an additional lens.

According to cross-cultural communication research (e.g., Brand et al., 2022), cultures can be broadly categorized.

In high-context cultures:
- Communication tends to be indirect and subtle  
- Emotional evaluation is often implied rather than explicitly stated  

In low-context cultures:
- Communication is explicit and direct  
- Emotional reactions are often expressed with strong evaluative words  

This distinction is important because sentiment analysis models rely heavily on explicit emotional vocabulary.

If emotion is expressed indirectly, a model may struggle to detect it accurately.

---
<br><br>
## 📦 4. Data Collection 📦

To explore this question, I collected movie review data from two major platforms:

- 🇺🇸 **Rotten Tomatoes**  
- 🇰🇷 **Naver Movie**

### Dataset Overview

- 📄 Total reviews: **600**
- 🇺🇸 300 English reviews
- 🇰🇷 300 Korean reviews
- 📝 Text-only reviews (free-text format)
- Each dataset contains a single column: `review`

All reviews were manually collected from publicly available sources and stored in CSV format.

---
<br><br>

## USA

### 🔹Data Processing

1. Preprocess Text Data

```python
def clean_text(text):
    text = str(text)                        # make sure it is a string
    text = re.sub(r'\n', ' ', text)         # remove new lines
    text = re.sub(r'\r', '', text)          # remove return marks
    text = re.sub(r'\t', ' ', text)         # remove tabs
    text = re.sub(r'\.', '', text)          # remove dots
    text = re.sub(r"[^A-Za-z\s]", "", text) # remove special marks, keep letters
    text = re.sub(r'\d+', '', text)         # remove numbers
    text = re.sub(r'\s+', ' ', text)        # fix many spaces to one
    text = text.strip().lower()             # cut side spaces and lowercase
```

2. Remove Stopword and Domain-Specific Word

```python
stop_words = set(stopwords.words("english"))

keep_words = {"not", "no", "nor", "but", "however", "though", "although", "without"}
stop_words = stop_words - keep_words

domain_stopwords = {
    "movie", "film", "movies", "films",
    "cinema", "endgame", "marvel",
    "avengers", "mcu", "infinity"
}

def remove_stopwords(text):
    tokens = [
        w for w in text.split()
        if w not in stop_words
        and w not in domain_stopwords
        and len(w) > 2
    ]
    return tokens
```

3. Normalization & Lemmatization

```python
lemmatizer = WordNetLemmatizer()

def normalize_and_lemmatize(tokens):

    # normalize films → movie
    tokens = [re.sub(r"\bfilms?\b", "movie", w) for w in tokens]

    # apply lemmatization
    tokens = [lemmatizer.lemmatize(w) for w in tokens]

    return tokens
```

4. Final Pipeline

```python
def full_preprocess(text):
    text = clean_text(text)
    tokens = remove_stopwords(text)
    tokens = normalize_and_lemmatize(tokens)
    return " ".join(tokens)

df["clean_review"] = df["review"].apply(full_preprocess)
```

---

### 🔹Word Frequency Analysis (U.S. Reviews)

The bar chart below presents the top 30 most frequent words in U.S. reviews.

<p align="left">
  <img src="/img/posts/ubar.png" width="650">
</p>

Strong evaluative terms such as *best*, *perfect*, *great*, and *amazing* dominate the ranking.

This indicates that American reviewers frequently rely on direct and high-intensity emotional vocabulary.

---

### 🔹Word Cloud Visualization

To complement the frequency distribution, a word cloud was generated to visualize important words.

<p align="left">
  <img src="/img/posts/ucloud.png" width="650">
</p>

The visual dominance of words like *best*, *time*, *great*, and *perfect* reinforces the observation that positivity is expressed explicitly and emphatically.

While the bar chart provides precise rankings, the word cloud highlights the emotional intensity embedded in word choice.


