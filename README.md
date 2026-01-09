# 🏋️‍♂️ Body Fat Prediction Project

This project applies advanced Data Science techniques to predict body fat percentage using anthropometric measurements. The primary focus was on building a statistically sound linear regression model by addressing real-world data issues such as noise, missing values, and multicollinearity.



---

## 🎯 Objective
To develop a reliable predictive model using only simple measurements (attained with a tape measure and scale), allowing for an accurate estimate without the need for complex exams like hydrostatic weighing.

---

## 🛠️ Technologies and Tools
* **Language:** Python 3.x
* **Data Processing:** `Pandas`, `Numpy`
* **Data Cleaning:** `Re` (Regular Expressions)
* **Statistical Modeling:** `Statsmodels` (OLS Regression, VIF)
* **Machine Learning:** `Scikit-Learn` (`KNNImputer`, `StandardScaler`)
* **Visualization:** `Seaborn`, `Matplotlib`

---

## 📈 Methodology and Technical Decisions

### 1. Data Cleaning
The raw data contained inconsistencies such as commas instead of dots and special characters. A **Regex-based** cleaning process was implemented to normalize numerical columns, ensuring mathematical integrity.

### 2. Intelligent Imputation (KNN Imputer)
To avoid losing valuable data, missing values were filled using the **KNN (K-Nearest Neighbors)** algorithm. 
> **Technical Note:** Before imputation, the data was normalized using `StandardScaler` to ensure that the KNN's Euclidean distance was not distorted by the different scales of the variables.

### 3. Feature Selection
The selection strategy was based on two statistical pillars:
* **VIF (Variance Inflation Factor):** We identified and removed the `Weight` variable, which showed high redundancy (VIF > 20) with other circumference measurements.
* **Backward Elimination (P-value):** We refined the model by removing non-significant variables (such as `Density`, `AdiposeTissue`, and `Hip`) to focus on those that truly impact `BodyFat`.



### 4. Residual Analysis
A residual scatter plot visualization was implemented to validate the model's **linearity** and **homoscedasticity**, ensuring that errors are randomly distributed around zero.

---

## 📊 Final Model Performance
The `modelo_v2` achieved robust results:
* **Adjusted R²:** 0.730 (73% of variance explained).
* **Durbin-Watson:** 2.015 (Indicating no autocorrelation in residuals).
* **F-statistic:** Highly significant (p < 0.001).

---

## 🚀 How to Run
1. Clone the repository or download the files.
2. Ensure you have the required libraries installed:
   ```bash
   pip install pandas numpy seaborn matplotlib statsmodels scikit-learn