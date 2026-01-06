# Framingham Heart Study: 10-Year CHD Risk Prediction

This project predicts the 10-year risk of Coronary Heart Disease (CHD) using the Framingham Heart Study dataset.  
It demonstrates data cleaning, exploratory data analysis (EDA), modelling with multiple algorithms, evaluation, and feature importance analysis using Random Forest and SHAP.

## Project Structure

```
framingham-heart-risk/
│
├── framingham.csv
├── framingham_risk_analysis.ipynb
├── outputs/
├── plots/
└── README.md
```

## Steps Included

1. **Load and Inspect Data**  
   - Load CSV dataset into a DataFrame  
   - Examine shape, columns, and missing values  

2. **Data Cleaning**  
   - Convert categorical variables to proper types  
   - Fill missing numerical values with medians  
   - Handle missing BPMeds values  

3. **Exploratory Data Analysis (EDA)**  
   - Visualize target distribution  
   - Compute correlation heatmap  
   - Plot histograms for key features  

4. **Feature Preparation**  
   - Encode categorical features as numeric codes  
   - Define target variable  

5. **Train/Test Split and Scaling**  
   - Split data into training (80%) and testing (20%) sets  
   - Standardize features  

6. **Modelling**  
   - Logistic Regression  
   - Random Forest Classifier  
   - XGBoost Classifier  

7. **Model Evaluation**  
   - Accuracy, ROC-AUC, confusion matrix  
   - Classification reports  
   - ROC curves  
   - Model comparison table  

8. **Feature Importance and SHAP Analysis**  
   - Random Forest feature importance  
   - SHAP summary plots  

## Results

### Model Performance

| Model                  | Accuracy  | ROC-AUC  |
|------------------------|-----------|----------|
| Logistic Regression    | 0.844     | 0.702    |
| Random Forest          | 0.846     | 0.642    |
| XGBoost                | 0.822     | 0.605    |

### Feature Importance (Random Forest)

| Feature   | Importance |
|-----------|------------|
| sysBP     | 0.135      |
| BMI       | 0.128      |
| age       | 0.126      |
| totChol   | 0.121      |
| glucose   | 0.116      |

### Target Distribution

| TenYearCHD | Count |
|------------|-------|
| 0          | 3596  |
| 1          | 644   |

**Insights**  
- Systolic blood pressure (sysBP), BMI, age, total cholesterol, and glucose are the most important predictors for 10-year CHD risk.  
- Logistic Regression slightly outperforms other models in ROC-AUC, while Random Forest has the highest accuracy.  
- The dataset is imbalanced with ~15% of patients experiencing CHD within 10 years.

## Requirements

- Python 3.x  
- pandas  
- numpy  
- matplotlib  
- seaborn  
- scikit-learn  
- xgboost  
- shap  

Install packages via pip:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost shap
```

## Author

Uche Dumzo-Ajufo
MSc Data Science | BEng Biomedical Engineering (Hons)
