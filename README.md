# Project Title

Machine Learning for FAERS Safety Signal Classification

## Project Goal

The goal of this project is to build a machine learning model to classify adverse event reports from the FAERS (FDA Adverse Event Reporting System) database into serious vs non-serious cases.

This task is clinically important because identifying serious adverse events early can support pharmacovigilance, patient safety monitoring, and regulatory decision-making.

## Target Variable

- Target: Serious
- Type: Binary classification
- 0 = Non-serious
- 1 = Serious

The target variable was encoded into numeric format for machine learning modeling.

## Methods

### Data Preprocessing

- Missing values handled:
- Text fields filled with empty string
- Numeric fields (age, weight) filled with median
- Categorical variables encoded using one-hot encoding
- All structured features converted to numeric format

### Feature Engineering

Two types of features were used:

#### Structured Features

- Patient Age
- Patient Weight
- Sex
- Case Priority
- Reporter Type
- Report Source

#### Text Features

- Reactions column
- Processed using TF-IDF vectorization (max_features=500)
- Structured and text features were combined into a single feature matrix using sparse representation.

### Models

Two machine learning models were trained:

- Logistic Regression (baseline, interpretable)
- Random Forest (nonlinear, ensemble-based)

## Evaluation Metrics

Models were evaluated using:

- Accuracy
- Precision, Recall, F1-score
- ROC-AUC (overall discrimination)
- PR-AUC (important for class imbalance)

## Results
**Logistic Regression**

- Accuracy: ~0.90
- ROC-AUC: ~0.962
- PR-AUC: ~0.979

**Random Forest**

- Accuracy: ~0.90
- ROC-AUC: ~0.963
- PR-AUC: ~0.978

## Visual Evaluation
**ROC Curve**

- Both models show strong discrimination
- Performance is very similar between models

**Precision-Recall Curve**

- High precision maintained across most recall levels
- Indicates strong performance in identifying serious cases

**Calibration Curve**

- Logistic Regression shows slightly better calibration
- Random Forest tends to be slightly overconfident

## Interpretation

- Both models achieved strong performance in distinguishing serious vs non-serious adverse events.
- High ROC-AUC indicates excellent ability to separate classes.
- High PR-AUC confirms strong performance on the positive class (serious cases), which is critical in safety analysis.

## Clinical Insight

- In pharmacovigilance, correctly identifying serious adverse events is more important than overall accuracy.
- Precision reflects false positive risk (unnecessary alerts)
- Recall reflects missed safety signals
- Calibration Importance
- Calibration is especially important in healthcare applications because predicted probabilities may influence clinical or regulatory decisions.
- A well-calibrated model ensures that predicted risk reflects true observed risk.

## Conclusion

- Machine learning models can effectively classify FAERS reports
- Combining structured data with text features improves performance
- Logistic Regression provides strong and well-calibrated baseline performance
- Random Forest offers comparable performance with slightly different behavior

## Future Work

- Threshold tuning for clinical decision-making
- Model calibration improvement (Platt scaling / isotonic regression)
- Drug-specific safety signal analysis
- Time-series analysis of adverse event reporting
