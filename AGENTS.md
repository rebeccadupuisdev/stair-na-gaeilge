# AGENTS.md — Stair na Gaeilge

Project-specific context for the **Stair na Gaeilge** Irish language data dashboard.
This file overrides or extends the global `.cursor/rules` where noted.

---

## Project Overview

A data dashboard telling three interconnected stories about the Irish language, using CSO Ireland census data spanning 170 years.

### The Three Stories
1. **The Historical Arc** — 170 years of speaker data (1851–2022)
2. **The Education Cliff** — why speakers drop off sharply after school age
3. **The Sentiment Paradox** — people value Irish but don't speak it daily

---

## Stack

This project uses the global preferred stack without modification:

| Layer | Choice |
|---|---|
| Backend | FastAPI + Jinja2Templates |
| Frontend | HTMX + Tailwind CSS |
| Charts | ECharts v5 |
| Data | Pandas, reading cleaned CSVs from `/data/processed/` |

Do not suggest alternatives to any of these.

---

## Project Structure

```
/
├── main.py                  # FastAPI app, lifespan startup, static file mounting
├── views/
│   └── dashboard.py         # Web route handlers
├── services/
│   └── data_utils.py        # Data loading, cleaning, and caching logic
├── data/
│   ├── raw/                 # Original CSO downloads — never modify
│   └── processed/           # Cleaned CSVs ready for Pandas
├── frontend/
│   ├── static/
│   └── templates/           # Jinja2 templates
│       ├── base.html        # Base layout with Tailwind + HTMX + ECharts CDN links
│       ├── index.html       # Main dashboard page
│       └── partials/        # HTMX HTML fragment templates (one per section)
├── tests/
├── requirements.txt         # fastapi, uvicorn, jinja2, pandas, python-multipart
├── pyproject.toml           # Ruff configuration
├── pytest.ini
├── PROMPT_LOG.md            # Developer-maintained AI prompt log
├── AGENTS.md                # This file
└── README.md                # Includes "Development Approach" section
```

---

## Data

### Census Years Available
`1851, 1901, 1926, 1961, 1981, 1991, 1996, 2002, 2006, 2011, 2016, 2022`

### Data Rules
- `/data/raw/` is read-only — never modify these files
- All cleaning logic lives in `services/data_utils.py`
- Cleaned outputs live in `/data/processed/`
- DataFrames are cached at startup via FastAPI's `lifespan` event — never re-read CSVs per request

---

## Language & Localisation

- Code, comments, and variable names are in **English**
- UI strings and chart labels should offer **bilingual versions (English + Irish)** where practical
- Irish strings must include English translations in adjacent code comments
- The developer owns all Irish-language strings — do not generate or modify them without being asked

---

## Developer Ownership (Project-Specific)

In addition to the global ownership rules, the following are fixed for this project:

- **Data framing** — how decline, resilience, or paradox is narrated belongs to the developer
- **Bilingual labels** — the developer is learning Irish and owns all Irish-language copy
- **Story structure** — the three section titles and their sequencing are fixed; do not reorder or rename

---

## Prompt Logging

This project uses `PROMPT_LOG.md` as documented in the global `prompt_logging.mdc` rule.
The log is part of the developer's portfolio documentation and must be kept up to date after every significant generation.
