# ArthaYantra System Architecture & Workflow

ArthaYantra is a comprehensive investment engine designed for beginners. It combines educational tools, risk assessment, and a real-time stock simulator to help users transition from saving to investing.

## 🏗️ System Architecture

The application follows a standard **Client-Server** architecture with specialized modules for financial logic and simulation.

### 1. Frontend (The "UI/UX" Layer)
- **Framework**: React 19 + Vite.
- **Styling**: Tailwind CSS (v4) for a premium, responsive glassmorphism aesthetic.
- **State Management**: React Context (`AuthContext`) for user sessions and authentication state.
- **Visualizations**: 
  - `Recharts`: For interactive goal projections and risk allocation pies.
  - `Chart.js`: For high-performance stock simulation line charts.
- **Routing**: `react-router-dom` with private route protection.

### 2. Backend (The "Engine" Layer)
- **API Framework**: FastAPI (Python 3.10+).
- **Database**: SQLite (Local persistence) with SQLAlchemy ORM.
- **Security**: 
  - `JWT` (JSON Web Tokens) for stateless authentication.
  - `Passlib` (bcrypt) for secure password hashing.
- **Middleware**: CORS handling for cross-origin requests from the React frontend.

---

## 🔄 Core Workflows

### 1. User Onboarding & Auth
1. **Registration**: User signs up with email/password.
2. **Authentication**: User logs in; backend issues a JWT.
3. **Session Persistence**: JWT is stored in local storage and included in the `Authorization` header for all protected API calls.

### 2. Risk Profiling (The "Brains")
1. **Questionnaire**: New users are redirected to a survey covering age, income, and risk tolerance.
2. **Logic**: A weighted algorithm calculates a **Risk Score**.
3. **Categorization**: Users are tagged as *Conservative*, *Moderate*, or *Aggressive*.
4. **Recommendation**: The system maps the risk category to a specific asset allocation (e.g., 80% Equity for Aggressive).

### 3. Investment Simulator (The "Practice")
1. **Virtual Capital**: Users start with ₹1,00,000 in virtual funds.
2. **Trading**: Buy/Sell simulated assets based on "live" market feeds.
3. **Portfolio Engine**: 
   - Backend tracks `Trade` objects.
   - Automatically groups trades to calculate current holdings and average buy prices.
   - Deducts virtual balance on every purchase.

### 4. Goal Management (The "Plan")
1. **Goal Creation**: Users define targets like "Retirement" or "Emergency Fund".
2. **Projection Logic**: Uses compound interest formulas to visualize future growth based on monthly contributions and expected returns.
3. **Tracking**: Real-time progress bars show how close a user is to their milestone.

---

## 📂 Project Structure

```text
ArthaYantra/
├── backend/
│   ├── app/
│   │   ├── main.py        # API Entry & Routing
│   │   ├── auth.py        # JWT & Security logic
│   │   ├── models.py      # SQLAlchemy DB schemas
│   │   ├── schemas.py     # Pydantic data validation
│   │   └── database.py    # DB engine & Session setup
│   └── requirements.txt   # Backend dependencies
├── frontend/
│   ├── src/
│   │   ├── pages/         # Dashboard, Simulator, Market, etc.
│   │   ├── components/    # Reusable UI (Navbar, Charts, Cards)
│   │   ├── context/       # Auth state provider
│   │   ├── api/           # Axios wrappers for backend calls
│   │   └── App.jsx        # Routing & Layout logic
│   └── tailwind.config.js # Design system tokens
└── README.md              # Setup instructions
```

---

## 📈 Data Flow Diagram (Conceptual)
`User Action` ➔ `React Component` ➔ `AuthContext/API Call` ➔ `FastAPI Router` ➔ `SQLAlchemy ORM` ➔ `SQLite DB` ➔ `JSON Response` ➔ `App State Update` ➔ `UI Render`
