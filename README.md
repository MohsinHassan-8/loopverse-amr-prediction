# Antibiotic Resistance Prediction (LoopVerse 2.0 hackathon)

An 11-hour hackathon project: predict whether a bacterial strain is **Resistant** or **Susceptible** to an antibiotic, using data from the BV-BRC pathogen database.

## Data

About 171k raw records, of which roughly half have no resistance label. After removing unlabeled rows, duplicates and spelling variants of antibiotic names, **82,897 rows** remain (69.7% Susceptible, 30.3% Resistant). Cleaning and strain-name grouping are in `LOOP_MAIN_1.ipynb`; the cleaned CSVs are included.

## Models

Inputs are the antibiotic and the strain name only (no genomic features).

| Notebook | Model | Result |
|---|---|---|
| `amr_random_forest` | Random Forest | accuracy 0.73, F1 0.61 |
| `amr_rf_xgboost_tuner` | Random Forest / XGBoost / tuned neural net | RF accuracy 0.751, F1 0.558, ROC-AUC 0.790; best neural net recall 0.737 on the resistant class |
| `amr_models_rf_mlp_tuner` | RF, MLP, Keras Tuner | validation accuracy about 0.73 |

## What I learned

Tuning did not move accuracy past about 0.73-0.75 across many Keras Tuner runs, which points to the feature set, not the model, as the limit: strain and antibiotic names carry little biological signal, and most labels in the source data were themselves model-predicted. Genomic features would be the next step.

---
**Author:** Mohsin Hassan · [GitHub](https://github.com/MohsinHassan-8) · [LinkedIn](https://linkedin.com/in/mohsin-hassan-gen-ai)
