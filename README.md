
# Quantifying the Fragility of Reasoning in Successive Generations of Large Language Models

**Author:** Dr. Pegah Merrikhi · Independent Researcher · PhD in Applied Linguistics

---

## Graphical Abstract

![Graphical Abstract](https://raw.githubusercontent.com/Pegi1727/Reasoning-Fragility-in-Large-Language-Models/main/figures/graphic%20abstractttpng.png)

*Reasoning Predictive Equity (RPE) decays exponentially as recursive generation depth increases.*

---

## Results Snapshot

| Finding | Result |
|---|---|
| Fragility coefficient (`k`) | Larger models show lower `k`, indicating slower semantic degradation |
| Stability horizon (`n₀`) | Larger models preserve coherent reasoning across more generations |
| Task complexity penalty (`Δ`) | More complex tasks produce greater semantic drift |
| Decay dynamics | RPE follows an exponential decline across recursive generations |
| Statistical validation | Bayesian hierarchical modeling supports robust scaling differences |

---

## Overview

Large Language Models (LLMs) demonstrate remarkable reasoning capabilities, yet their reliability under recursive inference remains under-explored. This project introduces **Reasoning Predictive Equity (RPE)**, a quantitative metric that tracks semantic fidelity across successive generations of model-generated reasoning and models degradation as a structured dynamical process.

## Abstract

Large Language Models (LLMs) demonstrate significant reasoning capabilities, yet their reliability under recursive inference remains under-explored. We introduce Reasoning Predictive Equity (RPE), a quantitative metric tracking semantic fidelity across successive generations. Using a recursive evaluation protocol, we demonstrate that reasoning degradation is a structured dynamical process characterized by exponential decay: `RPE(g) = RPE₀ · e^(−kg)`. We identify three regularities: (1) larger models exhibit lower fragility (`k`) and extended stability horizons; (2) task complexity systematically amplifies semantic drift, imposing a structural performance penalty (`Δ`); and (3) degradation follows predictable scaling laws, validated by Bayesian hierarchical modeling.

---

## ⚙️ Methodology

The recursive evaluation protocol comprises five components:

1. **Benchmark-derived task construction** across complexity regimes
2. **Comparative evaluation** of transformer autoregressive language models
3. **Iterative self-conditioned reasoning generation**
4. **Semantic trajectory alignment** using RPE
5. **Statistical modeling** of fragility and collapse dynamics

---

## 🧩 Key Figures

![Reasoning Depth Fragility Curve](https://raw.githubusercontent.com/Pegi1727/Reasoning-Fragility-in-Large-Language-Models/main/figures/reasoning_depth_fragility_curve.png)

*Exponential decay of RPE across generation depth.*

![Collapse Regime](https://raw.githubusercontent.com/Pegi1727/Reasoning-Fragility-in-Large-Language-Models/main/figures/collapse%20regime%204.1.png)

*Transition into the instability/collapse regime.*

![Bayesian Posterior Density](https://raw.githubusercontent.com/Pegi1727/Reasoning-Fragility-in-Large-Language-Models/main/figures/bayesian_posterior_density_plot.png)

*Posterior densities of the fragility coefficient k across model scales.*

![Stability Horizon](https://raw.githubusercontent.com/Pegi1727/Reasoning-Fragility-in-Large-Language-Models/main/figures/stability_horizon_n0%204.4.png)

*Stability horizon n₀ across model scales and task complexity.*

![Benchmark Difficulty Heatmap](https://raw.githubusercontent.com/Pegi1727/Reasoning-Fragility-in-Large-Language-Models/main/figures/benchmark_difficulty_heatmap.png)

*Task difficulty heatmap across benchmarks.*

---
Dr. Pegah Merrikhi — Independent Researcher, PhD in Applied Linguistics

📧 [email] · 🔗 [ORCID / Scholar / LinkedIn

![Benchmark Difficulty Heatmap](https://raw.githubusercontent.com/Pegi1727/Reasoning-Fragility-in-Large-Language-Models/main/figures/benchmark_difficulty_heatmap.png)
