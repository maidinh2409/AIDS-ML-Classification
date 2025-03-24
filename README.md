# AIDS-Classification-ML-Models

-- Dataset: AIDS Clinical Trials Group Study 175
-- Source: https://archive.ics.uci.edu/dataset/890/aids+clinical+trials+group+study+175

The AIDS Clinical Trials Group Study 175 Dataset contains healthcare statistics and categorical information about patients who have been diagnosed with AIDS. 

Tools used: Python
Models: Logistics Regression, Kernel SVM, K-Neighbour Networks, Decision Tree


This is a dataset from the medical industry that contains data of patients diagnosed with HIV/AIDS who are participating in a study with the goal of observing whether or not each patient died within a certain observation time. The purpose is to examine the performance of two different types of AIDS treatments (with ZDV treatments  and no ZDV treatments)

* Target values: cid - censoring indicator (1 = Death (Patient died within observation time), 0 = Censored (Patient did not die within observation time). **Note: Censored does not mean survival after observation time but can be due to external factors such as the patient stopping the study halfway, accidents, etc. Therefore, outliers may still exist.**
* Features overview:
  + Time (observation time)
  + Personal information (age, weight, race, gender, sexual activity)
  + Medical history (hemophilia (blood clotting disorder), history of IV drug use (drugs injected directly into the vein), Karnofsky score (health index (90-100 meaning normal)))
  + Treatment history (whether or not the patient has been treated with ZDV before)
  + Lab results: counts of two types of immune cells during treatment:
    - CD4: Helper T cells -> The lower the CD4 count, the greater the immune deficiency.
    - CD8: Cytotoxic T cells -> In HIV-infected individuals, CD4 count decreases, and CD8 can increase as a compensatory response to the CD4 deficiency. This results in the CD4:CD8 ratio being potentially low.
