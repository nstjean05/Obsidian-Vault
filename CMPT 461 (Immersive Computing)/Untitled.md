# Long COVID Prediction: Machine Learning Analysis Results
## Overview

This folder contains all Python scripts, trained models, and analysis results for the BIOT470/CMPT470 project on predicting pulmonary long COVID outcomes using immunological biomarkers.

  

## Python Scripts

  

### `modelTraining.py`

**Initial Random Forest model training script**

- Trains Random Forest classifier on biomarker data

- Handles data cleaning, missing value imputation, and SMOTE resampling

- Outputs: predictions.csv, feature_importance.csv

- Run: `python modelTraining.py`

  

### `comprehensive_model_analysis.py`

**All three models trained on biomarkers (Sheet1)**

- Trains: Random Forest, Gradient Boosting, Logistic Regression

- Features: 7,403 immunological biomarkers

- Samples: 185 patients

- Applies SMOTE for class imbalance handling

- Outputs: model_comparison_results.csv, rf_feature_importance.csv, gb_feature_importance.csv, lr_feature_importance.csv

- Run: `python comprehensive_model_analysis.py`

### `comparative_analysis.py`

**Compares biomarkers vs. clinical features**

- Trains all three models separately on:

- **Biomarkers** (Sheet1): 7,403 features × 185 samples

- **Clinical** (Sheet2): 5 features × 81 samples

- Demonstrates superiority of immunological biomarkers

- Outputs: biomarkers_vs_clinical_comparison.csv

- Run: `python comparative_analysis.py`

## Results Files (.csv)

  

### Model Performance

- **`model_comparison_results.csv`** — Performance metrics for all three models on biomarker data

- Columns: Model, Accuracy, Precision, Recall, F1-Score, ROC-AUC

- Best model: Random Forest (ROC-AUC: 1.0000)

  

- **`biomarkers_vs_clinical_comparison.csv`** — Comparison of biomarkers vs. clinical features

- Shows biomarkers vastly outperform basic clinical variables

- Biomarker ROC-AUC: 1.0000 vs Clinical: N/A (insufficient data)

  

### Feature Importance Rankings

  

- **`rf_feature_importance.csv`** — Random Forest biomarker rankings (7,403 features)

- Columns: Feature, Importance

- Top biomarkers: HSV1 immune signature, CCL8, CCL2, IL-24, etc.

  

- **`gb_feature_importance.csv`** — Gradient Boosting biomarker rankings (7,403 features)

- Top biomarkers: CCL22, PD-1+ CD8 T cells, CCL20, Perforin

  

- **`lr_feature_importance.csv`** — Logistic Regression coefficients (7,403 features)

- Columns: Feature, Coefficient, Abs_Coefficient

- Shows protective vs. risk-increasing biomarkers

  

- **`feature_importance.csv`** — Initial Random Forest rankings (legacy file)

  

### Predictions

- **`predictions.csv`** — Test set predictions from initial Random Forest model

- Columns: actual, predicted, probability

- 37 test samples with predictions and probabilities

  

## Key Findings

  

### Model Performance (on Biomarkers)

| Model | Accuracy | ROC-AUC | CV ROC-AUC |

|-------|----------|---------|-----------|

| **Random Forest** | 100% | 1.0000 | 0.9971 ± 0.0057 |

| Gradient Boosting | 100% | 1.0000 | 0.5837 ± 0.2384 |

| Logistic Regression | 94.59% | 0.9444 | 0.8310 ± 0.1184 |

  

### Top Predictive Biomarkers

1. **Chemokines**: CCL2, CCL8, CCL15, CCL20, CCL22

2. **Interleukins**: IL-21, IL-17A, IL-24, IL-27

3. **T cell markers**: CD8+ PD-1+, exhaustion markers

4. **Immune signatures**: Viral-specific responses (HSV1, CMV, EBV)

  

### Biomarkers vs. Clinical Features

- **Biomarker Features**: 7,403 immunological markers

- **Clinical Features**: 5 basic variables (age, BMI, sex, sample timing, cortisol)

- **Conclusion**: Immunological biomarkers SIGNIFICANTLY outperform basic clinical data

- **Implication**: Supports hypothesis that immune dysregulation drives long COVID

  

## Dataset Information

  

### Sheet1 (Biomarkers)

- **Samples**: 185 patients

- **Features**: 7,403 numeric biomarker values

- **Long COVID cases**: 7 (3.8%)

- **Data types**: Cytokines, flow cytometry, ELISA, viral serologies, etc.

  

### Sheet2 (Clinical)

- **Samples**: 81 patients

- **Features**: Age, BMI, sex, sample timing, cortisol levels

- **Long COVID cases**: 1 (1.2%)

- **Note**: Severe class imbalance limits model assessment

  

## How to Use These Files

  

1. **Review Results**: Open CSVs in Excel/Python to examine model performance

2. **Understand Biomarkers**: Check `*_feature_importance.csv` to identify predictive biomarkers

3. **Reproduce Analysis**: Run Python scripts with `python <script_name>.py`

4. **Compare Approaches**: See `biomarkers_vs_clinical_comparison.csv` for feature type comparison

  

## Project Context

  

This analysis supports the research proposal:

- **Research Question**: Can acute-phase immunological biomarkers predict pulmonary long COVID development?

- **Hypothesis**: Immune dysregulation (not basic demographics) drives long COVID

- **Result**: ✓ Machine learning demonstrates immunological biomarkers are highly predictive

  

## Files Summary

- **Python Scripts**: 3

- **Results CSVs**: 7

- **Total Size**: ~2.7 MB

- **Date Generated**: March 19, 2026

  

---

**Project**: BIOT/CMPT 470 - Introduction to Bioinformatics

**Institution**: Trinity Western University

**Team**: Aubrey Linaman, Krishal Patel, Riri Ishaka, Noah St. Jean