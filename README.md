# Precision Livestock Health (PLH) – Behavioural Early-Warning Demo (Synthetic Data)

## **Introduction**

Modern dairy systems increasingly rely on commercial sensor platforms such as DeLaval, Lely, Afimilk, and CeresTag to provide real-time dashboards for rumination, activity, milk yield, SCC, and health alerts. These vendor interfaces are effective for day-to-day monitoring and operational decision support.

However, these systems are inherently vendor-defined: users typically interact with pre-built visualisations and fixed alert logic, with limited ability to extract cloud-hosted data for custom, question-driven analysis. When new biological, clinical, or research questions arise — for example “What behavioural changes precede mastitis across cows?” or “How should baselines be adjusted for parity or environment?” — the standard dashboards are often insufficient.

This repository demonstrates a vendor-agnostic Precision Livestock Health (PLH) analytics concept: starting from cloud-accessible sensor data, independent of the originating platform, and enabling flexible downstream analysis defined by the researcher or clinician, not the dashboard. Using synthetic dairy sensor data, the demo shows how rumination, activity, SCC, and milk production signals can be normalised at the individual-cow level and explored through interpretable visualisations rather than fixed vendor views.

**The emphasis is on:**

- Working directly with data retrieved from vendor clouds (once access is granted)

- Applying cow-specific baselines instead of one-size-fits-all thresholds

- Enabling ad-hoc, hypothesis-driven analysis beyond predefined web interfaces

This workflow is not a replacement for commercial platforms. Instead, it represents a complementary analytics layer that becomes possible once data access is available — supporting research, teaching, and services.

All data in this repository are synthetic, making it safe to share. 

> This repo is a **pilot demo** showing how common dairy sensor signals (rumination, activity, SCC, milk yield) can be transformed into **interpretable early-warning visualisations**.

---

## What’s inside

### 1) Herd rumination heatmap (cow × day)
- Grey = within each cow’s healthy range  
- Red = below healthy range (magnitude encoded)  
- Blue = above healthy range (magnitude encoded)

### 2) Single-cow trend view (example: Cow 13)
- Rumination time series with per-cow thresholds
- Points annotated as Healthy/Flagged

### 3) Rumination vs Activity scatter (context view)
- Used to understand behavioural state changes and how mastitis labels relate to behaviour-space

---

## Quickstart

### Option A — Run the notebook (recommended)
Open:
`notebooks/dairy_ml_trends_notebook_all_cows_annotated.ipynb`

### Option B — Create an environment
```bash
conda env create -f environment.yml
conda activate plh-demo
jupyter lab
