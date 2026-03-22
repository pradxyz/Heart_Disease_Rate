# Heart Disease Risk Prediction

This project investigates whether machine learning models can accurately predict heart disease using structured clinical data. Using the Cleveland Heart Disease dataset, multiple classification algorithms were evaluated and compared, with a focus on identifying the most clinically relevant features influencing prediction.

## Why I built this

Heart disease is one of the leading causes of mortality worldwide. Early and accurate prediction using clinical data can assist in timely diagnosis. This project was an attempt to understand what clinical features matter most and how well standard ML models perform on this kind of health data.

## Dataset

**Cleveland Heart Disease Dataset** (via Kaggle)
- 303 patient records
- 13 clinical features including age, sex, chest pain type, cholesterol, resting blood pressure, maximum heart rate, and more
- Target variable: `condition` (0 = no disease, 1 = disease)

## What I did

### 1. Exploratory Data Analysis
- Checked for missing values (none found)
- Plotted age distribution across the dataset
- Compared cholesterol and maximum heart rate between patients with and without heart disease using boxplots
- Generated a correlation heatmap to understand feature relationships

### 2. Baseline Model Comparison

Trained three classifiers on all 13 features:

| Model | Accuracy |
|---|---|
| Logistic Regression | 73.3% |
| Decision Tree | 71.6% |
| Random Forest | 73.3% |

### 3. Feature Selection

Applied **SelectKBest with chi-squared test** to identify the 8 most clinically significant features:

`sex, cp, restecg, exang, oldpeak, slope, ca, thal`

### 4. Improved Model Performance

Retrained the same models on selected features:

| Model | Before | After |
|---|---|---|
| Logistic Regression | 73.3% | 78.3% |
| Decision Tree | 71.6% | 73.3% |
| Random Forest | 73.3% | **81.6%** |

### 5. Final Evaluation

Evaluated the best model (Random Forest) using:
- Confusion Matrix
- Classification Report (Precision, Recall, F1-Score)

**Final Results:**
- Accuracy: 81.6%
- Precision: 0.84 (no disease), 0.79 (disease)
- Recall: 0.81 (no disease), 0.82 (disease)

## Key Findings

**From Exploratory Data Analysis:**
- Patients without heart disease had noticeably higher maximum heart rate compared to those with disease — suggesting cardiovascular fitness plays a protective role
- Cholesterol levels were surprisingly similar between both groups — not as strong a predictor as commonly assumed
- Heart disease cases were concentrated in patients in their 60s

**From Feature Selection:**
- Chi-squared test identified 8 most significant features: chest pain type, thalassemia, number of major vessels, ST depression, slope, exercise induced angina, sex, and resting ECG
- Age, cholesterol, and resting blood pressure were dropped — statistically less predictive in this dataset
- This is clinically interesting as it challenges the assumption that cholesterol alone is the primary heart disease indicator

**From Model Results:**
- Feature selection improved Random Forest accuracy from 73.3% to 81.6%
- Decision Tree was least affected by feature selection — consistent with its nature of doing internal feature selection
- Random Forest was the best overall performer with 82% accuracy, 0.84 precision and 0.82 recall

## Tech Stack

- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn

## Future Work

- Hyperparameter tuning (GridSearchCV)
- Cross-validation for more robust evaluation
- Exploring additional ensemble methods (XGBoost, GradientBoosting)
- SHAP values for better model interpretability

---

## Author

**Pradyumna**
B.Tech Computer Science and Engineering
