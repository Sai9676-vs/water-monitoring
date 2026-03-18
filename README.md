# University IoT Water Monitoring System

This project is an end-to-end full-stack Internet of Things (IoT) monitoring dashboard built for the College Research Affiliate Program. It dynamically tracks water tank usage via ultrasonic sensor telemetry (distance and temperature) and uses Machine Learning to categorize the usage behavior in real-time.

## 🌟 Features
- **Real-Time Dashboard**: View current water heights, sensor telemetry, and dynamic AI-powered inferences tracking node activity.
- **Machine Learning**: Integrates a highly-accurate Random Forest classifier (`scikit-learn`) optimized via hyperparameter tuning to accurately discern between activities like `washing_machine`, `flush`, and `geyser`.
- **Historical Analysis**: Features detailed `/predictions` charting powered by Recharts (Pie/Confidence Gauges) to review statistical history.
- **Cloud Database (Aiven)**: Safely logs temporal series analysis and AI prediction history asynchronously in a cloud-hosted PostgreSQL instance.
- **Custom Theming**: Incorporates the University's "Deep Blue & Gold" design system for a sleek visual experience.

## 🛠 Tech Stack
- **Frontend**: React.js, Axios, Recharts, Custom CSS (Vercel)
- **Backend**: FastAPI, Uvicorn, SQLAlchemy, Scikit-Learn (Render)
- **Database**: PostgreSQL (Aiven)

## 📦 Local Setup Instructions

### 1. Backend Service
1. Navigate into the backend directory:
   ```bash
   cd backend
   ```
2. Activate a Python virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # Or `.\venv\Scripts\activate` on Windows
   ```
3. Install strict runtime dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Define your `.env` connection strings for the Aiven Cloud DB:
   ```env
   DB_HOST=watermonitoring-cluster.aivencloud.com
   DB_PORT=...
   DB_NAME=defaultdb
   DB_USER=avnadmin
   DB_PASSWORD=...
   DB_SSLMODE=require
   ```
5. Run the server using `uvicorn`:
   ```bash
   uvicorn main:app --reload
   ```

### 2. Frontend Interface
1. Open a new terminal and navigate to the UI root:
   ```bash
   cd frontend
   ```
2. Install node dependencies:
   ```bash
   npm install
   ```
3. Set your internal `.env`:
   ```env
   REACT_APP_API_URL=http://localhost:8000
   ```
4. Launch the local React server on Port 3000:
   ```bash
   npm start
   ```

## 🚀 Cloud Deployment
This project is configured natively for completely zero-touch deployment pipelines!

**Backend (Render API)**
- Reads from the root `render.yaml` orchestration configuration to pull dependencies directly from `backend/requirements.txt`.
- Starts the production `uvicorn main:app --host 0.0.0.0` process.

**Frontend (Vercel UI)**
- Pulls configuration from `frontend/vercel.json` for mapping external HTTP routes over React's native Single Page Application (SPA) logic.

## 📝 Assignment Deliverable Note
Detailed ML optimization reports, analysis of switching models from Keras LSTMs to `joblib` Random Forests, and final Cloud architecture setups are tracked within the `Documentation.md` artifact included inside this repository!
