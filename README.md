# Health Seva — Rural Healthcare Platform

Voice-first rural healthcare platform with ASHA worker coordination, JWT auth, AI chat, diabetes risk analysis, and doctor mapping.

## Quick start

```bash
cd stitch_health_seva_rural_platform
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

Open **http://localhost:8000** in your browser.

## Application flow

| Step | Page | API |
|------|------|-----|
| Landing | `/` | — |
| User signup | `/signup-user.html` | `POST /api/v1/auth/register` (role=USER) |
| ASHA signup | `/signup-asha.html` | `POST /api/v1/auth/register` (role=ASHA) |
| Login | `/login.html` | `POST /api/v1/auth/login` → JWT |
| User dashboard | `/dashboard/user.html` | `/api/v1/dashboard/user/me` |
| ASHA dashboard | `/dashboard/asha.html` | `/api/v1/dashboard/asha/me` |

After login, users are redirected by role (USER → user dashboard, ASHA → ASHA dashboard).

## Project structure

```
app/          FastAPI backend (JWT, SQLite, models)
web/          HTML/CSS/JS frontend (Stitch designs)
  index.html
  login.html
  signup-user.html
  signup-asha.html
  dashboard/user.html
  dashboard/asha.html
  js/         API client & page logic
  css/        Shared styles
```

The Next.js `frontend/` folder has been removed in favor of static HTML served by FastAPI.

## API docs

Interactive docs: **http://localhost:8000/docs**
