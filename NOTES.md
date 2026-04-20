# Project Notes

Running log of setup decisions, data choices, and "why I did this" context.
Updated as the project evolves — not a polished doc, just honest notes.

---

## Environment setup

| Thing | Detail |
|-------|--------|
| Python | 3.11.15 via Homebrew (`/opt/homebrew/bin/python3.11`) |
| Venv | `.venv/` at repo root — activate with `source .venv/bin/activate` |
| Jupyter | Runs inside venv via VS Code Jupyter extension |
| OS | macOS (Apple Silicon) |

**Why 3.11 and not system Python?**
macOS ships with Python 3.9 at `/usr/bin/python3` — that's Apple's, we never touch it.
3.11 is installed separately via Homebrew into `/opt/homebrew/`, giving us a clean,
upgradeable Python that doesn't affect any macOS internals.

**Why venv and not conda?**
Portability. A `requirements.txt` + `venv` works on any machine with any Python install.
Conda adds a layer of complexity that isn't needed for projects at this scale.

---

## Repo structure

```
analytics-portfolio/
├── .venv/                  # local only, gitignored
├── 01_cybersecurity/
│   ├── data/               # raw data, gitignored
│   ├── notebooks/          # primary coding interface
│   └── outputs/            # saved charts and exports, committed
├── 02_social_data/
│   ├── data/
│   ├── notebooks/
│   └── outputs/
├── .gitignore
├── NOTES.md                # this file
├── README.md
└── requirements.txt
```

**Why is `data/` gitignored?**
Raw data files are often large and sometimes sensitive. Keeping them out of version
control is standard practice. Each project's README will document where to get the data.

---

## Project 1 · Cybersecurity / Vulnerability Management

**Goal:** Vulnerability prioritization analysis for a telecom internal use case.
Model which CVEs to patch first based on CVSS scores and exploitability signals.

**Dataset:** NVD (National Vulnerability Database) — public CVE data
- Source: [nvd.nist.gov](https://nvd.nist.gov)
- Format: CSV extract
- Key fields: CVE ID, CVSS score, severity, attack vector, exploitability score

**Key questions this project answers:**
1. What does the severity distribution look like across our vulnerability backlog?
2. Which attack vectors are most common?
3. Can we predict exploitability from CVSS component scores?

**Milestones:**
- [ ] M1: Load + first look
- [ ] M2: Data wrangling + feature engineering
- [ ] M3: EDA — distributions, trends, breakdowns
- [ ] M4: Model — binary classifier for exploitability
- [ ] M5: Outputs + write-up

**Decisions log:**
- Using CVSS v3 scores where available, falling back to v2
- Treating exploitability score > 2.5 as positive class for the classifier (revisit after EDA)

---

## Project 2 · Social Data (TBD)

**Goal:** A fun, personality-driven project — social trends, media consumption,
or marketing signals. Something with character.

**Dataset:** TBD
**Key questions:** TBD

**Milestones:**
- [ ] M1: Dataset chosen + loaded
- [ ] M2: Wrangling
- [ ] M3: EDA
- [ ] M4: Model or statistical analysis
- [ ] M5: Outputs + write-up

---

## AI workflow notes

This project deliberately uses Claude as part of the workflow. Documenting how:

- Environment setup and troubleshooting: Claude
- Dataset selection and framing: Claude
- Code review and explanation: Claude
- Milestone structure: Claude
- Writing (READMEs, docstrings): Claude-assisted, human-edited

The goal is to demonstrate fluency with AI-assisted development as a real skill —
not to hide it, but to show deliberate, documented use.

---

## Useful commands

```bash
# Start of session
cd ~/projects/analytics-portfolio
source .venv/bin/activate
git pull origin main
code .

# Save work
git add .
git commit -m "your message"
git push origin main

# Add a new package
pip install packagename
pip freeze > requirements.txt

# Rebuild venv on a new machine
python3.11 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```
