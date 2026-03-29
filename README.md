# Treatment Effect Analysis with DiD in Lalonde dataset
# Does Job Training Raise Earnings?

---

## Overview

This project applies the **Difference-in-Differences (DiD)** estimator to the LaLonde (1986) dataset to answer a causal question: did the National Supported Work (NSW) job training programme raise participants' real earnings?

The dataset is uniquely valuable because the true causal effect is known from a concurrent randomised experiment (**RCT benchmark: $1,794**), allowing direct validation of the non-experimental estimator.

**Main finding:** DiD estimates a treatment effect of **$1,529** (95% CI: $152–$2,906, p = 0.030), recovering a value close to the experimental ground truth.

<!-- ---

## Project Structure

```
├── lalonde_did_causal_inference.ipynb   # Full analysis notebook
├── lalonde_did_report.pdf               # LaTeX report (compiled)
├── lalonde_did_report.tex               # LaTeX source
└── README.md
``` -->

<!-- ---

## Notebook Contents

| Section | Description |
|---------|-------------|
| 0 | Setup — packages, plot style, colour palette |
| 1 | Data loading, EDA, baseline balance table |
| 2 | Causal DAG and identification strategy |
| 3 | Naive OLS — quantifying selection bias |
| 4 | DiD via panel regression with interaction term |
| 5 | Parallel trends check + placebo falsification test |
| 6 | Robustness across specifications + E-value sensitivity |
| 7 | Estimator comparison against RCT benchmark |
| 8 | Interpretation and limitations |
| 9 | Heterogeneous treatment effects across 10 subgroups |

---

## Setup

```bash
pip install causaldata statsmodels matplotlib seaborn scipy numpy pandas
``` -->


---

## Key Results

| Estimator | Estimate | 95% CI | p-value |
|-----------|----------|--------|---------|
| Naive OLS | $1,794 | [$553, $3,036] | 0.005 |
| OLS + controls | $1,676 | [$422, $2,931] | 0.009 |
| **DiD (main)** | **$1,529** | **[$152, $2,906]** | **0.030** |
| DiD + controls | $1,529 | [$165, $2,893] | 0.028 |
| RCT ground truth | $1,794 | — | — |

Placebo DiD (pre-periods only): $277, p = 0.644 — supports parallel trends assumption.

---

## Dataset

`nsw_mixtape` from the [`causaldata`](https://github.com/NickCH-K/causaldata) package — the standard implementation of the LaLonde (1986) National Supported Work data. 445 observations: 185 treated, 260 control. Earnings measured in 1974, 1975 (pre-treatment) and 1978 (outcome).

---

<!-- ## Reference

LaLonde, R.J. (1986). *Evaluating the Econometric Evaluations of Training Programs with Experimental Data.* **American Economic Review**, 76(4): 604–620. -->