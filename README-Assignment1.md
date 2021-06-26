
# Final Project (Assignment 6)
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
  * The five different metrics used to evaluate our models were: ACC, AUC, F12, LogLoss, and MSE.
  * ACC:  Maximum Accuracy
  * AUC: Area Under the ROC Curve
  * F1: Maximum F1 - measures sensitivity and precision
  * LogLess: Weights predictions differently based on how confident the prediction was.
  * MSE: Mean Squared Error - measures how accurate the predictions were, with further errors weighted more heavily.
* We trained the model on 10 grid search runs, randomizing various parameters such as max bins, max interactions, outer bags, inner bags, etc. This resulted in a best grid search AUC score of .8281 on our training data. Our metrics against the validation sets were: Acc ranged from .897-.908 depending on the fold number, AUC from .827-.906, f1 from .369-.408, logloss from .245-.263, and MSE from .073-.08.

* Plots

In Assignment 1, before we began modeling, to get a better picture of the features and their potential interactions between one another, we created a correlation matrix. 

![Assignment1_Corr](https://user-images.githubusercontent.com/84480851/123499541-905b1180-d605-11eb-8e3d-164339f2acf0.png)

In Assignment 2, we found each feature's importance in our EBM model. 
![Assignment2_Feat_Importance](https://user-images.githubusercontent.com/84480851/123500168-0eb9b280-d60a-11eb-8eed-6885174a7fcb.PNG)

Also in Assignment 2, we found the partial dependence for each of the ten variables for our 3 different models. The images of the best model are the ones on the right, EBM. 

![Assignment2_Partial_Dep1](https://user-images.githubusercontent.com/84480851/123499394-69e8a680-d604-11eb-934d-68897aabdc0d.PNG)
![Assignment2_Partial_Dep2](https://user-images.githubusercontent.com/84480851/123499395-69e8a680-d604-11eb-9e10-69498a64afcd.PNG)
![Assignment2_Partial_Dep3](https://user-images.githubusercontent.com/84480851/123499391-69501000-d604-11eb-91a8-113ff34fc5a6.PNG)
![Assignment2_Partial_Dep4](https://user-images.githubusercontent.com/84480851/123499392-69501000-d604-11eb-9326-c3b02e28a450.PNG)
![Assignment2_Partial_Dep5](https://user-images.githubusercontent.com/84480851/123499393-69e8a680-d604-11eb-93cb-70a28f3d6798.PNG)

In Assignment 3, we tried several different EBMs as we changed paramter values and searched for the best combination of AIR vs. AUC. The highest value of AUC above the minimum threshold of .80 AIR (Adverse Impact Ratio) is the EBM model we chose to retrain.
![Assignment3_AIRvsAUC](https://user-images.githubusercontent.com/84480851/123499802-3b1fff80-d607-11eb-9e42-534a69be5cc0.png)

In Assignment 4, we simulated data to create an attack based on contextual information, such as domain knowledge and publicly available information. A few were created with binomial, exponential, and normal distributions, as is clearly seen below.

![Assignment4_SimulatedData](https://user-images.githubusercontent.com/84480851/123499935-314acc00-d608-11eb-8447-ee00a255ce06.png)


In Assignment 5, we created this image, displaying outliers and a tendency to predict non-high-priced data more accurately than high-priced. 
![Residuals with Outliers](https://github.com/youssefragab99/dnsc6290_assignment_1/blob/main/residuals_Assignment5.png)

* Address other alternative models considered
* We also considered a GLM, a Monotonix XGBoost model, and a Random Forest model, but the results did not compare favorably to our EBM. Notably, the AUC's were consistently lower across the different validation folds for those models in comparison to our EBM.



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

