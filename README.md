# Chronic Kidney Disease Predictor

## CIS 581 Healthcare Project

## Setup

* Install git - see [here](https://git-scm.com/downloads/win) for Windows
* Clone the repo from GitHub:
  `git clone https://github.com/sockduct/HealthPredictor.git`
* Note:  As of February 10, 2025 - the CatBoost Python package used in this
    Jupyter Notebook is not compatible with Python 3.13.  See [here](
    https://catboost.ai/docs/en/concepts/python-installation) for details.
* Install Python 3.12, 64 bit - see
  [here](https://www.python.org/ftp/python/3.12.9/python-3.12.9-amd64.exe) for
  Windows as of February 10, 2025
* Setup and activate a Python virtual environment:
  * Windows:

    ```PowerShell
    PS> py -3.12 -m venv .venv
    PS> .venv\scripts\activate
    ```

* Install required libraries from within Python virtual environment from the root
  directory of the repository (where the master requirements.txt package specifications is):
  `pip install -r requirements.txt`

## Explore Notebooks

* Start the Jupyter lab environment to browse/work on the Notebooks (from the root
  directory of the repository):
  `jupyter lab`

* Dataset Exploration:
  * [Analyze Runs - 100 Random Sampling (Original Dataset)](AnalyzeRuns100Random.ipynb)
  * [Analyze Runs - 100 KNN Imputation (Original Dataset)](AnalyzeRuns100KNN.ipynb)
  * [HealthPredictor Notebook - Original Dataset](HealthPredictor.ipynb)
  * [HealthPredictor Notebook 2 - New Dataset](HealthPredictor2.ipynb)

* Note: Analyze Runs data created using `batch_collector.py`
