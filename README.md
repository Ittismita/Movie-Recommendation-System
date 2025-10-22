# 🎬 Movie Recommendation Systems

This repository implements three core types of **movie recommender systems**, each built using different recommendation strategies and data representations. The project demonstrates how traditional recommendation algorithms can be applied on movie metadata to suggest relevant and similar movies.

---

## Overview

The notebook `mov-rec.ipynb` builds three fundamental recommendation models:

### 1. Popularity-Based Recommender
A simple **non-personalized** approach that recommends movies based purely on their overall popularity — such as the highest vote count or average rating.  
Useful as a **baseline model** or for **cold-start** scenarios.

### 2. Content-Based Recommender
A **personalized system** that uses movie features such as:
- Overview (plot summary)
- Genres
- Keywords
- Cast and Crew  

These features are combined into a single text representation (`tags`), vectorized using text embedding techniques like **TF-IDF** or **Count Vectorizer**, and similarity is computed using **cosine similarity**.  
Movies similar in metadata space are recommended to the user.

### 3. Collaborative Filtering Recommender
A **user-item similarity** based approach that uses relationships among users or items derived from their historical preferences.  
Instead of relying on explicit rating predictions, this version computes **similarity (distance)** between user or item vectors and recommends the most similar items.

---

## Technologies Used

- **Python**
- **Pandas** – Data manipulation and analysis  
- **NumPy** – Numerical computations  
- **Scikit-learn** – Vectorization and similarity metrics  
- **Seaborn / Matplotlib** – Visualization  
- **AST** – Parsing stringified JSON objects in movie metadata  
- **NLTK** – Tokenization and text normalization  

---

## Workflow Summary

1. **Data Loading and Cleaning**
   - Load datasets.
   - Merge dataframes and handle missing values or irrelevant columns.
   - Convert stringified columns (`genres`, `keywords`, `cast`, `crew`) into structured lists using `ast.literal_eval`.

2. **Feature Engineering**
   - Combine key descriptive columns (overview, genres, keywords, cast, crew) into a new composite column called `tags`.
   - Apply text preprocessing — lowercasing, removing spaces, and tokenization.
   - Convert these tags into numerical vectors using **CountVectorizer** or **TF-IDF**.

3. **Model Building**
   - **Popularity-Based Model:** Sorts and recommends movies by popularity metric.
   - **Content-Based Model:** Computes **cosine similarity** between movie tag vectors.
   - **Collaborative Filtering Model:** Computes similarity between user/movie embeddings to recommend similar items.

4. **Recommendation Retrieval**
   - For a given input movie or user, compute similarity scores.
   - Retrieve the top-N most similar movies based on distance values.

---

## Key Learnings

- Recommender systems can function without explicit rating prediction by relying on **similarity-based ranking**.  
- The **content-based approach** enables personalized yet interpretable recommendations.  
- **Collaborative filtering** captures user or item-level relationships effectively when historical interactions exist.  
- Even simple **popularity models** serve as strong baselines and handle new-user cold-start scenarios.

---

## Future Improvements

- Integrate **hybrid recommenders** combining content-based and collaborative methods.  
- Experiment with **deep learning-based embeddings** using models like **Word2Vec** or **BERT** for movie metadata.  
- Deploy the system using **Streamlit** or **FastAPI** for interactive user testing.

---
