# ArthaYantra Investment Engine

ArthaYantra is a full-stack, beginner-friendly investment platform and stock market simulator. It aims to provide users with a secure and educational environment to learn about investing, test strategies, and track financial goals without real-world financial risk.

## Features

- **Educational Dashboard**: Personalized portfolio recommendations based on a risk assessment questionnaire.
- **Stock Simulator**: Real-time mock stock trading to practice investing strategies safely.
- **Goal Tracking**: Plan for the future with projected growth charts and monthly investment tracking.
- **Market Insights**: Simulated live market data to understand trends and economic news.
- **User Authentication**: Secure JWT-based login and signup powered by FastAPI and SQLite.

## Tech Stack

### Frontend
- React 19 + Vite
- Tailwind CSS (v4)
- React Router DOM for routing
- Recharts & Chart.js for data visualization
- Lucide React for icons

### Backend
- Python 3.10+
- FastAPI
- SQLite with SQLAlchemy ORM
- Pydantic for validation
- Passlib + JWT for authentication

## Project Structure

- `/frontend` - The React Vite application.
- `/backend` - The FastAPI server and SQLite database.

## Setup & Running Locally

### 1. Start the Backend

Navigate to the `backend` directory and install dependencies:

```bash
cd backend
python -m pip install -r requirements.txt
```

Run the FastAPI server:

```bash
python -m uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

The backend API will run on `http://localhost:8000`.

### 2. Start the Frontend

Navigate to the `frontend` directory and install dependencies:

```bash
cd frontend
npm install
```

Start the Vite development server:

```bash
npm run dev
```

The frontend application will be available at `http://localhost:5173`.
# ArthaYantra.
# ArthaYantra.
