# 🧹 Text Preprocessing & Word2Vec Pipeline

This repository provides two **Colab notebooks** that demonstrate a complete **text preprocessing** and **Word2Vec model training** pipeline.  
It is designed for Natural Language Processing (NLP) experiments that require structured and well-cleaned textual data.

---

## 📘 Overview

The project is divided into **two main stages**:

1. **Text Preprocessing Pipeline** — Prepares raw text data for embedding training.  
2. **Word2Vec Embedding Training** — Trains a Word2Vec model and generates document-level embeddings.

---

## 📂 Notebooks

### 1️⃣ `text-preprocessing-pipeline.ipynb`

This notebook performs comprehensive **text preprocessing** on a dataset to create a clean and consistent text corpus.

#### 🔧 Steps in the Pipeline
- **Cleaning**:  
  - Removes unnecessary cells and rows containing NaN values in label columns.  
  - Reorders columns into:  
    `Label Columns | Text Columns | Numerical Columns`  
- **Text Corpus Creation**:  
  - Concatenates all text columns into a single text corpus.  
- **Text Cleaning Operations**:
  - Expands abbreviations (e.g., `don't → do not`).  
  - Removes contact details (emails, URLs, phone numbers, and social media mentions).  
  - Optionally removes stop words and punctuation.  
  - Restores genitive and plural “s” endings after punctuation removal.  
  - Replaces **positive/negative numbers** and **dates** with placeholders.  
- **Vocabulary Optimization**:
  - Identifies and removes **common phrases** (low informational value) and **rare words** (increase vocabulary noise).  
- **Output**:
  - Returns a cleaned DataFrame containing processed text columns.  
  - Produces a cleaned text corpus ready for training Word2Vec or similar models.

#### 📖 Reference
This pipeline follows concepts introduced in:  
> Bird, Steven, Edward Loper, and Ewan Klein (2009). *Natural Language Processing with Python.* O’Reilly Media Inc.  
> [DOI: 10.1145/2783258.278338](https://doi.org/10.1145/2783258.278338)

---

### 2️⃣ `text_to_vec.ipynb`

This notebook takes the **cleaned text corpus** from the previous step and trains a **Word2Vec model** using the **Gensim** library.

#### 🧠 Main Steps
- **Training**:
  - Trains a Word2Vec model on the cleaned text corpus.  
- **Embedding Creation**:
  - Computes a **document vector** for each DataFrame row by averaging word vectors across all text columns.  
  - Stores:
    - The overall document vector.  
    - Individual document vector for each text column.  
- **Evaluation**:
  - Reports:
    - Vocabulary length.  
    - Most common and rare words.  
    - Example word similarities (e.g., `most_similar('money')`).  
- **Visualization**:
  - Generates a **t-SNE plot** to visually map word vector similarities.
