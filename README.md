# FinTrackDB

[![CI](https://img.shields.io/github/actions/workflow/status/Caranthir-0/fintrackdb/python-tests.yml?branch=main)](../../actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue)

CLI tool to manage a small investor database (SQLite), seed from CSV, and compute key ratios (P/E, P/S, P/B, ROE, ROA, ND/EBITDA, L/A).  
Great as a portfolio piece showing Python, lightweight data engineering, and simple CLI UX.

---

## ✨ Features
- Import/seed data from CSV (`companies.csv`, `financial.csv`)
- CRUD operations (create/read/update/delete) for companies & financials
- Computed metrics (ROE/ROA/ND-EBITDA etc.)
- “Top 10 by ratio” listings (ND/EBITDA, ROE, ROA)
- Compact numeric formatting and safe divisions to avoid crashes

---

## 📦 Install
```bash
git clone https://github.com/Caranthir-0/fintrackdb.git
cd fintrackdb
python -m venv .venv
# Windows:
# .venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate
pip install -r requirements.txt
```

---

## ▶️ Run
```bash
python -m src.fintrackdb.main
```
On first run, the app creates `investor.db` at the repo root and seeds from `data/test/*.csv` if the tables are empty.

**Paths in code**
```python
BASE_DIR = Path(__file__).resolve().parents[2]
DB_NAME = str(BASE_DIR / "investor.db")
COMPANIES_CSV = BASE_DIR / "data" / "test" / "companies.csv"
FINANCIAL_CSV = BASE_DIR / "data" / "test" / "financial.csv"
```
Keep your CSVs in `data/test/` (or adjust these constants).

---

## 🧪 Test
```bash
pytest -q
```

---

## 🧹 Lint & Format
```bash
ruff check .
black .
```
Or install pre-commit hooks to run checks automatically:
```bash
pip install pre-commit
pre-commit install
```

---

## 🛠 Tech Stack
- Python 3.10+
- SQLite (built-in `sqlite3`)
- Pytest, Ruff, Black, Pre-commit
- GitHub Actions CI

---

## 📁 Project Structure
```
src/fintrackdb/main.py     # CLI entry
data/test/companies.csv    # seed data
data/test/financial.csv    # seed data
tests/                     # minimal smoke tests
.github/workflows/         # CI
pyproject.toml             # tooling config
.pre-commit-config.yaml    # hooks
requirements.txt
```

---

## 🧭 Usage Tips
- From the **MAIN MENU**, pick CRUD or “Top ten” views.
- In CRUD, you can create/read/update/delete or list all companies.
- “Top ten by ratio” prints a deterministic ranking (by value desc, then ticker asc).

---

## 🚀 Roadmap
- Export reports (CSV/Markdown)
- Package & publish to PyPI (`pip install fintrackdb`)
- Add more ratios & filters
- Optional text UI (TUI) enhancement
