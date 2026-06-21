# Reasoning-Fragility-in-Large-Language-Models
Code, dataset, and analysis for studying reasoning stability in large language models. This repository introduces the Reasoning Persistence Error (RPE) metric and provides experiments, bootstrap and Bayesian analyses, and sample reasoning trajectories for evaluating how reasoning chains degrade across iterative generations.
# Reasoning Fragility in Large Language Models

This repository contains the data, analysis scripts, and experimental materials for the paper:

"Reasoning Persistence and Fragility in Large Language Models"

## Overview

Large language models can produce complex multi-step reasoning chains.  
However, when reasoning outputs are recursively reused as inputs, the stability of these reasoning trajectories remains poorly understood.

This project introduces the **Reasoning Persistence Error (RPE)** metric to measure how reasoning accuracy degrades across iterative generations.

## Repository Structure

data/  
Dataset used in the reasoning fragility experiments.

figures/  
All figures used in the paper.

src/  
Core scripts for computing RPE, bootstrap confidence intervals, and Bayesian comparisons.

notebooks/  
Jupyter notebooks for analysis and figure generation.

prompts/  
Prompt templates and reasoning tasks used in experiments.

## Key Contributions

• Introduction of the Reasoning Persistence Error (RPE) metric  
• Empirical analysis of reasoning stability across model scales  
• Bootstrap and Bayesian statistical evaluation  
• Dataset of iterative reasoning trajectories

## Reproducibility

All experiments were conducted using publicly available language models and standardized prompting procedures.

The dataset and evaluation pipeline allow full reproduction of the results presented in the paper.

## Citation

If you use this work, please cite:

[Paper citation will be added after publication]

## License

MIT License
