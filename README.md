
# Final Project (Assignment 6)
Youssef Ragab, Ting Huang, Jaime Sarmiento, Garrett Hastings

### Intended use
∗ The Home Mortgage Disclosure Act (HMDA) data contains loan-level information about mortgages in the U.S. The HMDA data is modified to guarantee the privacy of applicants and borrowers. Our best remediated model can identify and solve lending patterns implemented by financial institutions that could be considered discriminatory in terms of race and gender, mainly.

∗ Our group’s best remediated model is as an Explainable Boosting Machine (EBM) that requires to state hyper parameters related to interactions, outer/inner bags, learning rate, validation size, sample leaves, jobs, threads, and seeds.

∗ The intended users of the EBM are financial institutions that do not want to be sued for implementing biased or discriminatory models to lend money. Our best remediated model is an ethical and explanatory model that can provide a technical reason of the approval or denial of each loan.

∗ Additional purposes can be found in the mortgage market with institutions or applicants getting a better understanding of trends and patterns when offering or seeking a loan.

### Training data

The Home Mortgage Disclosure Act (HMDA) training data can be downloaded from from [this link](https://github.com/jphall663/GWU_rml/blob/bf2f60875315cff30257ee24036d8d47836e9ee8/assignments/data/hmda_train_preprocessed.zip) in the class repository.

 * hmda train preprocessed.zip – Zipped CSV HMDA labeled training data

The training data was divided into training and validation data with a 70%/30% train/test split.

Training data contains 112085 rows.
Validation data contains 48253 rows.

Columns:
* high priced: Binary target, whether (1) or not (0) the annual percentage rate (APR) charged for a mortgage is 150 basis points (1.5%) or more above a survey-based estimate of similar mortgages. (High-priced mortgages are legal, but somewhat punitive to borrowers. High-priced mortgages often fall on the shoulders of minority home owners, and are one of many issues that perpetuates a massive disparity in overall wealth between different demographic groups in the US.)
* conforming: Binary numeric input, whether the mortgage conforms to normal standards (1), or whether the loan is different (0), e.g., jumbo, HELOC, reverse mortgage, etc. 
* debt to income ratio std: Numeric input, standardized debt-to-income ratio for mortgage applicants. 
* debt to income ratio missing: Binary numeric input, missing marker (1) for debt to income ratio std. 
* income std: Numeric input, standardized income for mortgage applicants. 
* loan amount std: Numeric input, standardized amount of the mortgage for applicants.
* intro rate period std: Numeric input, standardized introductory rate period for mortgage applicants. 1 
* loan to value ratio std: Numeric input, ratio of the mortgage size to the value of the property for mortgage applicants. 
* no intro rate period std: Binary numeric input, whether or not a mortgage does not include an introductory rate period. • property value std: Numeric input, value of the mortgaged property. 
* term 360: Binary numeric input, whether the mortgage is a standard 360 month mortgage (1) or a different type of mortgage (0).


### Evaluation data 

The Home Mortgage Disclosure Act (HMDA) evaluation data can be downloaded from [this link](https://github.com/jphall663/GWU_rml/blob/bf2f60875315cff30257ee24036d8d47836e9ee8/assignments/data/hmda_test_preprocessed.zip) in the class repository.

* hmda test preprocessed.zip – Zipped CSV HMDA unlabeled test data

Evaluation data contains 19831 rows.

Since it’s evaluation data, it does not contain ‘high price’ column like training data does. ‘high price’ is the response variable.


* The columns used in the best remediated model are: 'property_value_std', 'no_intro_rate_period_std', 'loan_amount_std', 'income_std', 'conforming', 'intro_rate_period_std', 'debt_to_income_ratio_std', 'term_360'

* The target, or dependent, variable in the model is P_default_next_month

* The best remediated model is an Explainable Boosting Machine.
    
* The model was created using the interpret Package, specifically using the ExplainableBoostingClassifier function.

* The version of the interpret package used is the latest available version at the time of creation: interpret            0.2.4

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
              
### Quantitative Analysis

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

In Assignment 3, we tried several different EBMs as we changed parameter values and searched for the best combination of AIR vs. AUC. The highest value of AUC above the minimum threshold of .80 AIR (Adverse Impact Ratio) is the EBM model we chose to retrain.
![Assignment3_AIRvsAUC](https://user-images.githubusercontent.com/84480851/123499802-3b1fff80-d607-11eb-9e42-534a69be5cc0.png)

In Assignment 4, we simulated data to create an attack based on contextual information, such as domain knowledge and publicly available information. A few were created with binomial, exponential, and normal distributions, as is clearly seen below.

![Assignment4_SimulatedData](https://user-images.githubusercontent.com/84480851/123499935-314acc00-d608-11eb-8447-ee00a255ce06.png)


In Assignment 5, we created this image, displaying outliers and a tendency to predict non-high-priced data more accurately than high-priced.

![Residuals with Outliers](https://github.com/youssefragab99/dnsc6290_assignment_1/blob/main/residuals_Assignment5.png)

* We also considered a GLM, a Monotonic XGBoost model, and a Random Forest model, but the results did not compare favorably to our EBM. Notably, the AUC's were consistently lower across the different validation folds for those models in comparison to our EBM.


### Ethical considerations
* In regards to potential negative impacts, while our EBM is remediated to remove negative impacts to a few specific groups, by doing that we may have affected other groups unintentionally. We also possibly could have negatively affected a group for which we did not test.
* Regarding uncertainty, using different versions of software packages could yield different results. 
* Since this affects people's lives, it is of the utmost importance that the code is protected from hacking. Also, since so much money is at stake, this model could be more likely to be the subject of a hack.
* The runtime during the model training was very significant so that more resources (hardware) would be required to run this for a larger scale.  

