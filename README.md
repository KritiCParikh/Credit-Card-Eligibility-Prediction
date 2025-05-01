# Credit Card Eligibility Prediction

A machine learning project aimed at automating credit card eligibility decisions using applicants' demographic, financial, and employment data. Completed as a 120-minute challenge to build a base model, with plans for further tuning.

---

## Problem Statement

Global Bank currently reviews applicants’ credit histories manually to determine credit card eligibility. To streamline this process, we developed a machine learning pipeline that predicts eligibility using structured applicant data.

---

## Dataset Overview

Files:
- `train.csv`: Labeled data for model training
- `test.csv`: Unlabeled data for prediction
- `sample_output.csv`: Expected format for submission

### Target Variable
- `Eligibility`: 
  - `1` = Eligible
  - `0` = Not Eligible

### Key Features
| Feature               | Description                                      |
|-----------------------|--------------------------------------------------|
| Age                  | Applicant's age                                   |
| Sex                  | Gender (M/F)                                      |
| Marital Status       | Single, Married, Divorced, Widow, Other           |
| Dependents           | Number of dependents                              |
| Education            | Education level                                   |
| Monthly Salary       | Income in dollars                                 |
| Residence/Working Since | Time spent in current home/job (months)       |
| Existing Credit Card | Whether applicant has another card (0/1)          |
| Avg Account Balance  | Average bank account balance                      |

---

## Data Preprocessing

- **Missing Values** handled using:
  - `mode()` for categorical columns
  - `median()` for numerical columns
- **Special Cleaning**:
  - Parsed ranges in `Dependents` (e.g., `(4.0, 6.0]` → `5.0`)
- **Encoding**:
  - Applied `LabelEncoder` to all categorical features

---

## ⚙Model: Random Forest Classifier

> Chosen for its robustness, interpretability, and ability to handle mixed feature types with minimal tuning and time constraints.

- Achieved **91.4% accuracy** on the validation set
- Used `train_test_split` (80/20)
- Evaluated with `accuracy_score` and `classification_report`
- Visualized top 20 important features via feature importance plot

---

## Feature Importance

!![Feature Importance](https://github.com/KritiCParikh/credit-card-eligibility/blob/main/important_features.png)
*Top 20 features influencing credit eligibility*

--

## Insights from Feature Importance

| Rank | Feature(s)                                 | Insight                                                                 |
|------|---------------------------------------------|-------------------------------------------------------------------------|
| 1   | **Number of Bank Accounts**                | Most influential — likely reflects financial stability and experience   |
| 2   | **Dependents**                             | High number might signal higher expense load, reducing eligibility      |
| 3   | **Education**                              | Higher education often correlates with stable income and low risk       |
| 4   | **Employment Industry**                    | Industry type affects income predictability and job stability           |
| 5   | **Avg Account Balance**                    | Higher balances imply better money management                           |
| 6–10 | **Age, Monthly Salary, Residing/Working Since** | Stability factors — tenure and income consistency add trust       |
| ↓    | **Least Impactful:** Insurance Status, Card Type, Existing Credit Card | Likely binary or less varied in influence |

---

## Future Enhancements

- Try **XGBoost** or **LightGBM** for improved performance
- Add **SHAP** or **LIME** for model explainability
- Implement **tiered product recommendation** or **risk-based flagging**
- Deploy the model with a simple Streamlit app for business use

---

## Tech Stack

- Python 3
- pandas, numpy, matplotlib, seaborn
- scikit-learn
- Jupyter Notebook

----

Thank You. Let’s keep learning and growing together!
