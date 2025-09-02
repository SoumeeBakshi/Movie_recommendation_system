# 🎬 Movie Recommendation System  

This project is a **content-based movie recommendation system** built in Python, designed to suggest movies similar to a user’s favorite choice. By leveraging **natural language processing (NLP)** techniques and machine learning tools from **scikit-learn**, the system analyzes key attributes of movies to generate personalized recommendations.  

---

## ✨ Features  
- **Content-Based Filtering** → Recommends movies by analyzing features like **genres, keywords, tagline, cast, and director**.  
- **TF-IDF Vectorization** → Converts textual metadata into numerical vectors for efficient comparison.  
- **Cosine Similarity** → Measures similarity between movies to identify the closest matches.  
- **User-Friendly Input** → Accepts a movie title from the user and outputs a ranked list of recommended movies.  

---

## 🛠️ Tech Stack / Requirements  
To run the notebook, install the following dependencies:  

- **Python Libraries**:  
  - `numpy`  
  - `pandas`  
  - `difflib`  
  - `scikit-learn` (TfidfVectorizer, cosine_similarity)  

- **Dataset**:  
  - A CSV file named **`movies.csv`**, containing movie metadata (genres, cast, director, keywords, tagline, etc.).  
  - Place this file in the same directory as the notebook or update the file path in the code accordingly.  

---

## 🚀 How It Works  
1. Load and preprocess movie data from `movies.csv`.  
2. Extract relevant features and combine them into a single string.  
3. Transform text features into numerical vectors using **TF-IDF**.  
4. Compute pairwise **cosine similarity scores** across all movies.  
5. When a user inputs a favorite movie title, retrieve and display the top similar movies.  

---

## 📌 Example Usage  
```python
Enter your favorite movie: Avatar  
Top 5 recommended movies:  
1. John Carter  
2. Guardians of the Galaxy  
3. Star Trek  
4. The Avengers  
5. Jupiter Ascending  
