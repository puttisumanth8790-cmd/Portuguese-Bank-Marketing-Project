# Portuguese-Bank-Marketing-Project
Bank Marketing – Term Deposit Subscription Prediction
Predicting whether a client will subscribe to a term deposit after a direct-marketing phone campaign run by a Portuguese bank, using exploratory data analysis and machine learning classification models.

Table of Contents
Project Overview
Dataset
Repository Structure
Workflow
Models and Results
Limitations and Future Work
How to Run
Tech Stack
Author
Project Overview
Banks run costly phone campaigns, and only a small share of contacted clients subscribe. The goal of this project is to:

Analyse the campaign data to understand which client, contact and economic factors relate to subscription.
Build a classification model that predicts whether a client will subscribe (y = yes/no).
Compare multiple algorithms to pick the best performer.
Dataset
File: bank-additional-full.csv (semicolon-separated)
Source: UCI Machine Learning Repository – Bank Marketing dataset (Moro, Cortez & Rita, 2014)
Size: 41,188 rows × 21 columns
Target: y – has the client subscribed to a term deposit? (yes / no)
Class balance: 36,548 no vs 4,640 yes (heavily imbalanced)
Group	Features
Client	age, job, marital, education, default, housing, loan
Last contact	contact, month, day_of_week, duration
Campaign	campaign, pdays, previous, poutcome
Economic context	emp.var.rate, cons.price.idx, cons.conf.idx, euribor3m, nr.employed
Missing values are encoded as unknown in the raw file (notably in default, education, housing, loan, job, marital).

Repository Structure
.
├── Bank_Marketing_Term_Deposit_Prediction.ipynb   # Full analysis and modelling notebook
├── bank-additional-full.csv                       # Dataset
└── README.md
Workflow
Data loading – read the CSV with sep=';' and treat unknown as missing.
Exploratory Data Analysis
Summary statistics, data types, missing-value counts
Automated profiling report with Sweetviz
Univariate plots: histograms, distribution plots, box plots
Bivariate plots: numeric features and categorical features split by subscription outcome
Data preprocessing
Renamed columns with dots (e.g. emp.var.rate → emp_var_rate)
Imputed missing categorical values with the mode
Encoded categorical variables (manual mapping and LabelEncoder)
Checked outliers with box plots
Removed 14 duplicate rows
Feature selection – correlation heatmap; dropped highly correlated emp_var_rate and nr_employed.
Scaling and balancing – StandardScaler and SMOTE oversampling of the minority class.
Modelling – 80/20 train–test split, trained and evaluated eight classifiers.
Hyperparameter tuning – RandomizedSearchCV set up for Random Forest.
Models and Results
Metrics on the 20% hold-out test set (14,614 samples, after SMOTE):

Model	Accuracy	F1-score
Logistic Regression	0.857	0.86
K-Nearest Neighbors (k=2)	0.948	0.950
Bagging (KNN base)	–	0.927 (weighted)
Random Forest	0.96	0.957
Support Vector Classifier	0.902	0.907
Decision Tree	0.921	0.921
Naive Bayes (Bernoulli)	0.740	0.721
Gradient Boosting	0.932	–
XGBoost	0.953	0.953
Takeaway: tree-based ensembles (Random Forest, XGBoost) and KNN scored highest on the hold-out set, while Naive Bayes performed worst.

Limitations and Future Work
Oversampling before the split: SMOTE was applied before the train–test split, so synthetic samples derived from test-set neighbours can leak into training and inflate hold-out scores. The cross-validated ROC-AUC on the original data (Logistic Regression ≈ 0.90, KNN ≈ 0.74, Bagging ≈ 0.77) is a more conservative view. Next step: split first, then apply SMOTE inside a pipeline on the training folds only.
duration feature: call duration is only known after the call ends, so it should be excluded when building a realistic pre-call prediction model (the dataset authors note this).
Imbalanced data metrics: report precision/recall, PR-AUC and ROC-AUC on an untouched, imbalanced test set rather than accuracy alone.
Encoding: nominal features such as job and marital were integer-encoded; one-hot encoding would avoid implying an order.
Time-aware validation: the data is ordered by date, so time-based splits would better reflect real deployment.
Complete and report the Random Forest hyperparameter search, and add feature-importance analysis.
How to Run
Clone the repository:
git clone https://github.com/A-praveen123/<your-repo-name>.git
cd <your-repo-name>
Install the dependencies:
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn xgboost sweetviz jupyter
Open the notebook and update the data path in the loading cell to a relative path:
data = pd.read_csv("bank-additional-full.csv", sep=';', na_values='unknown')
Run all cells:
jupyter notebook Bank_Marketing_Term_Deposit_Prediction.ipynb
Tech Stack
Python · Pandas · NumPy · Matplotlib · Seaborn · Scikit-learn · Imbalanced-learn (SMOTE) · XGBoost · Sweetviz · Jupyter Notebook

Acknowledgements
Dataset: S. Moro, P. Cortez and P. Rita, A Data-Driven Approach to Predict the Success of Bank Telemarketing, Decision Support Systems, 2014 (UCI Machine Learning Repository).
