# DailyBrief — AI-Powered Morning Briefing & Email Prioritisation System

**FYDP-DSE Group ID:** BSEF23-13
**Department of Software Engineering, FCIT, University of the Punjab, Lahore**
**Supervisor:** Ms. Nataliya Chaudhry

## Team

| Name | Roll Number | Role |
|---|---|---|
| Khubaib Ali Khan | BSEF23A031 | Scrum Master / Backend Lead |
| Nauman Saeed | BSEF23A008 | Product Owner / AI & LLM Lead |
| Sufyan Saeed | BSEF23A011 | Frontend Lead / UI & UX |
| Nimra Waseem | BSEF23A019 | QA Lead / Evaluation & Testing |

## Project Description

DailyBrief connects to a user's Gmail and Google Calendar via OAuth 2.0 and automatically
generates a single, prioritised morning briefing every day. It replaces the 30–45 minutes
professionals typically spend triaging email, calendar, and task apps with one actionable
summary, using a six-dimensional **Daily Priority Score (DPS)** to rank items by real urgency,
auto-generated meeting prep cards, a natural-language command interface, and a
bounded weight-learning mechanism that adapts to each user over time.

See `docs/` for the full proposal, DPS formula derivation, and calibration methodology.

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Next.js 14, Tailwind CSS |
| Backend | Python 3.11, FastAPI |
| Task Scheduling | Celery + Redis |
| LLM / AI | OpenAI GPT-4o API |
| External APIs | Gmail API, Google Calendar API |
| Auth | Google OAuth 2.0 |
| Database | PostgreSQL |
| Dev Tools | Git, GitHub, Docker, Postman, pytest |
| Hosting | Vercel (frontend), Railway/Render (backend + DB) |

## Repository Structure

```
dailybrief/
├── frontend/         # Next.js application
├── backend/          # FastAPI application, DPS engine, Celery worker
├── docs/             # Proposal, design diagrams, calibration notes
├── .github/workflows/ # CI pipeline
└── docker-compose.yml
```

## Setup Instructions

### Prerequisites
- Node.js 18+
- Python 3.11+
- PostgreSQL 14+
- Redis
- Google Cloud project with Gmail API + Calendar API enabled (OAuth credentials)
- OpenAI API key

### Backend

```bash
cd backend
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env            # fill in DB URL, OAuth keys, OpenAI key
uvicorn app.main:app --reload
```

### Celery worker (in a separate terminal)

```bash
cd backend
celery -A celery_worker worker --loglevel=info
```

### Frontend

```bash
cd frontend
npm install
<<<<<<< HEAD
cp .env.example .env.local     # fill in API base URL, OAuth client ID
=======
cp .env.example .env.local      # fill in API base URL, OAuth client ID
>>>>>>> 8e7e9d762b0ee896601febe7bcf7e409e8596ce4
npm run dev
```

### Running Tests

```bash
cd backend
pytest
```

## Environment Variables

See `.env.example` in each of `frontend/` and `backend/` for required keys
(Google OAuth client ID/secret, OpenAI API key, database URL, Redis URL).
Never commit real `.env` files — they are excluded via `.gitignore`.

## Branching Strategy

- `main` — stable, deployable
- `feature/*` — one branch per feature/backlog item, merged via PR
- `fix/*` — bug fixes

## CI/CD (Initial Plan)

GitHub Actions workflow (`.github/workflows/ci.yml`) runs on every push/PR:
1. Install backend dependencies and run `pytest`
2. Lint frontend with `next lint`
3. (Future) Build and deploy to Railway/Vercel on merge to `main`

## Project Status

Currently in **Sprint 1 — Foundation & Auth** (Weeks 1–2): Gmail + Calendar OAuth
integration and 30-day ingestion pipeline. See `docs/sprint-logs/` for sprint summaries.

## License

Academic project — FYDP-DSE, FCIT, University of the Punjab. Not licensed for
<<<<<<< HEAD
=======
commercial use without permission from the authors and department.
>>>>>>> 8e7e9d762b0ee896601febe7bcf7e409e8596ce4
