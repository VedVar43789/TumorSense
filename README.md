# Tumor Sense

Tumor Sense is an end-to-end SVM classification pipeline built on the Wisconsin Breast Cancer Diagnostic dataset. It reduces 30 raw cell nucleus measurements down to the 10 most predictive features and achieves high discriminatory performance providing a reliable, data-driven second opinion for ambiguous fine needle aspiration (FNA) cases.

---

## Results at a Glance

| Metric | Score |
|---|---|
| Malignant Recall | **98%** |
| Malignant Precision | **98%** |
| ROC-AUC | **0.995** |

A false negative (calling a malignant tumor benign) is a life-threatening error. The model was evaluated with this asymmetry in mind.

---

## Methodology

### 1. Data Preprocessing
- Dataset: [UCI Wisconsin Breast Cancer Diagnostic Dataset](https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+(Diagnostic)) (569 samples, 30 features)
- Stratified train-test split to preserve class balance across both sets

### 2. Feature Selection
- Applied **Recursive Feature Elimination (RFE)** with a `LinearSVC` estimator
- Reduced 30 raw features → **top 10 most predictive features**

### 3. Model Training
- **Algorithm:** Support Vector Machine with RBF kernel
- **Hyperparameter tuning:** `GridSearchCV` over `C` and `gamma`
- Best parameters selected via cross-validated grid search

### 4. Evaluation
- Precision, Recall, F1 per class
- ROC-AUC score
- SHAP summary plot for model explainability

---

## Tech Stack

![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=flat&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-2.0-150458?style=flat&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-1.26-013243?style=flat&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.8-11557C?style=flat)
![SHAP](https://img.shields.io/badge/SHAP-explainability-FF6B6B?style=flat)

---

## Repository Structure

```
tumor-sense/
├── data/
│   └── wdbc.csv                  # Wisconsin Diagnostic Breast Cancer dataset
├── notebook/
│   └── tumor_sense.ipynb         # Full analysis and model pipeline
├── models/
│   └── svm_model.pkl             # Serialized trained model
├── visuals/
│   ├── shap_summary.png          # SHAP feature importance plot
│   └── roc_curve.png             # ROC-AUC curve
└── README.md
```

---

## 🚀 Getting Started

```bash
# Clone the repo
git clone https://github.com/nathaniel-trueba/tumor-sense.git
cd tumor-sense

# Install dependencies
pip install -r requirements.txt

# Launch the notebook
jupyter notebook notebook/tumor_sense.ipynb
```

---

## Authors

- **Vedant Vardhaan** - Mentor
- **Nathaniel Trueba** - Group Member
- **Kavya Shah** - Group Member
- **Evan Park** - Group Member
- **Steven Ngo** - Group Member

---

## ⚠️ Disclaimer

Tumor Sense is an academic project and is **not intended for clinical use**. All results are derived from a publicly available research dataset and should not be used to inform medical decisions.
