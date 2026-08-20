# Quantifying the Fragility of Reasoning in Successive Generations of Large Language Models

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20785071.svg)](https://doi.org/10.5281/zenodo.20785071)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Paper Target](https://img.shields.io/badge/Target-Nature%20Human%20Behaviour-critical.svg)](#citation)

---

## 📊 Empirical Visualizations & Figures Overview

All primary figures generated from the empirical evaluation across recursive generations ($g \in [0, 10]$) and model parameter scales (7B, 13B, 70B):

| **Figure 1: Conceptual Framework & Recursive Degradation** | **Figure 2: Multi-Step Evaluation Pipeline** |
| :---: | :---: |
| ![Figure 1: Conceptual Framework](figures/figure1_conceptual_framework.png) | ![Figure 2: Evaluation Pipeline](figures/figure2_evaluation_pipeline.png) |
| *Recursive reasoning degradation and semantic entropy.* | *End-to-end multi-step evaluation workflow.* |

| **Figure 3: Semantic Alignment Trajectories (RPE)** | **Figure 4: Model Scale vs. Reasoning Fidelity** |
| :---: | :---: |
| ![Figure 3: RPE Trajectory](figures/figure3_rpe_trajectory.png) | ![Figure 4: Model Scale Comparison](figures/figure4_model_scale_comparison.png) |
| *RPE trajectories across successive recursive cycles.* | *Empirical scaling effects on retention across model sizes.* |

| **Figure 5: Non-Linear Exponential Decay Fitting ($k$)** | **Figure 6: Critical Stability Horizon ($\tau = 0.7$)** |
| :---: | :---: |
| ![Figure 5: Fragility Fit](figures/figure5_fragility_fit.png) | ![Figure 6: Stability Horizon](figures/figure6_stability_horizon.png) |
| *Exponential decay fit: $\text{RPE}(g) = \text{RPE}_0 e^{-kg}$.* | *Stability Horizon ($n_0$) threshold bounds across scales.* |

| **Figure 7: Reasoning Collapse Zone & Drift** | **Figure 8: Bayesian Posterior Distribution of $k$** |
| :---: | :---: |
| ![Figure 7: Collapse Zone](figures/figure7_collapse_zone.png) | ![Figure 8: Bayesian Posterior](figures/figure8_bayesian_posterior.png) |
| *Degradation bounds and catastrophic semantic drift zone.* | *Posterior parameter distributions with 95% HDI.* |

<p align="center">
  <b>Figure 9: Comprehensive Fragility Density & Parameter Synthesis</b><br>
  <img src="figures/figure9_density_plots.png" alt="Figure 9: Parameter Synthesis and Density Plots" width="85%">
</p>

---

## 📌 Executive Summary

This repository contains the empirical datasets, mathematical formulations, analysis pipelines, and replication code for the study:
> **"Quantifying the Fragility of Reasoning in Successive Generations of Large Language Models"** (Manuscript ID: NLP-2026-0255).

### Key Research Questions & Findings
1. **Mathematical Decay Dynamics:** Semantic consistency across recursive inference rounds follows an exponential decay function:
   $$\text{RPE}(g) = \text{RPE}_0 \cdot e^{-k \cdot g}$$
2. **Scale Invariance & Fragility Coefficients ($k$):** Larger parameter scales (70B) demonstrate lower fragility ($k \approx 0.10$) compared to base scales (7B, $k \approx 0.22$), extending the functional lifespan of recursive chains.
3. **Stability Horizon ($n_0$):** Using a critical threshold ($\tau = 0.70$), the Bayesian stability horizon indicates bounds beyond which multi-step recursive reasoning suffers irreversible semantic drift.

---

## 📂 Repository Structure
```text
├── data/
│   ├── rpe_vs_generation.csv            # Empirical RPE scores across generations (0–10)
│   ├── fragility_coefficients.csv       # Estimated k parameters and goodness-of-fit (R²)
│   ├── stability_horizon.csv            # Calculated n0 values across model scales
│   ├── bayesian_hdi_fragility.csv       # Bayesian posterior means and 95% HDIs
│   └── LLM_reasoning_fragility_datasets.xlsx # Aggregated multi-sheet experimental data
├── figures/                             # High-resolution vector and raster assets (Fig 1–9)
├── notebooks/
│   ├── 01_RPE_Calculation_and_Validation.ipynb # SBERT semantic alignment & validation
│   ├── 02_Fragility_Coefficient_Analysis.ipynb # Non-linear regression for decay parameter k
│   ├── 03_Bayesian_Stability_Horizon.ipynb     # Posterior estimation & stability bounds
│   └── 04_figure_generation.ipynb              # Publication-grade figure production
├── requirements.txt                     # Pinned environment dependencies
-----
# Clone repository
git clone https://github.com/Pegi1727/Reasoning-Fragility-in-Large-Language-Models.git
cd Reasoning-Fragility-in-Large-Language-Models

# Create and activate environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install requirements
pip install -r requirements.txt
----
numpy>=1.24.0
pandas>=2.0.0
scipy>=1.10.0
scikit-learn>=1.2.0
sentence-transformers>=2.2.0
matplotlib>=3.7.0
seaborn>=0.12.0
openpyxl>=3.1.0
---
@software{merrikhi_2026_zenodo20785071,
  author       = {Merrikhi, Pegah},
  title        = {Quantifying the Fragility of Reasoning in Successive Generations of Large Language Models: Empirical Data and Analysis Pipeline},
  year         = {2026},
  publisher    = {Zenodo},
  version      = {v1.0.0},
  doi          = {10.5281/zenodo.20785071},
  url          = {https://doi.org/10.5281/zenodo.20785071}
}

├── LICENSE                              # MIT License
└── README.md                            # Main project documentation
