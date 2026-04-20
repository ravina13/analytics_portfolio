# Project 1 · Cybersecurity / Vulnerability Management
## Findings Log

Running record of what each milestone revealed. Written for a non-technical stakeholder
who understands the business context but not the code.

---

## Milestone 1 · Load + First Look
**Date completed:**
**Notebook:** `01_cybersecurity/notebooks/01_eda.ipynb`

### Dataset
- **Source:** NIST National Vulnerability Database (NVD) API 2.0
- **Coverage:** CVEs published Jan–Aug 2024
- **Shape:** 4,000 rows × 15 columns
- **CVSS coverage:** 3,946 / 4,000 rows (98.6%) — near complete

### Key findings
- Mean base score of **6.8** — the average 2024 CVE skews HIGH severity, not medium
- Max base score of **10.0** — perfect-10 critical CVEs exist in this dataset
- Median exploitability score of **2.5** — half of CVEs are relatively easy to exploit
- 75th percentile exploitability = **2.8** — the top quarter are very exploitable

### So what? (business implication)
> A telecom security team cannot treat their 2024 backlog as "mostly medium risk."
> The data shows it skews high. Prioritisation tooling is not optional — it's necessary.

### Data quality notes
- `published` and `last_modified` stored as strings — fixed in M2
- 54 rows (1.4%) missing all CVSS fields — dropped in M2 (status: "Awaiting Analysis")
- All categorical columns stored as plain strings — converted to proper types in M2

---

## Milestone 2 · Data Wrangling
**Date completed:**
**Notebook:** `01_cybersecurity/notebooks/01_eda.ipynb`

### Changes made
- Dropped 54 rows missing CVSS scores → **3,946 rows remaining**
- Converted `published` and `last_modified` to datetime
- Engineered `published_month` and `days_to_modify` features
- Converted severity to ordered categorical: LOW < MEDIUM < HIGH < CRITICAL
- Converted 7 other columns to nominal categories
- Created binary target variable `high_exploitability` (1 = at or above median exploitability)

### Key findings
- Median exploitability score used as threshold: **TBD**
- Class balance — high exploitability (1): **TBD** | low (0): **TBD**

### So what?
> TBD after Cell 9 output

---

## Milestone 3 · EDA
**Date completed:**
**Notebook:** `01_cybersecurity/notebooks/01_eda.ipynb`

### Charts produced
- [ ] Severity distribution (bar chart)
- [ ] Base score distribution (histogram)
- [ ] Attack vector breakdown (bar chart)
- [ ] Exploitability score distribution (histogram)
- [ ] CVE volume over time (line chart)
- [ ] Heatmap: severity × attack vector

### Key findings
- TBD

### So what?
> TBD

---

## Milestone 4 · Model
**Date completed:**
**Notebook:** `01_cybersecurity/notebooks/02_model.ipynb`

### Model
- **Type:** TBD (binary classifier)
- **Target:** `high_exploitability`
- **Features:** TBD
- **Train/test split:** TBD

### Performance
| Metric | Value |
|--------|-------|
| Accuracy | TBD |
| Precision | TBD |
| Recall | TBD |
| F1 | TBD |
| AUC-ROC | TBD |

### Key findings
- TBD

### So what?
> TBD

---

## Milestone 5 · Outputs + Write-up
**Date completed:**

### Deliverables
- [ ] Notebook 1 clean and commented (`01_eda.ipynb`)
- [ ] Notebook 2 clean and commented (`02_model.ipynb`)
- [ ] Key charts saved to `outputs/`
- [ ] `README.md` updated for this project
- [ ] `FINDINGS.md` complete
- [ ] All committed and pushed to GitHub

### Final summary (2–3 sentences for a stakeholder)
> TBD

---

*This log is maintained alongside the code. Last updated: TBD*
