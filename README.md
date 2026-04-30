# 👥 Predicting Employee Attrition
**Academic project-DAT 430 | Southern New Hampshire University(2025)**

> *When people leave, organizations lose more than headcount. This project asks: can we see it coming?*

---

## The Problem

A fictional company — La Banca Central Bank's HR division — needed to understand which employees were most at risk of leaving. Reactive hiring is expensive. The goal was to build a predictive model that could flag at-risk employees early enough to act on it.

Sound familiar? Replace "employees" with "students" or "teachers" and this is one of the most pressing problems in education.

---

## What I Built

A two-part ML pipeline that escalates from a simple baseline to tuned ensemble models, with results visualized in an interactive Power BI dashboard.

**Tools used:** Python (pandas, scikit-learn), Power BI, Jupyter Notebook

---

## Part 1 — Baseline Logistic Regression

Starting simple on purpose. Before throwing complex models at a problem, it's worth knowing what a basic model can and can't do.

- Engineered a `high_income` binary feature from monthly salary data
- Built a logistic regression classifier using income and manager tenure as predictors
- Evaluated accuracy, precision, and recall on both full dataset and high-income subgroup

**Result:** ~70% overall accuracy but weak recall — the model missed too many actual attrition cases. Income and tenure alone aren't enough. More features needed.

📓 [`baseline_logistic_regression.ipynb`](baseline_logistic_regression.ipynb)

---

## Part 2 — Random Forest vs AdaBoost

Armed with the baseline's limitations, Part 2 expands the feature set and escalates to ensemble methods.

- Added engineered features: `high_income`, `tenured` (years at company ≥ 11)
- One-hot encoded categorical variables: Gender, JobRole, Department, MaritalStatus
- Tuned both models using **GridSearchCV** with 5-fold cross-validation, optimizing for **recall** — because missing an at-risk employee is costlier than a false alarm
- Compared Random Forest vs AdaBoost performance side by side

**Result:** Random Forest edged out AdaBoost on overall correct predictions. Both models showed the dataset's class imbalance challenge — attrition is rare, which makes recall-focused tuning essential.

📓 [`employee_attrition_analysis.ipynb`](employee_attrition_analysis.ipynb)

---

## Power BI Dashboard

Model outputs were exported to CSV and visualized in an interactive Power BI dashboard featuring:

- **Correct Predictions by Model** — RF vs AdaBoost side-by-side comparison
- **Actual Attrition vs AdaBoost Predictions** — breakdown by actual outcome
- **Interactive filters** — slice by JobSatisfaction, tenure status, YearsAtCompany, and TotalWorkingYears

🖼️ [`assets/dashboard_full.png`](assets/dashboard_full.png) *(screenshots — Power BI file not included)*

---

## Why Recall Over Accuracy?

This is worth calling out explicitly. In attrition prediction, a false negative — predicting someone stays when they're about to leave — is more costly than a false positive. GridSearchCV was configured with `scoring='recall'` for exactly this reason. Choosing the right metric is part of the analysis.

---

## Repo Structure

```
employee-attrition-analysis/
├── README.md
├── baseline_logistic_regression.ipynb
├── employee_attrition_analysis.ipynb
├── predictions_train.csv
├── predictions_test.csv
├── HRData1.csv
├── HRData2.csv
└── assets/
    ├── dashboard_full.png
    ├── dashboard_visuals_1_2.png
    ├── visual_model_accuracy.png
    ├── visual_attrition_breakdown.png
    ├── attrition_by_satisfaction.png
    ├── confusion_matrix_Random_Forest.png
    ├── confusion_matrix_AdaBoost.png
    ├── Feature_Importance.png
    ├── Full_visual_dashboard_with_title.png
    ├── Model_comparison_FR_AdaBoost.png
    └── visual_filters.png
```

---

## About Me
📎 [Portfolio](https://glitchwitchkitty.github.io/chaosgremlinhq-portfolio/) | [GitHub](https://github.com/glitchwitchkitty)
