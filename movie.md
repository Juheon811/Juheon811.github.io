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

This ensures consistency across datasets and allows a structured comparison between the two countries.

---
<br><br>
