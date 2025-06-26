# C108 Final Project: Heart Disease Risk Analysis

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Repository Structure](#repository-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Key Findings](#key-findings)
- [Ethics & Bias Considerations](#ethics--bias-considerations)
- [Next Steps](#next-steps)
- [License](#license)

## Overview

This repository contains a comprehensive data science project aimed at exploring, modeling, and interpreting risk factors for heart disease using the 2020 CDC Behavioral Risk Factor Surveillance System (BRFSS) dataset. Our primary research question is: **How does diabetes status interact with self‑reported physical and mental health days to predict heart disease risk?**

## Dataset

- **Source**: Personal Key Indicators of Heart Disease on Kaggle (originally from the 2020 CDC BRFSS survey)
- **Link**: [https://www.kaggle.com/datasets/kamilpytlak/personal-key-indicators-of-heart-disease](https://www.kaggle.com/datasets/kamilpytlak/personal-key-indicators-of-heart-disease)
- **Cleaning & Processing**: Categorical flags (e.g. `Yes`/`No`), age categories, and general health ratings were recoded into numeric formats. Missing or special values are handled in the notebook `data_processing.ipynb`.

## Repository Structure

```
├── data/                         # raw and cleaned CSV files
│   ├── heart_2020_raw.csv        # original dataset
│   └── heart_2020_cleaned.csv    # post-cleaning subset
├── notebooks/                    # exploratory and modeling notebooks
│   ├── 01_data_processing.ipynb
│   ├── 02_exploratory_analysis.ipynb
│   ├── 03_statistical_models.ipynb
│   └── 04_machine_learning.ipynb
├── scripts/                      # standalone scripts for key steps
│   ├── eda.py
│   ├── logistic_regression.py
│   └── random_forest.py
├── figures/                      # generated plots and visualizations
├── README.md                     # project overview and instructions
└── requirements.txt              # Python package dependencies
```

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/your_username/heart-disease-risk-analysis.git
   cd heart-disease-risk-analysis
   ```
2. Create a conda environment and install dependencies:
   ```bash
   conda create -n heart-env python=3.9
   conda activate heart-env
   pip install -r requirements.txt
   ```

## Usage

- **Data Cleaning**:
  ```bash
  jupyter notebook notebooks/01_data_processing.ipynb
  ```
- **Exploratory Data Analysis**:
  ```bash
  jupyter notebook notebooks/02_exploratory_analysis.ipynb
  ```
- **Statistical Modeling** (logistic & Poisson regressions):
  ```bash
  jupyter notebook notebooks/03_statistical_models.ipynb
  ```
- **Machine Learning** (random forest, hyperparameter tuning):
  ```bash
  jupyter notebook notebooks/04_machine_learning.ipynb
  ```

## Key Findings

- **Physical Health**: Days of poor physical health strongly discriminate heart disease status, especially among diabetics (Δmean ≈ +4–6 days).
- **Mental Health**: Generally weaker as a predictor, with notable separation only in pregnant diabetics.
- **Diabetes Effect**: Diabetic individuals have \~1.8× higher odds of heart disease, controlling for age, BMI, smoking, activity, and general health.
- **Model Performance**:
  - Logistic regression AUC ≈ 0.82
  - Random forest AUC ≈ 0.83; precision can be tuned via threshold and hyperparameter search.

-> Note: Several analysis we relocated to the Ad Nauseam section to preserve the project's brevity.

## Ethics & Bias Considerations

We acknowledge potential sampling bias (exclusion of non‑respondents or underrepresented groups), self‑report error in health days, and limitations in generalizing to non‑U.S. populations. We commit to:

- Evaluating fairness across age, sex, and race subgroups via stratified analyses.
- Flagging influential observations and ensuring robust inference.
- Respecting data privacy; no individual identifiers are used.

## Next Steps

- **Interaction & Mediation**: Test `DiabeticFlag × GenHealth` and `DiabeticFlag × PhysicalHealth` to confirm uniform effects.
- **Sensitivity Analyses**: Stratify by age/race and run propensity‐score matching to mitigate confounding.
- **Deployment**: Package the best predictive model into an API for clinical decision support.

## License

This project is released under the MIT License.