# AIDS-Survivor-ML-Classifiers


![image](https://github.com/user-attachments/assets/8f300174-1a26-43a1-83ee-4f50911ba0cc)


-- Dataset: AIDS Clinical Trials Group Study 175

-- Source: https://archive.ics.uci.edu/dataset/890/aids+clinical+trials+group+study+175

**Description:** 

In the fight against HIV/AIDS, understanding which treatments lead to better patient outcomes is critical. This project explores clinical trial data of patients diagnosed with HIV/AIDS, focusing on survival prediction. Each patient record includes key details—such as whether they received ZDV treatment and how long they were observed. 

Using this data, I applied and compared several machine learning classifiers to predict survival outcomes, aiming to uncover patterns that traditional statistical methods might miss.

**Purpose:** To evaluate the role of machine learning in medical prognosis and investigate treatment differences between ZDV and non-ZDV groups in terms of survival probability.

**Expected insights:** Reveals patterns in patient survival across treatment groups, demonstrates the predictive capability of various classifiers, and provides interpretable results to support healthcare research.

**Tech Stack:**

* Languages: Python
* Models: Logistic Regression, KNN, SVM, Decision Tree
* Libraries & Tools: scikit-learn, pandas, matplotlib

---------------------------------
**<u><span style="color:gray;">Target & Variables</span></u>**

| Name   | Role   | Type      | Demographic     | Description                                            | Units | Missing Values |
|--------|--------|-----------|-----------------|--------------------------------------------------------|-------|-----------------|
| pidnum | ID     | Integer   | None            | Patient ID                                            | None  | no              |
| cid    | Target | Binary    | None            | Censoring indicator (1 = failure, 0 = censoring)      | None  | no              |
| time   | Feature| Integer   | None            | Time to failure or censoring                           | None  | no              |
| trt    | Feature| Integer   | None            | Treatment indicator (0 = ZDV only; 1 = ZDV + d...)    | None  | no              |
| age    | Feature| Integer   | Age             | Age (yrs) at baseline                                  | None  | no              |
| wtkg   | Feature| Continuous| None            | Weight (kg) at baseline                                | None  | no              |
| hemo   | Feature| Binary    | None            | Hemophilia (0 = no, 1 = yes)                           | None  | no              |
| homo   | Feature| Binary    | Sexual Orientation| Homosexual activity (0 = no, 1 = yes)                 | None  | no              |
| drugs  | Feature| Binary    | None            | History of IV drug use (0 = no, 1 = yes)               | None  | no              |
| karnof | Feature| Integer   | None            | Karnofsky score (on a scale of 0-100)                  | None  | no              |
| oprior | Feature| Binary    | None            | Non-ZDV antiretroviral therapy pre-175 (0 = no, ...)   | None  | no              |
| z30    | Feature| Binary    | None            | ZDV in the 30 days prior to 175 (0 = no, 1 = yes)      | None  | no              |
| zprior | Feature| Binary    | None            | ZDV prior to 175 (0 = no, 1 = yes)                     | None  | no              |
| preanti| Feature| Integer   | None            | # Days pre-175 anti-retroviral therapy                 | None  | no              |
| race   | Feature| Integer   | Race            | Race (0 = White, 1 = non-white)                        | None  | no              |
| gender | Feature| Binary    | Gender          | Gender (0 = F, 1 = M)                                  | None  | no              |
| str2   | Feature| Binary    | None            | Antiretroviral history (0 = naive, 1 = experienced)    | None  | no              |
| strat  | Feature| Integer   | None            | Antiretroviral history stratification (1 = 'Anti...)   | None  | no              |
| symptom| Feature| Binary    | None            | Symptomatic indicator (0 = asymp, 1 = symp)            | None  | no              |
| treat  | Feature| Binary    | None            | Treatment indicator (0 = ZDV only, 1 = others)         | None  | no              |
| offtrt | Feature| Binary    | None            | Indicator of off-trt before 96+/-5 weeks (0 = no...)   | None  | no              |
| cd40   | Feature| Integer   | None            | CD4 at baseline                                        | None  | no              |
| cd420  | Feature| Integer   | None            | CD4 at 20+/-5 weeks                                    | None  | no              |
| cd80   | Feature| Integer   | None            | CD8 at baseline                                        | None  | no              |
| cd820  | Feature| Integer   | None            | CD8 at 20+/-5 weeks                                    | None  | no              |


**<u><span style="color:gray;">Problem Statement</span></u>**

According to the research topic of the dataset, it was collected to evaluate the performance of four AIDS treatment methods:

1. ZDV Only (zdv0)
2. ZDV + ddl (zdv_ddl)
3. ZDV + Zal
4. ddl

However, as analyzed in the treatment ratio below, it can be seen that, aside from zdv0, the other three treatments have relatively similar rates of censored cases and deaths. This suggests that there is no clear difference between the three treatments in this dataset. Therefore, incorporating all these treatments into a classification model for predicting who is likely to survive longer is challenging. It is evident that, compared to the other three treatments, using only zdv0 shows a significant difference.

Returning to the final question for this data science project: What is the final question?

If the goal is to evaluate the performance of the experimental treatments as stated in the original task, it is clear that, as a non-primary researcher, there is still insufficient information about the dataset (e.g., whether drug intake is continuous, which cases represent death vs. treatment abandonment, etc.). Therefore, this question would not be effective in this context when all the three treatments return a not really significant impact on classification.

On the other hand, there are several features that are valuable for classification to address the question: Which patients, treated during the observation period, will die (CID = 1)? For example, features like **time, cd420 with a correlation to CID over 0.35**, and the **ratio differences indicate slight changes** in CID = 1 versus CID = 0 (suggesting that patients who die may experience a near-zero immune cell count, while CID = 0 patients show higher changes). 

Furthermore, based on data visualization, other factors like medical history and demographics do not significantly impact the classification of the two groups.

Thus, for training models, the following features—***time, cd420, ratio_differences, and zdv0—will*** be used to develop a model to avoid overfitting and ensure better generalization, as well as answer the question: ***Which patients are likely to die within the observation time range (135 weeks - 147 weeks)?***

**<u><span style="color:gray;">Model Performance</span></u>**

![image](https://github.com/user-attachments/assets/2d8008e0-dec9-4d71-9d99-fedc16c3146a)


**<u><span style="color:gray;">Model Evaluation</span></u>**

In this section, I chose Recall and F1 instead of a fixed metric. The goal of this project is to find the most usable predictive model, which can:

1. Be applied in medical diagnostics to predict whether a patient will die before the observation time.
2. Serve as a tool for comparing the effectiveness of the ZDV-only treatment to other treatments, especially with future research extension.

The importance order of metrics is: Recall >> F1 because:

* Accuracy is unreliable with imbalanced data.
* Recall is most important because it’s critical not to miss actual deaths for diagnostics purpose. Missing a true death is far more problematic than incorrectly predicting someone will die who later survives.
* F1 is second in importance to balance Recall and Precision. A high Recall with low Precision would result in missing many surviving patients, leading to biased treatment assessments if the model is expanded later.

***Final Observation:***

| Models               | Precision                       | Recall                         | F1                             |
|----------------------|---------------------------------|--------------------------------|--------------------------------|
| Logistic Regression   | 0.821293                        | 0.891111                       | 0.854475                       |
| RBF Kernel            | 0.829823                        | 0.886667                       | 0.857269                       |
| Polynomial Kernel     | (2, 0.8178640829595191)         | (9, 0.9111111111111111)        | (2, 0.8537477252047315)        |
| KNN                   | (10, 0.9315845662941326)        | (18, 0.7977777777777778)       | (16, 0.8555398974547911)       |
| Decision Tree         | (1, 0.8160176229979559)         | (4, 0.9155555555555556)        | (1, 0.845968325129438)         |


Based on the evaluation metrics, the following conclusions can be drawn:

1. The best degree for Polynomial SVM is 2, with an F1 score of 0.85 and a Recall of approximately 0.88.
2. The best value of K for KNN is K = 16, with an F1 score of 0.85 and a Recall of 0.80.
3. The best Decision Tree configuration is max-depth = 1, with an F1 score of 0.84 and a Recall of approximately 0.88.
4. Logistic Regression and RBF SVM both show an F1 score of around 0.85 and a Recall of about 0.88.

From these observations, it can be seen that the models with the optimal parameters for each algorithm yield similar F1 scores and Recall values, with F1 at 0.85 and Recall ranging between 0.80 and 0.88. This indicates a good balance between Precision and Recall, suggesting high accuracy in real-world predictions and demonstrating strong generalization.

From the Decision Tree results, it can be inferred that classifying the cid class largely depends on 1-2 important features (assumed to be time and cd420 based on initial data exploration). The best tree depth of 1-2 is sufficient for accurate predictions. As the tree depth increases, taking into account more features, the metrics fluctuate significantly before stabilizing at a maximum depth of 10, indicating overfitting. This suggests that if the tree depth is too deep, the model loses its generalizability.

Logistic Regression and the other models return similar results, suggesting that the data is not highly separable and is nearly linear. Therefore, the similarity in metrics between nonlinear models and Logistic Regression is consistent.

KNN has similar F1 scores to the other models but with a slightly lower Recall, indicating that it is still somewhat influenced by outliers. **F1 seems to be the best metric to reflect the performance of this model** because from the given results, precision Fluctuated alot after looping the k range and Recall stabilize at 0.75 - 0.8. It also means that the KNN is sentitive to outliers so that it cannot get the higher Recall, thus, the best F1 is the one that can maximize the Recall while get the high precision. 

Based on the two intended uses of the model outlined above:

* For **medical diagnosis** (i.e., predicting whether a patient will survive between 135-147 weeks), **Logistic Regression and Decision Tree are the best model**s due to their high accuracy, high Recall, simplicity, speed, and low computational cost.
* For **expanding FUTURE research** and evaluating additional treatment methods, **RBF SVM and Polynomial SVM will be more adaptive** and flexible if there are changes in the relationships between variables, as their margins are not fixed.

