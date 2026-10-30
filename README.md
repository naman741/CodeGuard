# CodeGuard

Security validation for AI-generated code.
Built for SecureNet 2026 Hackathon (ISEA Project Phase-III), Challenge 2.

## What it does
Paste or upload AI-written code. CodeGuard finds security problems,
gives a risk score, explains each issue in simple words, suggests a
fixed version, and re-scans the fix to confirm it is safe.

## Features
- Vulnerability scan (Bandit + Semgrep + custom rules)
- Hardcoded secrets detection
- Fake / hallucinated package detection (PyPI check)
- AI explanation and fix (LLM)
- Re-scan of fixed code (verification)
- Risk score (0 to 100) and dashboard

## How it works
1. User gives code
2. Scanners find issues (code, secrets, packages)
3. Results are merged and a risk score is calculated
4. LLM explains the issues and rewrites the code
5. Fixed code is scanned again
6. Dashboard shows before/after score and report

## Tech stack
Python, FastAPI, Streamlit, Bandit, Semgrep, detect-secrets, LLM API (Gemini)

## Project structure
- `backend/` : API, scanners, LLM fixer, scoring
- `rules/` : custom Semgrep rules
- `frontend/` : dashboard
- `tests/` : test samples and ground truth
- `docs/` : concept note, report, slides

## Setup
```
git clone https://github.com/naman741/CodeGuard.git
cd CodeGuard
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```
Create a `.env` file (do not upload it) and add:
```
GEMINI_API_KEY=your_key_here
```

## Run
```
uvicorn backend.main:app --reload
streamlit run frontend/app.py
```

## Team
| Name | Role |
|---|---|
| Naman Nandan | Team lead, Backend/API |
| Sourjesh Mohanty | Scanner engine |
| Aena Tariq | Secrets + package checker |
| Avni Shrivastava | LLM fixer + scoring |
| Vaishnavi Singh | Frontend, testing, docs |

## Status
Work in progress.
