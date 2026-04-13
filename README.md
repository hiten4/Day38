# Week 07 - Tuesday NLP Assignment (Word2Vec & Semantic Similarity)

## Overview
This assignment focuses on understanding word embeddings using Word2Vec and comparing different text representation techniques for semantic similarity. It also explores how context affects meaning and how modern models overcome limitations of traditional approaches.

## Dataset
ShopSense E-Commerce Dataset:
- Reviews Dataset (~10,000 rows)
- Column used:
  - review_text

## Tasks Completed

### Q1 - Word2Vec Training

- Trained Word2Vec model on review text
- Used preprocessing (lowercase, cleaning, tokenization)
- Generated word embeddings for vocabulary

### Polysemy Problem (Word: "cheap")

- Checked similarity:
  - cosine("cheap", "affordable")
  - cosine("cheap", "flimsy")

- Observation:
  Word2Vec generates only one vector for "cheap", even though it has multiple meanings (affordable vs low-quality). This shows limitation of static embeddings.

### Disambiguation System

- Built a simple system using context vectors
- Created anchor vectors:
  - Affordable context → "cheap affordable price good deal"
  - Low-quality context → "cheap flimsy poor quality bad"

- Compared cosine similarity of sentence with both anchors
- Classified meaning of "cheap" based on higher similarity

### Window Size Comparison

- Trained two models:
  - window = 2 → captures syntactic relationships
  - window = 10 → captures semantic relationships

- Observation:
  Larger window size captures broader context and meaning, while smaller window focuses on nearby word relationships

---

## Q2 - Similarity Comparison

Two reviews:
- Review A: "incredible camera but terrible battery life"
- Review B: "Battery drains fast, although photos are stunning"

### Methods Used

1. Bag of Words (BOW)
2. TF-IDF
3. Word2Vec (average embeddings)
4. Sentence-BERT

### Observations

- BOW performs poorly due to low word overlap
- TF-IDF improves slightly but still limited
- Word2Vec captures some semantic similarity
- Sentence-BERT gives best similarity as it understands sentence meaning

---

## BOW Failure Explanation

BOW relies on exact word matching. In this case:
- "terrible battery life" vs "battery drains fast"
- "incredible camera" vs "photos are stunning"

Although meaning is similar, words differ → low similarity score

---

## Semantic Gap Explanation

- BOW → No understanding of meaning
- TF-IDF → Weighs importance but still word-based
- Word2Vec → Captures word-level semantics
- Sentence-BERT → Captures full sentence meaning and context

Each step reduces the semantic gap between text representations

---

## How to Run

1. Upload dataset to Colab:
   /content/shopsense_reviews.csv

2. Open notebook:
   week07_tuesday_structured.ipynb

3. Install dependencies (first cell):
   pip install gensim sentence-transformers

4. Run all cells

---

## Output

- Word2Vec similarity scores
- Disambiguation results for "cheap"
- Window size comparison insight
- Similarity scores across 4 methods (BOW, TF-IDF, Word2Vec, SBERT)

---

## Engineering Practices Followed

- Modular code (separate functions)
- Clear variable naming
- Minimal hardcoding
- Defensive handling (missing words, missing data)

---

## Conclusion

This assignment demonstrates how word embeddings work and highlights limitations of traditional NLP methods. It shows how contextual embeddings like Sentence-BERT significantly improve semantic understanding compared to earlier approaches.
