# Topic discovery in the University of Patras mailing list archive

Notebooks for my master's thesis: unsupervised topic discovery in the
public mailing list archive of the University of Patras (2018-2023),
using multilingual sentence embeddings (BGE-M3), UMAP, HDBSCAN and
TF-IDF labeling.

## Pipeline

Run the notebooks in order. Each one reads the output file of the
previous one.

| # | Notebook | Input | Output |
|---|----------|-------|--------|
| 01 | make_dataset | mailarchive.upatras.gr | tovima.csv |
| 02 | eda_data_audit | tovima.csv | audit findings |
| 03 | preprocessing | tovima.csv | tovima_clean.csv |
| 04 | nlp_preprocessing | tovima_clean.csv | tovima_nlp_ready.csv |
| 05 | compare_embeddings | tovima_nlp_ready.csv | model decision (BGE-M3) |
| 06 | embedding_generation | tovima_nlp_ready.csv | tovima_embeddings_bge_m3.npy |
| 07 | clustering | embeddings | tovima_clustered.csv, best_params.json |
| 08 | tfidf_labeling | tovima_clustered.csv | tovima_final.csv, cluster_top_terms.csv |
| 09 | validation | tovima_final.csv | baselines, NPMI, sensitivity |
| 10 | temporal_analysis | tovima_final.csv | yearly/monthly figures |

`figures.ipynb` (not part of the pipeline) reproduces Figures 7.1 and 7.2
from `tovima_final.csv`.

## Requirements

- Python 3.13, conda env with: pandas, numpy, scikit-learn, umap-learn,
  hdbscan, optuna, spacy (el_core_news_lg), matplotlib, beautifulsoup4,
  ollama, tqdm
- Ollama with BGE-M3 for notebook 06 (Modelfile inside the notebook)

Data files are not included in the repo.
