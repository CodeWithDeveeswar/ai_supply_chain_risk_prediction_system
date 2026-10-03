# 🚀 AI-Based Supply Chain Risk Prediction System

[![Python](https://img.shields.io/badge/Python-3.10.11-blue.svg)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-3.0.3-black.svg)](https://flask.palletsprojects.com/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-RandomForest-orange.svg)](https://scikit-learn.org/)
[![License](https://img.shields.io/badge/License-Academic-lightgrey.svg)](#-license)

An AI-powered web application that predicts supply chain risk levels using a **Random Forest** machine learning model. The system enables administrators to analyze supply chain data, generate predictions, visualize insights through an interactive dashboard, and export reports.

---

## 📑 Table of Contents

- [Features](#-features)
- [Login Credentials](#-login-credentials)
- [Requirements](#-requirements)
- [Technologies Used](#️-technologies-used)
- [Project Structure](#-project-structure)
- [Installation](#️-installation)
- [Run the Application](#️-run-the-application)
- [Deploy to Render](#-deploy-to-render)
- [Machine Learning](#-machine-learning)
- [Future Enhancements](#-future-enhancements)
- [Author](#-author)
- [License](#-license)

---

## ✨ Features

|     |                                   |
| --- | --------------------------------- |
| 🔐  | Admin Login                       |
| 🤖  | AI-Based Risk Prediction          |
| 📂  | Manual Data Entry & CSV Upload    |
| 📊  | Interactive Dashboard with Charts |
| 📜  | Prediction History                |
| 🔍  | Search & Filter Records           |
| 📥  | Excel Report Export               |
| 🖼️  | Dashboard Image Export            |
| 💾  | SQLite Database Storage           |

---

## 🔐 Login Credentials

A single admin account is used. It is stored in the `users` table and seeded with a default account by `database/db_setup.py`.

| Username | Password   |
| -------- | ---------- |
| `admin`  | `admin123` |

> ⚠️ These are default credentials and are intended for local development and academic use only. Change them before exposing the application publicly.

---

## ✅ Requirements

| Requirement | Version   |
| ----------- | --------- |
| Python      | `3.10.11` |

> 💡 Make sure the correct Python version is installed and active (`python --version`) before creating your virtual environment.

---

## 🛠️ Technologies Used

**Frontend**

- HTML5
- CSS3
- JavaScript
- Bootstrap
- Chart.js

**Backend**

- Python
- Flask

**Machine Learning**

- Scikit-learn
- Pandas
- NumPy
- Joblib

**Database**

- SQLite

---

## 📂 Project Structure

```text
ai_supply_chain_risk_prediction_system/
│
├── app.py
├── requirements.txt
├── config.py
├── .python-version
├── .env
│
├── model/
│   ├── train_model.py
│   ├── risk_model.pkl
│   └── reports/
│
├── database/
│   ├── database.db
│   └── db_setup.py
│
├── data/
│   └── supply_chain_data.csv
│
├── uploads/
│
├── Downloads/
│
├── static/
│   ├── css/
│   └── js/
│
├── templates/
│
└── utils/
    ├── excel_export.py
    └── predictor.py
```

---

## ⚙️ Installation

**1. Clone the repository**

```bash
git clone https://github.com/CodeWithDeveeswar/ai_supply_chain_risk_prediction_system.git
```

**2. Navigate to the project directory**

```bash
cd ai_supply_chain_risk_prediction_system
```

**3. (Optional) Create and activate a virtual environment**

```bash
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate
```

**4. Install dependencies**

```bash
pip install -r requirements.txt
```

**5. (Optional) Configure the secret key**

`SECRET_KEY` is read from a local `.env` file. If it is not set, the app falls back to a default value, which is fine for local development:

```bash
SECRET_KEY=your_random_secret_here
```

> 💡 The `.env` file is gitignored and must never be committed.

---

## ▶️ Run the Application

**1. Initialize the database**

```bash
python database/db_setup.py
```

**2. Train the model**

```bash
python model/train_model.py
```

**3. Start the Flask server**

```bash
python app.py
```

**4. Open your browser**

```
http://127.0.0.1:5000
```

Log in with the credentials listed in [Login Credentials](#-login-credentials).

---

## ☁️ Deploy to Render

This app is configured for deployment to [Render](https://render.com) as a Python Web Service. The trained model (`model/risk_model.pkl`) and the seeded database (`database/database.db`) are committed to the repository, so no retraining or database setup is needed on the server.

**1. Create the Web Service**

Connect the repository at [dashboard.render.com](https://dashboard.render.com) and use these settings:

| Setting           | Value                             |
| ----------------- | --------------------------------- |
| Runtime           | `Python`                          |
| Build Command     | `pip install -r requirements.txt` |
| Start Command     | `gunicorn app:app`                |
| Instance Type     | `Free`                            |
| Health Check Path | `/`                               |

The Python version is pinned to `3.10.11` via the `.python-version` file, so no version needs to be selected in the dashboard. Pinning is required because Render's default Python (3.14) has no prebuilt wheels for the pinned `numpy`/`matplotlib` versions.

**2. Add the secret key**

Under **Environment**, add:

| Key          | Value                  |
| ------------ | ---------------------- |
| `SECRET_KEY` | your random secret key |

**3. Deploy**

Render builds and deploys on every push to the connected branch.

> ⚠️ **Note on the free plan:** Render's filesystem is ephemeral, so newly added predictions and uploaded files are **lost on every deploy or restart**, and the database resets to the committed seed data. For persistence, attach a Render Disk or use a managed PostgreSQL database.

---

## 📊 Machine Learning

| Detail                 | Description                                                                              |
| ---------------------- | ---------------------------------------------------------------------------------------- |
| **Algorithm**          | Random Forest Classifier                                                                 |
| **Prediction Classes** | Low, Medium, High Risk                                                                   |
| **Evaluation Metrics** | Accuracy, Balanced Accuracy, Classification Report, Confusion Matrix, Feature Importance |

---

## 🚀 Future Enhancements

- [ ] Multi-user Authentication
- [ ] Mobile Responsive Design
- [ ] Cloud Database Integration
- [ ] Live Supply Chain Data Feeds
- [ ] REST API Support
- [ ] Deep Learning Models
- [ ] Email Notifications

---

## 👨‍💻 Author

**DEVEESWAR K**

---

## 📄 License

This project is developed for **academic and educational purposes**.
