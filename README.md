# CIE 457 — Statistical Inference and Data Analysis
## MLE Estimation and Estimator Distribution in Linear Regression

**University of Science and Technology · Zewail City — Spring 2026**

| | |
|---|---|
| **Authors** | Ibrahim Hanafy · 202200518 &ensp;·&ensp; Mai Ibrahim · 202200504 &ensp;·&ensp; Mohamed Alaa · 202100905 |
| **Instructor** | Dr. Mahmoud Abdelaziz |
| **Teaching Assistants** | Eng. Nasrah Mohamed · Eng. Aya Abdelaziz |

---

## Project Overview

This project investigates **Maximum Likelihood Estimation (MLE) in linear regression** — specifically how the OLS estimator is derived as the MLE under Gaussian noise, how it behaves as a random variable across repeated experiments, and how it compares to WLS when the homoscedastic assumption breaks down.

The work is divided into four parts plus a theory section and a bonus:

| Part | Topic |
|---|---|
| **Theory** | MLE derivation — homoscedastic and heteroscedastic likelihoods, estimator distribution |
| **Part 1** | Monte Carlo simulation of OLS under homoscedastic noise — empirical vs theoretical distribution |
| **Part 2** | OLS vs WLS efficiency comparison under heteroscedastic noise via Monte Carlo |
| **Part 3** | Confidence intervals for β̂ and prediction intervals for new observations |
| **Part 0 / Part 4** | Exploratory data analysis and real data application — Advertising dataset |
| **Bonus** | Fisher Information Matrix, Cramér-Rao Lower Bound, Sufficient Statistics |

---

## Folder Structure

```
Project/
│
├── README.md                          ← you are here
│
├── notebook/
│   └── Statistical_Inference_and_Data_Analysis_Project_v2.ipynb
│       The main notebook.
├── figures/
│   ├── homo_distribution.png          ← Part 1: OLS estimator distribution
│   ├── hetero_distribution.png        ← Part 2: OLS vs WLS distributions
│   ├── hetero_variance_comparison.png ← Part 2: variance bar chart
│   ├── ci_plot.png                    ← Part 3: CI coverage across MC trials
│   ├── ci_vs_pi.png                   ← Part 3: CI vs PI width comparison
│   ├── eda_distributions.png          ← EDA: variable histograms
│   ├── eda_correlation.png            ← EDA: Pearson correlation heatmap
│   ├── eda_scatter.png                ← EDA: feature vs sales scatter
│   ├── eda_pairplot.png               ← EDA: pairwise relationships
│   ├── residual_diagnostics.png       ← Part 4: OLS residual analysis
│   ├── hetero_evidence.png            ← Part 4: squared residuals vs features
│   └── ols_vs_wls_real.png            ← Part 4: OLS vs WLS on real data
│
├── report_and_presentation/
│   ├── Statistical_Inference_and_Data_Analysis_Project_Report.pdf
│   └── presentation.pptx
│
└── CIE 457-Project-Sp2026.pdf         ← original project specification
```

---

## How to Run

### Requirements

```bash
pip install numpy pandas matplotlib seaborn scipy statsmodels
```

### Run the notebook

1. Open `notebook/Statistical_Inference_and_Data_Analysis_Project_v2.ipynb` in Jupyter or VS Code
2. Run all cells top to bottom (`Kernel > Restart & Run All`)
3. All figures are automatically saved to `figures/` — they overwrite the existing ones

> The notebook fetches the Advertising dataset from the internet (one `pd.read_csv` call). Internet connection required for Part 4 / EDA.

### Expected runtime

Approximately **30–60 seconds** — the Monte Carlo loop runs M = 5000 trials twice (Parts 1 and 2).

---

## Key Results

- **OLS is the exact MLE** under homoscedastic Gaussian noise; its distribution is analytically **N(β, σ²(XᵀX)⁻¹)**
- Monte Carlo simulations with M = 5000 trials confirm this distribution empirically with <0.5% error on covariance diagonals
- Under heteroscedastic noise, **WLS achieves 1.5–3× lower variance** than OLS across all coefficient components
- Confidence interval coverage matches the nominal 95% level to within ±0.5% across all parameters
- **White's test** (p < 0.001) formally rejects homoscedasticity on the Advertising dataset — WLS is the appropriate estimator
- OLS is shown to achieve the **Cramér-Rao Lower Bound** — it is UMVUE under Gaussian noise
