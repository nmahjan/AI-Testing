# AI Benchmark — Basketball Stats Analyzer

A head-to-head comparison of 6 AI coding tools tasked with the same Python/Flask assignment: build a basketball stats web app that loads CSV data, calculates advanced metrics, and displays results in a styled HTML table.

**[Live Demo → GitHub Pages](https://nmahjan.github.io/AI-Testing/)**

**[Documentation And Comparison](https://docs.google.com/document/d/1fT8Oke9GJe_kEhlyWbY6uQp1HamFvVsCrBT-IBRnYDE/edit?usp=sharing)**
---

## The Task

Each tool was given identical instructions:

- Load `basketball_stats.csv` (player stats: points, rebounds, assists, turnovers, FG%, 3P%, FT%)
- Clean data — fill missing values with column averages, standardize column names
- Calculate three advanced metrics per player:
  - **True Shooting %** — `TS% = pts / (2×FGA + 0.44×FTA)`
  - **Assist-to-Turnover Ratio** — `A/T = assists / turnovers`
  - **Player Efficiency Rating** — `PER = (pts + reb + ast - tov) / 30`
- Display a styled HTML table sorted by PER, highlight top 3 green / bottom 3 red
- Flask backend, plain HTML/CSS frontend, single command to run

---

## The Tools

| Tool | Score /40 | Notes |
|------|-----------|-------|
| **Superpowers** | 35 | Best output — sortable table, 11 unit tests, 4 bugs self-caught |
| **Traycer.ai** | 32 | Best pre-build planning — caught division-by-zero before writing code |
| **Amp** | 32 | Fastest (3–5 min, $0.20). Self-tested. Plain frontend |
| **BMAD v4** | 30 | Solid baseline. Best dark UI but needed 3 manual fixes |
| **BMAD v6** | 30 | Zero-cost upgrade over v4. Autonomous error recovery |
| **Ralph** | 8 | Circuit breaker opened — never produced a working app |

---

## Project Structure

```
tests/
├── bmadv4_imp/        # BMAD v4 implementation (port 8080)
├── traycer_imp/       # Traycer.ai implementation (port 8081)
├── amp_imp/           # Amp implementation (port 8082)
├── superpower_imp/    # Superpowers implementation (port 8083)
├── ralph_imp/         # Ralph implementation (port 8084)
├── bmadv6/            # BMAD v6 implementation (port 8085)
├── switcher/          # Dashboard app (port 8090)
├── start_all.sh       # Start all 7 servers
├── stop_all.sh        # Stop all servers
└── build_static.py    # Pre-render all apps to docs/ for GitHub Pages
docs/                  # Static build for GitHub Pages
```

---

## Run Locally

```bash
pip install flask pandas
cd tests
bash start_all.sh
```

Then open `http://127.0.0.1:8090` for the switcher dashboard.

Stop everything:
```bash
bash stop_all.sh
```

---

## Rebuild Static Site

```bash
python tests/build_static.py
```

Outputs pre-rendered HTML to `docs/` — push and GitHub Pages auto-updates.

---

## Author

Neil Mahajan · April 2026
