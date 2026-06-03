
About
This project builds a predictive model to classify whether a forest is at risk of fire, based on environmental and ecological features. The project was completed as a formally assessed university assignment (ITNPBD6) and follows the CRISP-DM (Cross-Industry Standard Process for Data Mining) methodology end-to-end.
Four classification models were developed, tuned, and evaluated — Logistic Regression, Decision Tree, Random Forest, and Neural Network (MLP) — with Logistic Regression selected as the final model based on its balanced performance across all evaluation metrics.
A research poster summarising the methodology and findings was produced as part of the assessment.

Research Question

Which environmental and ecological variables are the strongest predictors of forest fire occurrence, and which classification model best balances recall and precision for real-world fire prevention?


Dataset

File: forestdata.csv
Target variable: fire (binary: 0 = No Fire, 1 = Fire)
Key features:

FeatureTypeDescriptionc.scoreContinuousCarbohydrate score — influences fuel qualityl.scoreContinuousLeaf litter score — indicates fire spread potentialrainContinuousRainfall leveltree.ageContinuousAge of treessurface.litterContinuousSurface litter coveragewind.intensityContinuousWind speedhumidityContinuousHumidity leveltree.densityContinuousDensity of treesmonthCategoricalMonth of observationtime.of.dayCategoricalTime of day

Methodology — CRISP-DM
1. Business Understanding
Develop a predictive model to assist forest management commissions in identifying forests at risk of fire, supporting proactive prevention strategies.
2. Data Understanding

Explored data types, distributions, and correlations
Plotted histograms and box plots for all numerical features
Checked class balance of the target variable

3. Data Preparation

Missing value imputation — median imputation for: l.score, rain, tree.age, wind.intensity, humidity
Outlier handling — clipping applied
Normalisation — numerical features normalised
One-hot encoding — applied to month and time.of.day
Feature selection — collector.id removed (non-predictive)
Class imbalance — addressed using SMOTE (Synthetic Minority Over-sampling Technique)
Train/Validation/Test split — 60% / 20% / 20%

4. Modelling & Hyperparameter Tuning
All models were tuned using GridSearchCV and RandomizedSearchCV with cross-validation, optimising for Recall and F1 Score to minimise false negatives (missed fire predictions).
ModelValidation RecallValidation PrecisionValidation F1Validation AccuracyLogistic Regression0.9540.9330.9430.945Decision Tree0.9310.9310.9310.934Random Forest0.9770.9550.9660.967Neural Network (MLP)0.9310.9530.9420.945
5. Final Model — Logistic Regression
Logistic Regression was selected as the final model due to its:

Interpretability — coefficients are directly explainable
Balanced performance — strong across recall, precision, F1, and accuracy
Simplicity — lower computational cost vs. Random Forest and Neural Network
Reliability — consistent results across cross-validation folds

Final test set performance:
MetricScoreRecall0.89Precision0.91Accuracy0.92F1 Score0.90
Confusion Matrix (Test Set):

True Negatives: 53 (correctly predicted No Fire)
True Positives: 32 (correctly predicted Fire)
False Positives: 3 (predicted Fire incorrectly)
False Negatives: 4 (missed actual fires — minimised by optimising for recall)


Repository Structure
├── forest_fire.ipynb       # Main notebook — EDA, data preparation, baseline models
├── LR_Main.ipynb           # Logistic Regression — full pipeline + hyperparameter tuning
├── DT_Main.ipynb           # Decision Tree — full pipeline + hyperparameter tuning
├── RF_Main.ipynb           # Random Forest — full pipeline + hyperparameter tuning
├── MLP_Main.ipynb          # Neural Network (MLP) — full pipeline + hyperparameter tuning
├── 3309061_ITNPBD6.pdf     # Research poster — methodology and results summary
└── README.md

Technologies Used

Python — pandas, numpy, matplotlib, seaborn
Machine Learning — scikit-learn (Logistic Regression, Decision Tree, Random Forest, MLP)
Imbalanced Data — imbalanced-learn (SMOTE)
Hyperparameter Tuning — GridSearchCV, RandomizedSearchCV
Methodology — CRISP-DM


Relevance to Environmental Research
This project applies machine learning classification to an environmental risk prediction problem — directly relevant to sustainability, ecological management, and the broader study of how data-driven methods can inform environmental policy. The focus on minimising false negatives (missed fire predictions) reflects the real-world stakes of environmental decision-making, a theme central to research on green innovation and climate policy impact.

Assessment Output
A formal research poster was produced summarising the project methodology, variable treatment, model comparison, hyperparameter tuning strategy, final model selection rationale, and confusion matrix results. This is included in the repository as 3309061_ITNPBD6.pdf.

Author
Clare Onyewuchi
MSc Data Science for Business (Distinction), University of Stirling
linkedin.com/in/clare-onyewuchi | github.com/Clare-Onyewuchi
