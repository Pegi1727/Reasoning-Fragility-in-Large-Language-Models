# =====================================================================
# Reasoning Predictive Equity (RPE) Implementation & Validation
# ---------------------------------------------------------------------
# Repository: https://github.com/Pegi1727/Reasoning-Fragility-in-Large-Language-Models
# Citation DOI: 10.5281/zenodo.20785071
# =====================================================================

import os
import numpy as np
import pandas as pd
from sklearn.metrics.pairwise import cosine_similarity
from sklearn.feature_extraction.text import TfidfVectorizer

def calculate_rpe(gen_0: str, gen_g: str, use_sbert: bool = False) -> float:
    """
    Computes the Reasoning Predictive Equity (RPE) metric.
    
    Quantifies semantic fidelity between initial (gen_0) and recursive (gen_g)
    generations using SBERT embeddings (preferred) or a deterministic TF-IDF fallback.
    
    Parameters:
        gen_0 (str): Baseline/initial step reasoning trace.
        gen_g (str): Step-g recursive generation reasoning trace.
        use_sbert (bool): Flag to utilize SentenceTransformer ('all-MiniLM-L6-v2').
        
    Returns:
        float: Cosine similarity score bounded in [-1.0, 1.0].
    """
    if use_sbert:
        try:
            from sentence_transformers import SentenceTransformer
            model = SentenceTransformer('all-MiniLM-L6-v2')
            embs = model.encode([gen_0, gen_g])
            return float(cosine_similarity([embs[0]], [embs[1]])[0][0])
        except (ImportError, Exception) as e:
            print(f"[Warning] SBERT unavailable ({e}). Falling back to TF-IDF cosine similarity.")
    
    # Deterministic local fallback: TF-IDF vectorization
    vectorizer = TfidfVectorizer()
    vectors = vectorizer.fit_transform([gen_0, gen_g]).toarray()
    return float(cosine_similarity([vectors[0]], [vectors[1]])[0][0])

# =====================================================================
# Empirical Data Validation
# =====================================================================
data_path = '[/mnt/data/rpe_vs_generation.csv'](https://gapgpt.app/api/v1/code_interpreter/100563522/9ffda0cf-4648-42be-8604-e840b9d22b85/.eJwNy0sOwiAQANC7zMZNMTgOhPYyEz6DJRraAHZjevf69u8H3y6NS4LlobWxT4M4QVz94LG9pcICc87J65gVWXKKMIhyVpMSRzrMCTE4AxPk8hHe_Vj_pe3CR-eXVGl-lK3eYz9ucF4UDyIM:1wwyHQ:4w9k9GlmV5rPB9HD1NTQ4ekY3vjrycKaKyNJPbDAdbA/rpe_vs_generation.csv%27)

if os.path.exists(data_path):
    df_rpe = pd.read_csv(data_path)
    print(f"Empirical Data Loaded successfully from: {data_path}")
    print(f"Empirical RPE Range (Llama-70B): {df_rpe['llama_70b'].min():.4f} to {df_rpe['llama_70b'].max():.4f}")
else:
    print(f"[Notice] Empirical file '{data_path}' not found locally. Running in standalone mode.")

# Test Case Demonstration
gen_0 = "The mathematical proof relies on the law of large numbers."
gen_1 = "The proof in mathematics depends strictly on the law of large numbers." # High fidelity
gen_5 = "Numbers are large in mathematics and proofs are important."              # Semantic drift

print("\n--- Validation Scores ---")
---
@software{merrikhi_2026_zenodo20785071,
  author       = {Merrikhi, Pegah},
  title        = {Quantifying the Fragility of Reasoning in Successive Generations of Large Language Models: Code and Empirical Data},
  year         = {2026},
  publisher    = {Zenodo},
  version      = {v1.0.0},
  doi          = {10.5281/zenodo.20785071},
  url          = {https://doi.org/10.5281/zenodo.20785071}
}
---
Merrikhi, P. (2026). Quantifying the Fragility of Reasoning in Successive Generations of Large Language Models (Version 1.0.0) [Computer software]. Zenodo. https://doi.org/10.5281/zenodo.20785071
print(f"RPE (Gen 0 vs 1 - High Fidelity): {calculate_rpe(gen_0, gen_1):.4f}")
print(f"RPE (Gen 0 vs 5 - Semantic Drift): {calculate_rpe(gen_0, gen_5):.4f}")
