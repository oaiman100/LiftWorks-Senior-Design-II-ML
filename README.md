# LiftWorks — Senior Design II | NACA 4-Series Airfoil Regression

## Project overview
This project evaluates five supervised regression models — **Random Forest (RF), K-Nearest Neighbors (KNN), Decision Tree (DT), Multilayer Perceptron (MLP), and Support Vector Regression (SVR)** — for predicting lift ($C_l$), drag ($C_d$), and pitching-moment ($C_m$) coefficients from NASA PALMO NACA 4-series aerodynamic data.

The dataset contains **52,480 observations across 16 geometries**. Twelve geometries (39,360 observations) are used for model development and four airfoils (13,120 observations: NACA 3415, 3418, 4415, and 4421) are reserved for independent testing.

## Repository contents
| Location | Description |
|---|---|
| `notebooks/FiveModels_Training_Evaluation.ipynb` | Main notebook: five models, documented hyperparameters, optional hyperparameter search, validation, independent testing, and Excel export. |
| `notebooks/Feature_Correlation.ipynb` | Spearman correlation analysis of aerodynamic inputs and outputs. |
| `notebooks/Five_Model_Permutation_Importance.ipynb` | Five-model permutation-importance analysis. |
| `data/PALMO_NACA_4Series_Complete_Dataset.xlsx` | NASA PALMO NACA 4-series dataset. |
| `results/model_workbooks/` | Evaluation workbooks for RF, KNN, DT, MLP, and SVR. |
| `figures/correlation/` | Final full Spearman correlation matrix in navy–orange, provided as PNG and SVG, computed directly from the dataset. |
| `documentation/Final_Engineering_Report_Draft.pdf` | Full engineering design report for context (ML and CFD). |
| `requirements.txt` | Python package requirements. |
| `.gitignore` | Ignore rules for temporary outputs. |

## Running the models
1. Install dependencies: `python -m pip install -r requirements.txt`.
2. Launch Jupyter from the repository root: `jupyter notebook`.
3. Open `notebooks/FiveModels_Training_Evaluation.ipynb` and set `method` to `RF`, `KNN`, `DT`, `MLP`, or `SVR`.
4. Run all cells. The notebook evaluates the selected model and exports its Excel results.
5. Run `Feature_Correlation.ipynb` or `Five_Model_Permutation_Importance.ipynb` for the feature-analysis workflows.

## Methods
**Inputs:** camber (%), thickness (%), Reynolds number, Mach number, and angle of attack. **Targets:** $C_l$, $C_d$, and $C_m$.

The final model configurations are specified in the main notebook for all five algorithms. It performs ten repeated random 70/30 training/validation splits on the twelve development airfoils, followed by training on the complete development set and testing on four independent geometries. The repeated splits are fixed-configuration diagnostics, not a replacement for hyperparameter search. An optional, documented 3-fold SVR search is included in the same notebook; the other models use their specified final configurations. Its optional execution does not change the selected model settings automatically.

Saved result workbooks are supplied to support model comparison; rerunning training is required to independently reproduce the numerical results.

## Data credit
Aerodynamic data are from NASA's PALMO NACA 4-series airfoil dataset. Refer to the full engineering report for the dataset citation. Confirm source redistribution terms before publishing the dataset publicly.


## Notebook roles

- `notebooks/FiveModels_Training_Evaluation.ipynb`: trains, validates, independently tests, and exports results for the five selected configurations.
- `notebooks/FiveModels_Tuning.ipynb`: optional hyperparameter-search implementation for all five models.

