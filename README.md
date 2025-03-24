# AIDS-Classification-ML-Models

-- Dataset: AIDS Clinical Trials Group Study 175
-- Source: https://archive.ics.uci.edu/dataset/890/aids+clinical+trials+group+study+175

This is a dataset from the medical industry that contains data of patients diagnosed with HIV/AIDS who are participating in a study with the goal of observing whether or not each patient died within a certain observation time. The purpose is to examine the performance of two different types of AIDS treatments (with ZDV treatments  and no ZDV treatments)

Tools used: Python
Models: Logistics Regression, Kernel SVM, K-Neighbour Networks, Decision Tree

---------------------------------

name	role	type	demographic	description	units	missing_values
0	pidnum	ID	Integer	None	Patient ID	None	no
1	cid	Target	Binary	None	censoring indicator (1 = failure, 0 = censoring)	None	no
2	time	Feature	Integer	None	time to failure or censoring	None	no
3	trt	Feature	Integer	None	treatment indicator (0 = ZDV only; 1 = ZDV + d...	None	no
4	age	Feature	Integer	Age	age (yrs) at baseline	None	no
5	wtkg	Feature	Continuous	None	weight (kg) at baseline	None	no
6	hemo	Feature	Binary	None	hemophilia (0=no, 1=yes)	None	no
7	homo	Feature	Binary	Sexual Orientation	homosexual activity (0=no, 1=yes)	None	no
8	drugs	Feature	Binary	None	history of IV drug use (0=no, 1=yes)	None	no
9	karnof	Feature	Integer	None	Karnofsky score (on a scale of 0-100)	None	no
10	oprior	Feature	Binary	None	Non-ZDV antiretroviral therapy pre-175 (0=no, ...	None	no
11	z30	Feature	Binary	None	ZDV in the 30 days prior to 175 (0=no, 1=yes)	None	no
12	zprior	Feature	Binary	None	ZDV prior to 175 (0=no, 1=yes)	None	no
13	preanti	Feature	Integer	None	# days pre-175 anti-retroviral therapy	None	no
14	race	Feature	Integer	Race	race (0=White, 1=non-white)	None	no
15	gender	Feature	Binary	Gender	gender (0=F, 1=M)	None	no
16	str2	Feature	Binary	None	antiretroviral history (0=naive, 1=experienced)	None	no
17	strat	Feature	Integer	None	antiretroviral history stratification (1='Anti...	None	no
18	symptom	Feature	Binary	None	symptomatic indicator (0=asymp, 1=symp)	None	no
19	treat	Feature	Binary	None	treatment indicator (0=ZDV only, 1=others)	None	no
20	offtrt	Feature	Binary	None	indicator of off-trt before 96+/-5 weeks (0=no...	None	no
21	cd40	Feature	Integer	None	CD4 at baseline	None	no
22	cd420	Feature	Integer	None	CD4 at 20+/-5 weeks	None	no
23	cd80	Feature	Integer	None	CD8 at baseline	None	no
24	cd820	Feature	Integer	None	CD8 at 20+/-5 weeks	None	no

**<u><span style="color:gray;">Correlation Detection</span></u>**

![image](https://github.com/user-attachments/assets/7094d7e0-d4b0-4d93-baf2-a29d2ecf5ed2)
