# Chronic Kidney Disease Prediction

## Project Overview

This project applies machine learning to classify chronic kidney disease (CKD)
from clinical and laboratory measurements. It compares preprocessing strategies
and classification algorithms to identify models that can support early CKD
risk assessment.

The repository contains end-to-end Jupyter Notebook experiments for data
cleaning, missing-value imputation, model training, hyperparameter tuning,
cross-run analysis, and model serialization.

## Datasets

The project uses two datasets:

- **UCI CKD dataset:** The original 400-record dataset contains 24 clinical
  and demographic attributes. It was sourced from the
  [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/336/chronic+kidney+disease)
  and the local copy is in
  [`Data/Chronic_Kidney_Disease/`](Data/Chronic_Kidney_Disease/).
- **Kaggle CKD dataset:** A 1,659-record dataset with 52 columns. The Kaggle
  source and local data files are documented in
  [`Data/README.md`](Data/README.md). The data copy is in
  [`Data/chronickidneydisease-kaggle-1659x52.csv`](Data/chronickidneydisease-kaggle-1659x52.csv).

The target variable is `classification` in the UCI data and `Diagnosis` in the
Kaggle data. For the cleaned UCI workflow, predictor columns include clinical
features such as age, blood pressure, specific gravity, albumin, blood glucose,
blood urea, serum creatinine, hemoglobin, hypertension, diabetes mellitus,
appetite, edema, and anemia.

The preprocessing notebooks also document encoding, duplicate removal,
normalization or scaling, train/test splitting, and KNN-based missing-value
imputation.

## Tech Stack

- Python
- Jupyter Notebook
- Pandas and NumPy
- Scikit-learn
- XGBoost
- Matplotlib, Seaborn, and Plotly
- CatBoost and LightGBM in additional experiments

## Methodology

- Clean and encode clinical data.
- Explore distributions and relationships between variables.
- Handle missing values, including KNN imputation.
- Split data into training and test sets.
- Train and compare Decision Tree, Random Forest, XGBoost, and Logistic
  Regression classifiers.
- Tune selected models with hyperparameter search.
- Evaluate test-set performance using accuracy, confusion matrices,
  classification reports, precision, recall, and F1-score.
- Compare repeated runs and imputation strategies in the analysis notebooks.
- Save trained models as `.pkl` files for reuse.

## Results

Recorded results from the primary UCI notebook
[`CKDPrediction.ipynb`](CKDPrediction.ipynb) include:

| Model | Test accuracy |
|---|---:|
| Decision Tree | 94.17% |
| Decision Tree with tuning | 95.00% |
| Random Forest | 100.00% |
| XGBoost | 99.17% |
| Logistic Regression | 97.50% |

Random Forest achieved the strongest test performance in this run. These values
depend on the selected dataset, split, preprocessing, and random seed, so they
should be compared across the repeated-run notebooks rather than treated as
guaranteed production performance.

The Kaggle experiment in
[`CKDPrediction2.ipynb`](CKDPrediction2.ipynb) achieved 92.57% test accuracy
with XGBoost, 91.77% with Random Forest, and 91.37% with Logistic Regression.

## Repository Files

### Main Notebooks

- [`CKDPrediction.ipynb`](CKDPrediction.ipynb) - primary UCI dataset
  preprocessing and model comparison.
- [`CKDPrediction2.ipynb`](CKDPrediction2.ipynb) - Kaggle dataset
  preprocessing and model comparison.
- [`DataPreprocessing.ipynb`](DataPreprocessing.ipynb) - data preparation
  and cleaning workflow.
- [`Original_Data_Cleaning.ipynb`](Original_Data_Cleaning.ipynb) - detailed
  original data-cleaning exploration.
- [`Original_Model_Buildout.ipynb`](Original_Model_Buildout.ipynb) - detailed
  original model-building experiments.

### Supporting Notebooks

- [`AnalyzeRuns100Random.ipynb`](AnalyzeRuns100Random.ipynb)
- [`AnalyzeRuns100KNN.ipynb`](AnalyzeRuns100KNN.ipynb)
- [`AnalyzeRuns250KNN.ipynb`](AnalyzeRuns250KNN.ipynb)
- [`Knn_Imputation_HealthPredictor_NoOutput.ipynb`](Knn_Imputation_HealthPredictor_NoOutput.ipynb)
- [`Knn_Imptn_XGBoost_HealthPredictor_NoOutput.ipynb`](Knn_Imptn_XGBoost_HealthPredictor_NoOutput.ipynb)

The `-NoOutput` versions contain executable notebook workflows without saved
cell output.

## How to Run Locally

### 1. Clone the repository

```powershell
git clone https://github.com/gitmeprius/CKD_Prediction.git
cd CKD_Prediction
```

### 2. Create and activate a virtual environment

```powershell
py -3.12 -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
```

Python 3.12 is recommended. CatBoost may not support Python 3.13.

### 3. Install dependencies

```powershell
python -m pip install -r requirements.txt
python -m pip install jupyterlab catboost lightgbm nbclient
```

The additional notebook dependencies ensure that Jupyter and all experiment
libraries are available.

### 4. Start Jupyter Lab

```powershell
jupyter lab
```

Open [`CKDPrediction.ipynb`](CKDPrediction.ipynb) for the primary UCI analysis
or [`CKDPrediction2.ipynb`](CKDPrediction2.ipynb) for the Kaggle analysis.
Run the cells in order from the repository root.

## Repeated Experiments

Use `batch_collector.py` to execute a notebook multiple times:

```powershell
python batch_collector.py CKDPrediction.ipynb -t 100
```

Each run uses a notebook copy in memory; the script prints timing and execution
status for the run to the terminal.

## Saved Models

The repository includes serialized model and data artifacts:

- `CKD-UCI.pkl`
- `CKD-Kaggle.pkl`
- `CKD-XGB.pkl`
- `CKD-XGB-UCI.pkl`
- `CKD-XGB-Kaggle.pkl`

## License

This project is distributed under the
[BSD 3-Clause License](LICENSE).
