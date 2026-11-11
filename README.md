# Framingham Heart Study: 10-Year CHD Risk Prediction

This project predicts the 10-year risk of Coronary Heart Disease (CHD) using the Framingham Heart Study dataset.

The analysis covers data preprocessing, exploratory data analysis (EDA), machine learning model development, performance evaluation, and model interpretability using Random Forest feature importance and SHAP (SHapley Additive exPlanations).

## Project Structure

```text
framingham-heart-risk/
│
├── 01_data/
│   └── framingham.csv
│
├── 02_notebooks/
│   └── 01_framingham_risk_analysis.ipynb
│
├── 03_plots/
│   └── [generated visualisations]
│
├── 04_outputs/
│   └── [model evaluation results]
│
├── README.md
├── requirements.txt
└── .gitignore
```

### Directory Overview

| Directory / File | Description |
|------------------|-------------|
| `01_data/` | Contains the Framingham Heart Study dataset. |
| `02_notebooks/` | Jupyter notebook containing the complete machine learning workflow. |
| `03_plots/` | Visualisations generated during EDA, model evaluation and feature importance analysis. |
| `04_outputs/` | Model evaluation results and other generated outputs. |
| `README.md` | Project documentation, methodology and results. |

## Methodology

### 1. Data Loading and Inspection
- Load the Framingham Heart Study dataset using pandas.
- Examine dataset dimensions, features and data types.
- Identify missing values and assess data quality.

### 2. Data Cleaning and Preprocessing
- Convert categorical variables into appropriate data types.
- Impute missing numerical values using median values.
- Handle missing values in the `BPMeds` feature.

### 3. Exploratory Data Analysis (EDA)
- Visualise the distribution of the target variable (`TenYearCHD`).
- Examine correlations between numerical features.
- Generate histograms to explore feature distributions.

### 4. Feature Preparation
- Encode categorical variables into numerical representations.
- Separate predictor variables from the target variable.
- Prepare the dataset for machine learning.

### 5. Train-Test Split and Feature Scaling
- Split the dataset into training (80%) and testing (20%) subsets.
- Standardise numerical features for model training.

### 6. Machine Learning Models
Train and compare three classification algorithms:

- **Logistic Regression:** A linear classification model used as a baseline.
- **Random Forest Classifier:** An ensemble learning algorithm combining multiple decision trees.
- **XGBoost Classifier:** A gradient boosting algorithm designed for predictive modelling.

### 7. Model Evaluation
Evaluate predictive performance using:

- Accuracy
- ROC-AUC score
- Confusion matrices
- Classification reports
- ROC curves
- Model comparison tables

### 8. Feature Importance and Explainability
- Calculate feature importance using Random Forest.
- Apply SHAP to examine feature contributions to model predictions.
- Identify influential predictors of 10-year CHD risk.

## Results

### Model Performance

| Model | Accuracy | ROC-AUC |
|-------|----------|---------|
| Logistic Regression | 0.844 | **0.702** |
| Random Forest | **0.846** | 0.642 |
| XGBoost | 0.822 | 0.605 |

Logistic Regression achieved the highest ROC-AUC score (0.702), indicating the strongest overall ability to distinguish between patients with and without CHD among the evaluated models.

Random Forest achieved the highest accuracy (84.6%), although accuracy alone provides a limited assessment due to class imbalance.

### Feature Importance (Random Forest)

| Feature | Importance |
|---------|------------|
| Systolic Blood Pressure (`sysBP`) | 0.135 |
| Body Mass Index (`BMI`) | 0.128 |
| Age (`age`) | 0.126 |
| Total Cholesterol (`totChol`) | 0.121 |
| Glucose (`glucose`) | 0.116 |

Systolic blood pressure, BMI, age, total cholesterol and glucose emerged as the five most influential predictors according to Random Forest feature importance.

These importance values describe model behaviour rather than causal relationships.

### Target Distribution

| TenYearCHD | Count | Percentage |
|------------|-------|------------|
| 0 (No CHD) | 3,596 | 84.8% |
| 1 (CHD) | 644 | 15.2% |
| **Total** | **4,240** | **100%** |

The dataset exhibits substantial class imbalance, with approximately 15% of patients experiencing CHD within 10 years.

### Key Findings

- Logistic Regression achieved the highest ROC-AUC score of 0.702.
- Random Forest produced the highest classification accuracy of 84.6%.
- Systolic blood pressure, BMI, age, total cholesterol and glucose ranked highest in Random Forest feature importance.
- Class imbalance presents a challenge for predicting the minority CHD-positive class.
- Further improvements could focus on class imbalance handling, hyperparameter optimisation and additional evaluation metrics such as recall, precision and PR-AUC.

## Installation and Usage

### 1. Clone the Repository

```bash
git clone https://github.com/uche1207/framingham-heart-risk.git
cd framingham-heart-risk
```

### 2. Create a Virtual Environment

```bash
python -m venv .venv
```

Activate the environment.

**Windows:**

```bash
.venv\Scripts\activate
```

**macOS / Linux:**

```bash
source .venv/bin/activate
```

### 3. Install Dependencies

Install the required Python libraries:

```bash
pip install -r requirements.txt
```

The main dependencies are:

- Python 3.x
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- xgboost
- shap

Jupyter Notebook is also required to run the analysis interactively.

### 4. Run the Analysis

Launch Jupyter Notebook from the repository root:

```bash
jupyter notebook
```

Open:

```text
02_notebooks/01_framingham_risk_analysis.ipynb
```

Execute the notebook cells sequentially to reproduce the data preprocessing, exploratory analysis, model training and evaluation.

**Note:** The notebook must use paths consistent with the new directory structure. When using root-relative paths, launch Jupyter from the repository root.

## Limitations

- **Class imbalance:** Only 15.2% of observations belong to the positive CHD class, potentially affecting minority-class prediction.
- **Moderate discrimination:** The highest ROC-AUC score of 0.702 indicates room for improvement.
- **Generalisation:** Performance on the available test set does not establish reliability across different populations or healthcare settings.
- **Clinical applicability:** The models require additional validation, calibration assessment and clinical evaluation before consideration for real-world healthcare use.

This project is intended for educational and research purposes only. The predictions should not be used for clinical diagnosis or medical decision-making.

## Author

**Uche Dumzo-Ajufo**

MSc Data Science | BEng Biomedical Engineering (Hons)

[GitHub](https://github.com/uche1207)