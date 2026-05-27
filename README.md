# 🏏 IPL Crunch '26 — Data Analytics Submission

> **"Teams now choose to field first in 80%+ of IPL matches — yet the field-first win rate collapsed from 65% in 2016 to 43% in 2023, proving that when everyone copies the same strategy, the strategy stops working."**

---

## Live Dashboard
🔗 **[YOUR_USERNAME.github.io/ipl-crunch](https://YOUR_USERNAME.github.io/ipl-crunch)**
*(Spiral loads → 13-page interactive dashboard → scroll or use ↑ ↓ arrow keys)*

---

## What This Submission Covers

| Question | Finding |
|----------|---------|
| Do toss winners win more? | 50.5% — statistically a coin flip. The *decision* (field vs bat) matters 9.4pp more than the toss itself. |
| Which phase decides the game? | Middle overs (7–15) — highest correlation (r=0.333) AND largest run differential (+11.7 runs). Not the death overs. |
| Who are the top performers? | Shubman Gill (2,827 runs, **75% in wins**). KL Rahul has 2,401 runs but only **52% in wins** — empty volume. |
| Surprise insight | Field-first adoption hit 80%+ yet win rate hit a record low of 43% in 2023. Herd behavior destroyed the edge. |

---

## Dataset
- **Source:** IPL ball-by-ball CSV (Cricsheet.org)
- **Coverage:** 2008–2026 · 19 seasons · **1,218 matches · 289,673 deliveries**

---

## Files in This Submission

| File | Description |
|------|-------------|
| `IPL_Crunch_26_Analysis.ipynb` | Full Google Colab notebook — run top to bottom |
| `IPL_Crunch_26_Report.html` | Complete analyst report (open in any browser) |
| `requirements.txt` | Python dependencies |
| `chart1_toss_analysis.png` | Toss winner vs loser + field-first trend |
| `chart2_phase_analysis.png` | Phase analysis + 2nd innings paradox |
| `chart3_player_rankings.png` | Top 5 batters & bowlers with win contribution |
| `chart4_surprise_insights.png` | Herd behavior backfire + PP wicket cliff |
| `chart5_ml_validation.png` | 3 ML models confirming middle overs dominance |

---

## How to Run the Notebook

```bash
# Option 1 — Google Colab (recommended)
# 1. Open IPL_Crunch_26_Analysis.ipynb in Colab
# 2. Upload ipl_matches.csv via Files panel
# 3. Runtime → Run All
# All 5 charts regenerate from scratch in < 3 minutes

# Option 2 — Local
pip install -r requirements.txt
jupyter notebook IPL_Crunch_26_Analysis.ipynb
```

---

## 5 Methodological Decisions That Separate This Analysis

Most submissions get these wrong:

| ✗ Common mistake | ✓ What we did | Why it matters |
|-----------------|--------------|----------------|
| Count wides as balls faced | Excluded wides from balls-faced | Inflates strike rate otherwise |
| Credit bowler for run-outs | Excluded run-outs from wicket counts | Run-outs aren't bowler skill |
| Use all-time player stats | Last 5 seasons only (2022–2026) | Dhawan & Bravo retired; era matters |
| Mix both innings for phase correlation | Innings 1 only for correlation | 2nd innings has chasing selection bias |
| Trust one ML model | 3 independent models (RF + GB + LR) | Consensus across models = robust conclusion |

---

## Key Findings

### Q1 — Toss
- Toss winners win **50.5%** — a coin flip
- Choosing to **field first → 53.7% win rate** (n=803)
- Choosing to **bat first → 44.3% win rate** (n=415)
- **+9.4 percentage point** advantage from the decision alone

### Q2 — Phase Analysis
- **Middle overs (7–15):** r=0.333 correlation, +11.7 run differential — highest of all phases
- **Death overs (16–20):** r=0.298 — second, despite dominating auction conversations
- **Powerplay (1–6):** r=0.238 — lowest, despite all the hype
- Paradox: winning chasers score **39.2** death-over runs vs losing chasers' **40.1**

### Q3 — Players (2022–2026)
- **Shubman Gill:** 2,827 runs · SR 150.5 · **75% in wins** ← best
- **KL Rahul:** 2,401 runs · SR 142.2 · **52% in wins** ← empty volume
- **CV Varun:** 74 wkts · Econ 8.34 · **76% in wins** ← most impactful bowler

### Surprise Finding
Field-first adoption grew from 55% (2016) to 80%+ yet win rate fell from **65% → 43%** in the same period.  
When a strategy becomes universal, it loses its edge entirely.

### ML Validation
3 models trained on pure in-match data (no toss features):
- Random Forest: **69.3%** accuracy
- Logistic Regression: **68.0%** accuracy  
- Gradient Boosting: **63.1%** accuracy
- All 3 independently rank **Middle Run Rate as the #1 predictor**

---


## GitHub Pages Setup

```bash
# 1. Create repo and push
git init
git add .
git commit -m "IPL Crunch 26 — Data Analytics Submission"
gh repo create ipl-crunch --public --push

# 2. Enable GitHub Pages
# Go to: GitHub repo → Settings → Pages → Source: main branch → / (root) → Save
# Your live URL: https://YOUR_USERNAME.github.io/ipl-crunch
```

## Tech Stack
- **Analysis:** Python · pandas · numpy · scikit-learn
- **Visualisation:** matplotlib · seaborn
- **Dashboard:** Next.js 14 · Tailwind CSS · Framer Motion
- **Deployment:** GitHub Pages
