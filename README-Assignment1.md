# dnsc6290_assignment_1
DNSC 6290 Assignment 1
Youssef Ragab, Ting Huang, Jaime Sarmiento, Garrett Hastings

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

1. Loading in the required libraries: 
Initializations, 
Importing data

2. Data exploration: 
Histograms, 
Correlation

3. Fitting interpretable models: 
Splitting data into training and validation subsets

4. Elastic Net: 
Defining wrapper function for hyperparameter grid search, 
Fitting elastic net, 
Best AUC assessment, 
Writing submission files

5. Monotonic XGBoost: 
Define utility function for random grid search, 
Fit monotonic XGBoost with random grid search, 
Basic AUC assessment, 
Write submission file

6. Explainable Boosting Machine: 
Define utility function for random grid search, 
Fit EBM with random grid search, 
Basic AUC assessment, 
Write submission file





2 Instructions and Rubric.
This is a pure technical writing assignment. Very little introduction, narrative, or conclusion text is necessary. You may make copious use of bullet points, charts, and tables. (But remember that all charts and
tables should have descriptions!)
Your model card must include the following sections: Intended use, Training data, Evaluation data, Model
details, Quantitative analysis, Ethical considerations. The focus of the model card should be your best
performing remediated model. You should briefly address your other models as “alternative approaches” in
the Quantitative analysis section, and point to why your main model is a better choice.
Rubric:

• Structure (6 pts.)
– Name and contact information for all group members. (Feel free to anonymize for this assignment.
The idea for the real-world is to “sign” your work and make it easy to find yourself if there are
problems in the future, i.e., accountability) (1 pt.)

– Clearly delineated sections for:

∗ Intended use ( 1/2 pt.)




  ∗ Training data ( 1/2 pt.)

  ∗ Evaluation data ( 1
2
pt.)

∗ Model details ( 1
2
pt.)
∗ Quantitative analysis ( 1
2
pt.)
∗ Ethical considerations ( 1
2
pt.)
– Correct and informative external links (e.g., to training and evaluation data) ( 1
2
pt.)
– Correct use and introduction of abbreviations ( 1
2
pt.)
– Charts or tables:
∗ Meaningful and informative use of charts or tables ( 1
2
pt.)
∗ Proper description of charts or tables ( 1
2
pt.)
• Content (13 pts.)

JAIME

– Intended use (2 pts.)
∗ Describe the business value of your group’s best remediated model
∗ Describe how your group’s best remediated model is designed to be used
∗ Describe the intended users for your group’s best remediated model
∗ State whether your group’s best remediated model can or cannot be used for any additional
purposes

TING

– Training data (2 pts.)
∗ State the source of training data
∗ State how training data was divided into training and validation data
∗ State the number of rows in training and validation data
∗ Define the meaning of all training data columns
∗ Define the meaning of all engineered columns
– Evaluation data (2 pts.)
∗ State the source of evaluation (or test) data
∗ State the number of rows in evaluation (or test) data
∗ State any differences in columns between training and evaluation (or test) data

GARRETT/YOUSSEF

– Model details (2 pts.)
∗ State the columns used as inputs in your group’s best remediated model
    * The columns used in the best remediated model are: 'property_value_std', 'no_intro_rate_period_std', 'loan_amount_std', 'income_std', 'conforming', 'intro_rate_period_std', 'debt_to_income_ratio_std', 'term_360'

∗ State the columns used as targets in your group’s best remediated model
    * The target, or dependent, variable in the model is P_default_next_month

∗ State the type of your group’s best remediated model
    * The best remediated mdoel is an Explainable Boosting Machine
    
∗ State the software used to implement your group’s best remediated model
    * The model was created using the interpret Package, specifically using the ExplainableBoostingClassifier function.
    
∗ State the version of the modeling software for your group’s best remediated model
    * The version of the interpret package used is the latest available version at the time of creation: interpret            0.2.4
∗ State the hyperparameters or other settings of your group’s best remediated model
    * Here is a list of the parameters used in the function, they were saved into a list called rems_params within the code: 
              'max_bins': 512,
              'max_interaction_bins': 16,
              'interactions': 10,
              'outer_bags': 4,
              'inner_bags': 0,
              'learning_rate': 0.001,
              'validation_size': 0.25,
              'min_samples_leaf': 5,
              'max_leaves': 5,
              'early_stopping_rounds': 100.0,
              'n_jobs': NTHREAD, 
              'random_state': SEED
              
              NTHREAD = 4
              SEED = 12345
              
1. Quantitative Analysis

* State the metrics used to evaluate your group’s best remediated model
  * After remediating our best EBM model, we found that the AUC (area under Curve) was the best way. Our model got an AUC of .7953. 
* State the values of the metrics for training, validation, and evaluation (or test) data – evaluation (or test) metrics come from the most recent class full evaluation results, link under Assignment 1.
* Provide at least one plot or table from each weekly assignment for a total of at least six plots, that must include the global variable importance and partial dependence of your group’s best remediated model.


![Residuals with Outliers](https://github.com/youssefragab99/dnsc6290_assignment_1/blob/main/residuals_Assignment5.png)

* Address other alternative models considered

EVERYONE SAT NIGHT

– Ethical considerations (2 pts.)
2
∗ Describe potential negative impacts of using your group’s best remediated model:
· Consider math or software problems
· Consider real-world risks: who, what, when and how?
∗ Describe potential uncertainties relating to the impacts of using your group’s best remediated
model:
· Consider math or software problems
· Consider real-world risks: who, what, when and how?
∗ Describe any unexpected or results encountered during training
• Grammar and spelling (1 pt.)
– Correct grammar and punctuation ( 1
2
pt.)
– Correct spelling ( 1
2
pt.)

