# 🚀 Skillverse — Universal AI Skill Marketplace

> **A universal AI skill marketplace where agents publish, discover, purchase, combine, and improve reusable AI skills — all powered by Google Gemini.**

![Status](https://img.shields.io/badge/Status-In%20Development-blue)
![Backend](https://img.shields.io/badge/Backend-FastAPI-green)
![Frontend](https://img.shields.io/badge/Frontend-React-blue)
![Database](https://img.shields.io/badge/Database-SQLite-lightgrey)
![AI](https://img.shields.io/badge/AI-Google%20Gemini-orange)

## 📖 Overview

Skillverse is a full-stack AI skill marketplace that treats AI capabilities as **reusable, tradeable, and composable units** called "Skills." Just like an app store lets you discover and install apps, Skillverse lets AI agents and developers discover, purchase, and execute skills built by others — and monetize their own.

Every skill is a lightweight AI workflow defined by a **prompt template** and executed on-demand using **Google Gemini**. Users can combine multiple skills into a **pipeline** (Skill A → Skill B → Skill C) to build complex multi-step AI workflows without writing any code.

> **Note:** This is a practice/learning project (not enterprise/production-grade) built to demonstrate full-stack engineering, API design, and AI integration.

---

## ✨ Core Features

### 🔐 Authentication & Users
- JWT-based register/login with Bcrypt password hashing
- New users receive **100 free credits** on signup
- Protected routes using FastAPI dependencies

### 🧠 Skill Management
- Publish skills with name, description, category, prompt template, and price
- **Version control** — creators can release v2, v3 without breaking existing purchases
- Categories: Text, Code, Data, Translation, Analysis, Creative, Utilities
- Owner-only editing and deletion

### 🛒 Marketplace & Discovery
- Browse all published skills
- **Search** by name/description
- **Filter** by category, price range, rating
- **Sort** by newest, top-rated, most purchased, price
- Detailed skill page with owner info, ratings, and reviews

### 💰 Credit Economy
- Users spend credits to purchase skills
- Skill owners earn credits when their skills are purchased
- Purchase history and balance tracking
- Transaction-safe credit transfers (DB rollback on failure)

### ⚡ Skill Execution Engine
- Run a skill by providing input text
- Input is injected into the skill's prompt template
- Google Gemini processes the request and returns output
- All executions logged for history
- **Access control** — only owner or purchaser can execute

### 🔗 Skill Pipelines (The Killer Feature)
- Combine 2+ skills into a sequential workflow
- Output of Skill A automatically becomes input to Skill B
- Build no-code multi-step AI automations
- Save, edit, and re-run pipelines

### ⭐ Ratings & Reviews
- 1–5 star rating + text review per user per skill
- Auto-calculated average rating
- Reviews visible on skill detail page
- Sort skills by rating

### 📊 Dashboard
- Stats: total credits, skills published, skills purchased, total runs
- "My Skills" list with edit/delete
- "Purchased Skills" quick access
- Activity feed of recent executions and purchases

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 18, Vite, TailwindCSS, React Router, Axios |
| **Backend** | Python 3.10+, FastAPI, SQLAlchemy, Pydantic |
| **Database** | SQLite (dev) — PostgreSQL-ready |
| **Auth** | JWT (python-jose), Bcrypt (passlib) |
| **AI Engine** | Google Gemini 1.5 Flash |
| **Dev Tools** | Uvicorn, ESLint, PostCSS |

---

## 🏗️ Technical Architecture

### Backend (Python + FastAPI)
- **Router → Service → Model** layered architecture for clean separation
- **SQLAlchemy ORM** with SQLite (easy migration path to PostgreSQL)
- **Pydantic** schemas for request/response validation
- **JWT + Bcrypt** for auth
- **Google Gemini 1.5 Flash** integration via `google-generativeai`
- Auto-generated **OpenAPI/Swagger docs** at `/docs`
- Custom exception handling and structured logging

### Frontend (React + Vite)
- **React 18 + Vite** for blazing-fast dev experience
- **TailwindCSS** with custom design system
- **Glassmorphism UI** — dark theme with purple/indigo gradients and neon cyan accents
- **React Router v6** with protected routes
- **Axios** with interceptors for JWT injection and error handling
- **Context API** for auth and toast state
- Fully responsive — mobile, tablet, desktop

---

## 📂 Project Structure

```text
universal-ai-skill-marketplace/
│
├── backend/
│   ├── app/
│   │   ├── models/          # SQLAlchemy ORM models (User, Skill, etc.)
│   │   ├── schemas/         # Pydantic request/response schemas
│   │   ├── routers/         # API endpoints (auth, skills, etc.)
│   │   ├── services/        # Business logic (Gemini, purchases)
│   │   ├── dependencies/    # FastAPI dependencies (Auth, DB)
│   │   ├── utils/           # Helper functions (JWT, exceptions)
│   │   ├── __init__.py
│   │   ├── main.py          # FastAPI app entry point
│   │   ├── database.py      # DB connection & session
│   │   └── config.py        # Environment variables
│   ├── database/            # SQLite DB files & seed scripts
│   ├── requirements.txt     # Python dependencies
│   └── .env                 # Environment variables (not pushed to Git)
│
├── frontend/                # React + Vite application
│   └── src/
│       ├── api/             # Axios API calls
│       ├── components/      # Reusable UI components
│       ├── pages/           # Route pages (Home, Dashboard, etc.)
│       ├── context/         # React contexts (Auth, Toast)
│       └── hooks/           # Custom React hooks
│
├── docs/                    # API docs, setup guide, screenshots
├── .gitignore               # Git ignore rules
└── README.md                # This file

git clone https://github.com/vishakha2121/agent-skills-marketplace.git
cd agent-skills-marketplace


cd backend
python -m venv venv
# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate

pip install -r requirements.txt


cd backend
python -m venv venv
# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate

pip install -r requirements.txt