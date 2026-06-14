# Global Internet Adoption Analysis (1990–2024)

A multi-lens statistical analysis of 34 years of global internet growth by combining Exploratory Data Analysis, phase segmentation, logistic curve modelling, and digital divide visualization to explain *how* and *when* the world came online.

---

## Key Findings

- Global internet users grew **1,817× in 34 years**. From 3 million (1990) to 5.45 billion (2024)
- Growth peaked at **100% YoY in 1994**, but the Maturation era (2010–2024) added the most users in absolute terms which are **3.68 billion people**
- A fitted logistic model estimates a **saturation ceiling of ~83%** global penetration (R² = 0.993), with the inflection point at **2014.8**
- The unconnected population began falling in **absolute terms after 2020**, meaning current growth now comes entirely from reaching structurally harder-to-access populations

---

## Analysis Breakdown

### A. Adoption Curve & Penetration Rate
Plots raw internet user counts alongside the global penetration rate (internet users / world population × 100) to show both absolute scale and relative progress. Key milestones ([WWW public launch](https://www.history.com/this-day-in-history/april-30/world-wide-web-launches-in-public-domain), [Google](https://about.google/company-info/our-story/), [iPhone](https://www.history.com/this-day-in-history/january-9/steve-jobs-debuts-the-iphone), [COVID-19](https://www.who.int/news/item/27-04-2020-who-timeline---covid-19)) are annotated by year.

### B. Year-over-Year Growth Rate by Phase
Segments annual growth rates into three historically distinct phases to reveal how the *character* of growth changed over time:

| Phase | Period | Avg YoY Growth | Users Added |
|---|---|---|---|
| Pioneer | 1990–1999 | 67.3% | 0.28B |
| Expansion | 2000–2009 | 20.6% | 1.49B |
| Maturation | 2010–2024 | 7.8% | 3.68B |

### C. Logistic (S-Curve) Model Fit & Projection
Since internet adoption naturally starts slow, accelerates rapidly, and eventually plateaus toward a bounded ceiling, we assume its growth follows an S-shaped curve. So, the logistic model the most theoretically appropriate choice, with basic function:

```
P(t) = L / (1 + e^(−k · (t − t₀)))
```
Then, we got this following value:
| Parameter | Value | Meaning |
|---|---|---|
| L | 83.08% | Saturation ceiling |
| k | 0.1595 | Growth rate steepness |
| t₀ | 2014.8 | Inflection point |
| R² | 0.993 | Model fit quality |

### D. The Digital Divide
Visualizes the connected vs. unconnected population over time as a stacked area chart. Highlights that even at the 75th percentile of observed years (~2015), over **5.65 billion people were still offline**.

---

## Tech Stack

| Library | Purpose |
|---|---|
| `pandas` | Data loading, merging, and feature engineering |
| `numpy` | Numerical operations and logistic curve generation |
| `matplotlib` | Multi-panel visualization |
| `scipy.optimize` | Logistic model fitting via `curve_fit` |

---

## How to Run

1. Clone this repository
```bash
git clone https://github.com/indahtamara/World_Internet_Adoption_Analysis_-1990-2024-.git
cd World_Internet_Adoption_Analysis_-1990-2024-
```

2. Install dependencies
```bash
pip install pandas numpy matplotlib scipy
```

3. Run the analysis
```bash
python World Internet Users Project.ipynb
```
---

## Data Limitation & Handling

The population dataset only extends to **2022**. To compute penetration rates for 2023 and 2024, population values were **linearly extrapolated** based on the average annual growth observed in the three preceding years (2020–2022), yielding estimates of ~8.09B (2023) and ~8.16B (2024).

Linear extrapolation was chosen because population growth at this scale is slow-moving and stable year-to-year, making the introduced error negligible over a two-year window. These values are acknowledged as estimates, not measured data points.
