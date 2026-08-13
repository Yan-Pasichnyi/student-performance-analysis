# Student Performance Analysis

This project analyzes the **Student Performance Dataset**, which contains 33 features describing students' academic results, family background, lifestyle, and personal characteristics.  
The dataset is sourced from Kaggle and is based on a survey of secondary school students in a math course.

## 🎯 Research Questions

### 1. Is alcohol consumption related to academic performance?
The dataset includes weekday (`Dalc`) and weekend (`Walc`) alcohol consumption.  
This project investigates whether higher alcohol intake correlates with lower grades (`G1`, `G2`, `G3`).

### 2. Which factors are the strongest predictors of the final grade?
The dataset contains many potential predictors such as study time, absences, family relationships, free time, and more.  
The goal is to identify which of these features have the strongest impact on student performance.

### 3. Does the occupation of parents influence student grades?
The dataset includes the mother's and father's job (`Mjob`, `Fjob`).  
This project examines whether parental occupation is associated with differences in academic outcomes.

### 4. Does the student's gender affect academic performance?
The variable `sex` allows us to analyze whether male and female students show different grade patterns  
and whether gender plays a role in academic achievement.

## 📊 Dataset Description

The dataset contains:
- **395 rows**
- **33 columns**
- A mix of numeric and categorical features
- Information about:
  - demographics (age, gender)
  - family background (education, occupation, family size)
  - lifestyle (free time, going out, alcohol consumption)
  - academic performance (G1, G2, G3)

## 📌 Summary

This project aims to understand how lifestyle choices, family background, and demographic factors  
shape student performance. The analysis includes descriptive statistics, visualizations, and correlation studies  
to answer the research questions clearly and effectively.

## 🧠 Modeling Results

Two regression models were trained to predict the final grade (G3): a baseline Linear Regression and a Random Forest Regressor.

**Handling G3=0:** 38 students had G3=0, which likely reflects students who did not complete the final exam rather than a genuine low score. These rows were excluded from the modeling dataset.

**Avoiding data leakage:** G1 and G2 (grades from earlier periods) are very strongly correlated with G3 (0.80 and 0.90 in the correlation matrix). Including them as features would let the model "see" a near-answer rather than learn from genuine predictors, so they were excluded from the main models.


| Model                  | Features        | MAE  | RMSE |
|-------------------------|------------------|------|------|
| Linear Regression        | Without G1/G2     | 2.30 | 2.75 |
| Random Forest             | Without G1/G2     | 2.23 | 2.73 |
| Linear Regression (leakage demo) | With G1/G2 | 0.67 | 0.90 |

The near-identical performance of Linear Regression and Random Forest (without G1/G2) suggests the relationships in the data are largely linear, and that family background, lifestyle, and demographic features alone have limited predictive power. Including G1/G2 improves MAE by roughly 3x, clearly demonstrating the effect of data leakage — G1/G2 essentially reveal the answer rather than serve as genuine predictors.
### Feature Importance (Random Forest)
[Заполнишь после того, как посмотрим feature_importances_]
