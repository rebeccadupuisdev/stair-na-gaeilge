# Stair na Gaeilge

FastAPI + HTMX dashboard visualizing 170 years of Irish language census data across three narratives: historical decline, the education cliff, and the sentiment paradox. Built as a deliberate human–AI collaboration exercise with documented prompt logging.

## The Three Stories

**1. The Historical Arc**
Speaker numbers from 1851 to 2022 — from the aftermath of the Famine to the present day. The long view of a language under pressure.

**2. The Education Cliff**
Census data shows a sharp drop-off in Irish speakers after school age. This section asks why fluency doesn't survive the transition to adult life.

**3. The Sentiment Paradox**
Survey data from Foras na Gaeilge reveals a gap between how people feel about Irish and how often they actually use it. High cultural attachment, low daily use.

## Tech Stack

- **Backend:** FastAPI + Jinja2 templates
- **Frontend:** HTMX + Tailwind CSS
- **Charts:** ECharts v5
- **Data:** Pandas, loading cleaned CSVs from `/data/processed/`

## Data Sources

- CSO Ireland census data (1851–2022)
- Foras na Gaeilge attitude and usage surveys
- Gaeltacht boundary GeoJSON from data.gov.ie (planned, for future map component)

## Project Structure

```
/
├── main.py                # Application entry point
├── views/                 # Web route handlers
│   └── dashboard.py
├── services/              # Business and data logic
│   └── data_utils.py
├── data/
│   ├── raw/               # CSO downloads — never modify
│   └── processed/         # Cleaned CSVs (committed)
├── frontend/
│   ├── static/
│   └── templates/         # Jinja2 templates
│       ├── base.html
│       ├── index.html
│       └── partials/      # HTMX fragment templates
├── tests/
├── requirements.txt
├── pyproject.toml         # Ruff configuration
├── pytest.ini
├── PROMPT_LOG.md
└── README.md
```

## Getting Started

Requires Python 3.11+.

```bash
python -m venv .venv
source .venv/bin/activate       # Windows: .venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
```

Processed data CSVs are committed in `/data/processed/`. Raw CSO source files are not — see Data Sources above for where to obtain them.

## Development Approach

This project was built with Cursor as an AI-assisted coding environment. Rather than treating AI output as a black box, every significant generation is logged in `PROMPT_LOG.md` — recording what was prompted, what was produced, what was changed, and what was learned in the process.

The goal is to document genuine human–AI collaboration honestly: the AI handles boilerplate and scaffolding; decisions about narrative framing, bilingual labels, data interpretation, and architecture stay with the developer.

## Bilingual UI

Labels in the dashboard appear in both English and Irish. The Irish language isn't just the subject of this project — it's present in it.

---

*Tá an teanga beo fós.* (The language is still alive.)