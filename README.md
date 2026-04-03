# Assignment 2: From Trees to Neural Networks

This repository contains the notebook and saved experiment outputs for **Applied ML - Assignment 2**. The project compares **Gradient Boosted Decision Trees (XGBoost)** and **Multi-Layer Perceptrons (MLP)** on the **Home Credit Default Risk** dataset.

## Repository Structure

```text
.
├── README.md
├── assignment2.ipynb
└── results/
    ├── final_model_comparison.csv
    ├── mlp_architecture_results.csv
    ├── mlp_tuning_results.csv
    ├── xgb_feature_importance.csv
    ├── xgb_learning_rate_results.csv
    ├── xgb_n_estimators_results.csv
    └── xgb_tuning_results.csv
```

## Dataset

This project uses the **Home Credit Default Risk** dataset from Kaggle.

- Dataset source: Kaggle competition `Home Credit Default Risk`
- Main file used: `application_train.csv`
- The raw dataset is not included in this repository

The notebook looks for the dataset in these locations:

```text
/kaggle/input/home-credit-default-risk/application_train.csv
/kaggle/input/competitions/home-credit-default-risk/application_train.csv
./data/application_train.csv
./application_train.csv
```

## What The Notebook Does

`assignment2.ipynb` includes the full workflow:

- data loading and basic feature engineering
- train / validation / test split
- preprocessing fit on training data only
- XGBoost experiments on learning rate, `n_estimators`, and other hyperparameters
- MLP experiments on architecture, activation, learning rate, and max iterations
- validation-based threshold selection using F1
- final retraining on `train + validation`
- test-set comparison between final XGBoost and final MLP models
- XGBoost feature importance export

## Saved Results

The `results/` folder already contains exported tables from the notebook:

- `xgb_learning_rate_results.csv`: XGBoost learning rate comparison
- `xgb_n_estimators_results.csv`: XGBoost `n_estimators` comparison
- `xgb_tuning_results.csv`: XGBoost hyperparameter tuning results
- `xgb_feature_importance.csv`: feature importance values from the final XGBoost model
- `mlp_architecture_results.csv`: MLP architecture comparison
- `mlp_tuning_results.csv`: MLP hyperparameter tuning results
- `final_model_comparison.csv`: final test-set comparison between XGBoost and MLP

## Final Comparison Snapshot

From `results/final_model_comparison.csv`:

| model | accuracy | precision | recall | f1 | auc_pr |
|---|---:|---:|---:|---:|---:|
| Final_XGBoost | 0.83695 | 0.23636 | 0.45704 | 0.31158 | 0.25094 |
| Final_MLP | 0.84946 | 0.23898 | 0.39581 | 0.29802 | 0.21790 |

In these saved outputs, XGBoost achieved the better **AUC-PR** and **F1**, while MLP had slightly higher **accuracy**.

## How To Run

### Option 1: Run in Kaggle

Open `assignment2.ipynb` in Kaggle, attach the Home Credit dataset, and run all cells.

### Option 2: Run locally

1. Download `application_train.csv` from Kaggle.
2. Place it in `./data/` or the repository root.
3. Open and run `assignment2.ipynb`.

Note: this repository currently does **not** include a `requirements.txt`, so local dependencies need to be installed manually.

## Reproducibility Notes

- Random seed is fixed in the notebook
- preprocessing is fit only on the training split before evaluation
- threshold selection is performed on the validation set
- final models are retrained on `train + validation` before test evaluation

## AI Tool Disclosure

AI tools were used for limited support such as debugging, code review, and README polishing. The final experiment design, notebook content, and saved results were reviewed and organized for assignment submission.
