# CineMatch — Interactive Movie Recommendation Dashboard & Defect Detection Lens

This project provides two related web experiences running from the same Flask backend:

1. **Movie Recommendations Dashboard** (content-based + collaborative)
2. **Defect Detection Dashboard** (computer vision heuristics with a CV “condition score”)

---

## Movie Recommendations Dashboard (default)

**CineMatch** is an interactive web dashboard for movie recommendations using:
- **Content-based filtering** (TF-IDF similarity on `genres`, `director`, `cast`, `title`)
- **Collaborative filtering** (item-item similarity derived from user ratings)

### Features
- Discover / Top Rated / Browse by Genre tabs
- Live search (title / genres / director / cast)
- Movie details modal
- Two recommendation lists inside the modal:
  - **You Might Also Like** (content-based)
  - **Collaborative Picks** (collaborative)

### API Endpoints
- `GET /api/stats`
- `GET /api/genres`
- `GET /api/movies/search?q=...`
- `GET /api/movies/top?genre=...`
- `GET /api/movies/<movie_id>`
- `GET /api/movies/<movie_id>/similar`
- `GET /api/recommend/collaborative?movie_id=...`

### Notes
- The backend validates that `movies.csv` and `ratings.csv` exist and include required columns.

---

## Defect Detection Dashboard (Computer Vision)

The **Defect Detection Dashboard** lets you upload an image and returns:
- `product_type` (baseline heuristic placeholder)
- `product_confidence` (baseline heuristic)
- `condition_score` in range **0–10**
- `verdict`: **Good / To Review / Bad**
- `debug` info (feature breakdown)

### UI
- Served at: `GET /`
- Frontend: `defect_dashboard_index.html`

### API Endpoint
- `POST /api/detect`
  - Form field: `image` (multipart/form-data)

---

## Project Structure
- `app.py` — Flask backend + recommendation APIs + `/api/detect`
- `defect_dashboard_index.html` — Defect detection UI
- `cv_pipeline.py` — CV feature extraction + condition scoring
- `movies.csv` — Movie metadata + IMDb rating (used by recommendation endpoints)
- `ratings.csv` — User ratings dataset (used by collaborative filtering)
- `requirements.txt` — Python dependencies

---

## Setup (Windows)

### 1) Create a virtual environment
```bat
python -m venv venv
venv\Scripts\activate
```

### 2) Install dependencies
```bat
pip install -r requirements.txt
```

---

## Run

From the project directory:
```bat
python app.py
```

Then open:
- http://127.0.0.1:5000/

---

## License
MIT (see `LICENSE`).

