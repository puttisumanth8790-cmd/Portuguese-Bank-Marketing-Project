# Portuguese Bank Marketing Prediction 📊

## 📌 Project Overview

The **Portuguese Bank Marketing Prediction** project aims to predict whether a bank customer will subscribe to a term deposit based on personal information, financial details, and previous marketing campaign interactions.

The bank conducts direct marketing campaigns through phone calls. However, contacting every customer is time-consuming and expensive.

This project uses Machine Learning classification algorithms to identify potential customers who are more likely to subscribe to a term deposit, helping the bank improve marketing effectiveness and reduce campaign costs.

## 🎯 Business Objective

- Predict whether a customer will subscribe to a term deposit.
- Identify potential customers who are more likely to respond positively.
- Improve marketing campaign effectiveness.
- Reduce unnecessary marketing calls.
- Support data-driven business decisions.

## 📂 Dataset Description

The project uses the **Portuguese Bank Marketing Dataset** (`bank-additional-full.csv`).

The dataset contains customer information, campaign details, and economic indicators.

**Target Variable:**
- `y = yes`: Customer subscribed to a term deposit.
- `y = no`: Customer did not subscribe to a term deposit.

**Features include:**
- Age
- Job
- Marital Status
- Education
- Default
- Housing Loan
- Personal Loan
- Contact
- Month
- Day of Week
- Duration
- Campaign
- Pdays
- Previous
- Poutcome
- Employment Variation Rate
- Consumer Price Index
- Consumer Confidence Index
- Euribor 3 Month Rate
- Number of Employees

## 🛠️ Technologies & Libraries Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Imbalanced-learn (SMOTE)
- XGBoost
- Sweetviz
- Jupyter Notebook

## 🔍 Project Workflow

### 1. Data Collection
- Loaded the Portuguese Bank Marketing dataset.
- Examined the dataset structure and features.

### 2. Exploratory Data Analysis (EDA)
- Univariate Analysis
- Bivariate Analysis
- Multivariate Analysis
- Distribution Analysis
- Correlation Analysis
- Outlier Detection

### 3. Data Preprocessing
- Handled missing values.
- Converted categorical variables into numerical representations.
- Applied Label Encoding and One-Hot Encoding.
- Removed duplicate records.
- Performed feature selection.
- Applied StandardScaler for feature scaling.

### 4. Handling Imbalanced Data
- Used SMOTE (Synthetic Minority Over-sampling Technique) to balance the target classes.

### 5. Model Building

The following Machine Learning classification algorithms were implemented:

1. Logistic Regression
2. K-Nearest Neighbors (KNN)
3. Bagging Classifier
4. Random Forest Classifier
5. Support Vector Machine (SVM)
6. Decision Tree Classifier
7. Naive Bayes
8. Gradient Boosting Classifier
9. XGBoost Classifier

### 6. Model Evaluation

The models were evaluated using:

- Accuracy Score
- Precision
- Recall
- F1-Score
- Confusion Matrix
- ROC-AUC Score
- Classification Report
- Cross-Validation

### 7. Hyperparameter Tuning

- Applied RandomizedSearchCV.
- Performed hyperparameter tuning for the Random Forest model.
- Used F1-score as the optimization metric.

## 🏆 Project Conclusion

Multiple classification algorithms were implemented and evaluated to predict whether customers would subscribe to a term deposit.

Based on the project analysis, **Random Forest Classifier was identified as the better-performing model** among the evaluated models.

The project demonstrates how Machine Learning can help financial institutions identify potential customers, optimize marketing campaigns, and reduce operational costs.

## 📁 Project Structure

```text
Portuguese-Bank-Marketing-Prediction/
│
├── Portuguese Bank Marketing Project.ipynb
├── bank-additional-full.csv
└── README.md
```

## ⚙️ How to Run the Project

**Step 1:** Clone the repository.

```bash
git clone https://github.com/your-username/Portuguese-Bank-Marketing-Prediction.git
```

**Step 2:** Navigate to the project directory.

```bash
cd Portuguese-Bank-Marketing-Prediction
```

**Step 3:** Install the required libraries.

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn xgboost sweetviz jupyter
```

**Step 4:** Open Jupyter Notebook.

```bash
jupyter notebook
```

**Step 5:** Open `Portuguese Bank Marketing Project.ipynb` and run the notebook cells.

Make sure the dataset is available in the correct location and update the dataset file path if necessary.

## 🚀 Future Improvements

- Build an interactive dashboard using Streamlit.
- Deploy the best-performing model as a web application.
- Improve model performance through advanced hyperparameter optimization.
- Use feature importance to identify the factors influencing customer subscriptions.
- Implement a leakage-free preprocessing and model evaluation pipeline.

## 👨‍💻 Author

**Your Name**

If you find this project useful, please give the repository a ⭐ on GitHub!
