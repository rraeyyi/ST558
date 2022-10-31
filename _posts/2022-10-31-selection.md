Feature selection
================
Yi Ren
Oct 31, 2022

The main goal is to construct a model that predicts well or explains the relationships in the data. However, it often takes lots of experience and knowledge to determine the variables. 

In machine learning and statistics, feature selection, also known as variable selection, attribute selection or variable subset selection, is the process of selecting a subset of relevant features (variables, predictors) for use in model construction. I am going to list some commom used methods and comparing the pros and cons. And hopefully it will help a bit for producing a better performing models.

## Stepwise Regression
Stepwise methods use a restricted search through the space of potential models and use a dubious hypothesis testing based method for choosing between models.

pros:
1. It is so easy to apply and improves model generalizability.
2. It yields a simple model that is easy to interpret.
3. It is objective and reproducible.

cons: 
1. It does not consider all possible combination of potential predictors.
2. It outputs biased regression coefficients, confidence intervals, p-values, and R2.
3. It produces an unstable selection of variables.

### Forward Selection (FS) 
This method adds variables to the model until no remaining variable (outside the model) can add anything significant to the dependent variable. 

1. Start with no variables in the model.
2. For all predictors not in the model, check their p-value if they are added to the model. Choose the one with lowest p-value less than αcrit .
3. Continue until no new predictors can be added.

![](https://quantifyinghealth.com/wp-content/uploads/2019/10/forward-stepwise-algorithm.png)

### Backward Elimination (BE)
This method deletes variables one by one from the model until all remaining variables contribute something significant to the dependent variable. 

1. Start with all the predictors in the model
2. Remove the predictor with highest p-value greater than αcrit 3. Refit the model and goto 2
4. Stop when all p-values are less than αcrit .

![](https://quantifyinghealth.com/wp-content/uploads/2019/10/backward-stepwise-algorithm.png)

### Stepwise (SW) 
This method is a modification of the forward selection approach, and differs in that variables already in the model do not necessarily stay.

Stepwise procedures are relatively cheap computationally but they do have some drawbacks.

## Criterion-based Methods 
If there are p potential predictors, then there are 2p possible models. We fit all these models and choose the best one according to some criterion. Clever algorithms such as the “branch-and-bound” method can avoid actually fitting all the models — only likely candidates are evaluated. Criterion-based methods typically involve a wider search and compare models in a preferable manner.
+ Akaike Information Criterion (AIC) & Bayes Information Criterion (BIC) 
+ Adjusted R2
+ Predicted Residual Sum of Squares (PRESS) 
+ Mallow’s Cp Statistic

## Penalized Likelihood Model Selection
Penalized likelihood Model selection can also be achieved by applying least angle selection and shrinkage operator (LASSO) penalties, which are based on subtracting a multiple (λ) of the absolute sum of regression coefficients from the log likelihood and thus setting some regression coefficients to zero

pros:  
LASSO models have been used extensively in high‐dimensional model selection problems, that is when the number of IVs k by far exceeds the sample size n. 

cons:
1. Regression coefficients estimated by the LASSO are biased by intention. Thus, interpretation in explanatory or descriptive models is difficult, and confidence intervals based on resampling procedures do not reach their claimed nominal level. 
2. LASSO estimation is its dependence on the scale of the covariates. 

## Change‐in‐estimate Criterion 
In particular in epidemiologic research the change‐in‐estimate criterion is often applied to select adjustment variables for explanatory models augmented backward elimination (ABE) procedure. 

pros:  
1. ABE leads to larger models and less biased regression coefficients than BE, and to MSE of regression coefficients.
2. It may be useful to eliminate IVs from a model that are irrelevant both for model fit and for interpretation of βs of other IVs. 

cons:  
Experience with ABE approach is still limited.

## 

I would definately start with a basic EDA first. The Natural Seven-step Cycle of Statistical Modeling and Analysis is a great approach, which serves as the most appropriate solution to the variable selection problem in regression. It contains 7 steps:
1. Definition of the problem.    
2. Determining technique.  
3. Use of competing techniques.  
4. Rough comparisons of efficacy.   
5. Comparison in terms of a precise (and thereby inadequate) criterion.  
6. Optimization in terms of a precise and similarly inadequate criterion.  
7. Comparison in terms of several optimization criteria.   

## What variable selection techniques do you prefer and why? 

