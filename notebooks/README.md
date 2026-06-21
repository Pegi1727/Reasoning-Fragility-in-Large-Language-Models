# Analysis & Visualization Notebooks

This directory contains Jupyter Notebooks used for data processing, statistical modeling, and producing the figures presented in the paper.

## Notebook Inventory:

1. **`01_fragility_analysis.ipynb`**: 
   - Computes the fragility coefficient ($k$) and Reasoning Persistence Error (RPE) curves for each LLM.
   - Performs Bayesian parameter estimation and hypothesis testing (HDI/ROPE).

2. **`02_paper_plots.ipynb`**:
   - Recreates the publication-quality figures (including the fragility landscape and multi-panel RPE decay plots) directly from the CSV files in `data/`.

## Requirements:
To run these notebooks, install the required packages:
```bash
pip install numpy pandas matplotlib seaborn scipy pymc arviz

