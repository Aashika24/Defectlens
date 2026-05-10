# Defect Detection Dashboard — Computer Vision and Machine learning “Condition Score” (0–10)

This dashboard lets you upload a product image and returns a CV-based condition estimate:
- **product_type** (baseline heuristic placeholder)
- **product_confidence**
- **condition_score** (0–10)
- **verdict**: **Good / To Review / Bad**
- **debug** info: feature breakdown

## UI
- Served at: **GET /**  
- Frontend file: `defect_dashboard_index.html`

## API Endpoint
- **POST `/api/detect`**
  - Content-Type: `multipart/form-data`
  - Form field: `image` (the uploaded file)

## Output Contract (JSON)
The backend returns JSON like:
- `product_type`
- `product_confidence`
- `condition_score`
- `verdict`
- `debug` (includes extracted features + breakdown)

## Setup / Run
From the project directory:
```bat
python app.py


