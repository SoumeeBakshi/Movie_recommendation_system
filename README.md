# 🎬 Movie Recommendation System

A content-based movie recommendation web app that suggests similar movies based on genres, keywords, tagline, cast, and director — built with Python, scikit-learn, and Flask, and deployed on Render.

**🔗 Live Demo:** [https://render-movie-recommendation.onrender.com](https://render-movie-recommendation.onrender.com)

> Note: This app is hosted on Render's free tier. The first request after inactivity may take 30–50 seconds while the server spins back up.

---

## 📌 Overview

This project recommends movies similar to a user's favourite movie using **content-based filtering**. Instead of relying on user ratings or collaborative data, it analyzes the *content* of each movie — genres, keywords, tagline, cast, and director — to find movies with similar characteristics.

---

## ⚙️ How It Works

1. **Data Preprocessing** — Selected features (`genres`, `keywords`, `tagline`, `cast`, `director`) are cleaned and missing values are filled.
2. **Feature Combination** — All selected features are merged into a single text string per movie.
3. **Vectorization** — The combined text is converted into numerical feature vectors using **TF-IDF (Term Frequency–Inverse Document Frequency)**.
4. **Similarity Computation** — **Cosine similarity** is used to measure how similar movies are to one another based on their feature vectors.
5. **Matching** — When a user enters a movie name, `difflib` finds the closest matching title in the dataset (to handle typos/partial names).
6. **Recommendation** — The top similar movies are ranked and displayed to the user.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3.13 |
| ML / Data | pandas, NumPy, scikit-learn (TF-IDF, cosine similarity) |
| Web Framework | Flask |
| Frontend | HTML, CSS (Jinja templates) |
| Deployment | Render (Gunicorn as production server) |
| Version Control | Git & GitHub |

---

## 📁 Project Structure

```
render-movie/
├── app.py                        # Flask application
├── movie_recommender_light.pkl   # Pickled movies data + TF-IDF vectorizer + feature vectors
├── requirements.txt              # Python dependencies
├── templates/
│   └── index.html                # Frontend UI
└── .gitignore
```

---

## 🧠 Model Details

Rather than storing a full precomputed similarity matrix (which becomes very large for bigger datasets), this project stores the lightweight components needed to compute similarity **on demand**:

- `movies_data` — a slimmed-down dataframe with only the columns needed for lookup (`index`, `title`)
- `vectorizer` — the fitted `TfidfVectorizer`
- `feature_vectors` — sparse TF-IDF feature vectors (stored as `float32` to save memory)

At request time, cosine similarity is computed only between the queried movie and all others, rather than loading a full precomputed matrix — this keeps memory usage low, which matters on free-tier hosting with limited RAM.

---

## 🚀 Running Locally

1. **Clone the repository**
```bash
git clone https://github.com/SoumeeBakshi/render-movie.git
cd render-movie
```

2. **Create and activate a virtual environment**
```bash
python -m venv myenv
myenv\Scripts\activate      # Windows
source myenv/bin/activate   # macOS/Linux
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Run the app**
```bash
python app.py
```

5. Open your browser at `http://127.0.0.1:5000`

---

## ☁️ Deployment (Render)

This app is deployed on [Render](https://render.com) as a Web Service:

- **Runtime:** Python 3
- **Build Command:** `pip install -r requirements.txt`
- **Start Command:** `gunicorn app:app --workers=1 --threads=1 --timeout=120`

---

## 📊 Dataset

The dataset used contains ~4800 movies with metadata including genres, keywords, cast, crew, director, tagline, and more (a standard TMDB-style movie dataset).

---

## 🙋 Usage

1. Enter the name of a movie you like on the homepage.
2. Click **Recommend**.
3. The app finds the closest matching title in the dataset and returns the top 10 most similar movies based on content similarity.

---

