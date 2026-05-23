# How to Run RetailIQ AI Project in VS Code

# STEP 1 — Install Required Software

## 1. Install VS Code
https://code.visualstudio.com/

## 2. Install Python
https://www.python.org/downloads/

IMPORTANT:
During installation, check:
- Add Python to PATH

## 3. Install Node.js
https://nodejs.org/

## 4. Install PostgreSQL
https://www.postgresql.org/download/

Remember:
- username = postgres
- password = your password

# STEP 2 — Open Project in VS Code

File → Open Folder

Open:
retailiq-ai

# STEP 3 — Setup Frontend

Open terminal in VS Code:

Terminal → New Terminal

Run:

cd frontend
npm install

If Tailwind is missing:

npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p

# STEP 4 — Run Frontend

Inside frontend folder:

npm run dev

You will see:

Local: http://localhost:5173

# STEP 5 — Setup Backend

Open NEW terminal.

Go to backend:

cd backend

Create virtual environment:

Windows:
python -m venv venv
venv\Scripts\activate

Mac/Linux:
python3 -m venv venv
source venv/bin/activate

# STEP 6 — Install Backend Packages

pip install fastapi uvicorn pandas numpy scikit-learn matplotlib seaborn sqlalchemy psycopg2-binary python-multipart passlib bcrypt python-jose xgboost prophet nltk transformers

# STEP 7 — Start Backend Server

uvicorn app.main:app --reload

You should see:

Uvicorn running on http://127.0.0.1:8000

# STEP 8 — Test Backend

Open browser:

http://127.0.0.1:8000

You should see:

{
  "message": "RetailIQ AI Backend Running"
}

# STEP 9 — Open Swagger API Docs

http://127.0.0.1:8000/docs

# STEP 10 — Connect Frontend to Backend

Create:
src/services/api.js

Add:

import axios from 'axios'

const API = axios.create({
  baseURL: 'http://127.0.0.1:8000'
})

export default API

# STEP 11 — Fetch Backend Data

Example inside Dashboard.jsx:

import { useEffect } from 'react'
import API from '../services/api'

useEffect(() => {
  API.get('/analytics/sales-summary')
    .then(res => console.log(res.data))
}, [])

# STEP 12 — Setup PostgreSQL Database

CREATE DATABASE retailiq;

# STEP 13 — Update Database URL

Inside:
backend/app/database.py

Update:

DATABASE_URL = 'postgresql://postgres:YOUR_PASSWORD@localhost/retailiq'

# STEP 14 — Recommended VS Code Extensions

- Python
- Pylance
- ES7 React Snippets
- Tailwind CSS IntelliSense

# STEP 15 — Run Both Together

Terminal 1:
cd frontend
npm run dev

Terminal 2:
cd backend
uvicorn app.main:app --reload

# FINAL URLs

Frontend:
http://localhost:5173

Backend:
http://127.0.0.1:8000

API Docs:
http://127.0.0.1:8000/docs

# Common Errors & Fixes

## npm not recognized
Reinstall Node.js and restart VS Code.

## python not recognized
Reinstall Python and check:
Add Python to PATH

## Module not found
npm install

or

pip install -r requirements.txt

## Port already in use
npm run dev -- --port 3000

# Recommended Development Flow

1. Build frontend UI
2. Build backend APIs
3. Connect database
4. Add ML models
5. Add charts
6. Add authentication
7. Add dashboards
8. Deploy project

# Best Features To Build First

1. KPI Dashboard
2. Revenue Analytics
3. Sales Forecasting
4. Customer Segmentation
5. Sentiment Analysis
6. Recommendation Engine
7. AI Assistant
8. Real-time Analytics
