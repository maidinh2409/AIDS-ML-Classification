# AIDS-Classification-ML-Models

-- Dataset: AIDS Clinical Trials Group Study 175
-- Source: https://archive.ics.uci.edu/dataset/890/aids+clinical+trials+group+study+175

This is a dataset from the medical industry that contains data of patients diagnosed with HIV/AIDS who are participating in a study with the goal of observing whether or not each patient died within a certain observation time. The purpose is to examine the performance of two different types of AIDS treatments (with ZDV treatments  and no ZDV treatments)

Tools used: Python

Models: Logistics Regression, Kernel SVM, K-Neighbour Networks, Decision Tree

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


**<u><span style="color:gray;">Correlation Detection</span></u>**

![image](https://github.com/user-attachments/assets/7094d7e0-d4b0-4d93-baf2-a29d2ecf5ed2)
