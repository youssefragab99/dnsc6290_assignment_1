# dnsc6290_assignment_1
DNSC 6290 Assignment 1
Youssef Ragab, Ting Huang, Jaime Sarmiento

Based on the assignment prompt, data exploration is performed as well as interpratable models such as elastic net, XGBoost, and Random forest are fitted. The target variable is high_priced, whereas the covariates are as follows: 
conforming, 
debt_to_income_ratio_std, 
debt_to_income_ratio_missing, 
income_std, 
loan_amount_std, 
intro_rate_period_std, 
loan_to_value_ratio_std, 
no_intro_rate_period_std, 
property_value_std, 
term_360, 

1. Loading in the required libraries
Initializations
Importing data

2. Data exploration
Histograms
Correlation

3. Fitting interpretable models
Splitting data into training and validation subsets

4. Elastic Net
Defining wrapper function for hyperparameter grid search
Fitting elastic net
Best AUC assessment
Writing submission files

5. Monotonic XGBoost
Define utility function for random grid search
Fit monotonic XGBoost with random grid search
Basic AUC assessment
Write submission file

6. Random forest
7. Explainable Boosting Machine
Define utility function for random grid search
Fit EBM with random grid search
Basic AUC assessment
Write submission file
