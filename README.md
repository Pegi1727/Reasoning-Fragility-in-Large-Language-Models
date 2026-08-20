# Reasoning Predictive Equity (RPE) Implementation
import numpy as np
import pandas as pd
from sklearn.metrics.pairwise import cosine_similarity
from sklearn.feature_extraction.text import TfidfVectorizer

def calculate_rpe(gen_0, gen_g, use_sbert=False):
    """
    Computes RPE. If use_sbert is True, it tries to load SentenceTransformer.
    Otherwise, it falls back to TF-IDF Cosine Similarity for local validation.
    """
    if use_sbert:
        try:
            from sentence_transformers import SentenceTransformer
            model = SentenceTransformer('all-MiniLM-L6-v2')
            embs = model.encode([gen_0, gen_g])
            return cosine_similarity([embs[0]], [embs[1]])[0][0]
        except ImportError:
            print("Sentence-Transformers not found. Falling back to TF-IDF.")
    
    # Fallback: TF-IDF Semantic Alignment
    vectorizer = TfidfVectorizer().fit_transform([gen_0, gen_g])
    vectors = vectorizer.toarray()
    return cosine_similarity([vectors[0]], [vectors[1]])[0][0]

# --- Validation with Empirical Data ---
# Loading real RPE values from the project CSV to check scale
df_rpe = pd.read_csv('[/mnt/data/rpe_vs_generation.csv'](https://gapgpt.app/api/v1/code_interpreter/100563522/9ffda0cf-4648-42be-8604-e840b9d22b85/.eJwNy0sOwiAQANC7zMZNMTgOhPYyEz6DJRraAHZjevf69u8H3y6NS4LlobWxT4M4QVz94LG9pcICc87J65gVWXKKMIhyVpMSRzrMCTE4AxPk8hHe_Vj_pe3CR-eXVGl-lK3eYz9ucF4UDyIM:1wwy97:C4xTs8bodfwcSlgh4-yg6A-PYQV1z8m0ihes_KMhwQw/rpe_vs_generation.csv%27))
print(f"Empirical RPE Range (Llama-70B): {df_rpe['llama_70b'].min():.2f} to {df_rpe['llama_70b'].max():.2f}")

# Example Test Case
gen_0 = "The mathematical proof relies on the law of large numbers."
gen_5 = "Numbers are large in mathematics and proofs are important." # Semantic drift
print(f"Calculated RPE (Gen 0 vs 5): {calculate_rpe(gen_0, gen_5):.4f}")
citation  DOI: 10.5281/zenodo.20785071
