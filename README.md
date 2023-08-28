# Bank Marketing Campaign Prediction

![dataset-cover](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/7d34113b-68e7-406d-87b2-e17dc4fd4c53)


It is a dataset that describing Portugal bank marketing campaigns results.
Conducted campaigns were based mostly on direct phone calls, offering bank client to place a term deposit.
If after all marking afforts client had agreed to place deposit - target variable marked 'yes', otherwise 'no'

# Steps

1.Conduct Exploratory Data Analysis using pandas-profiling.

2.Data preprocessing may not be necessary, as both the XGBoost and LightGBM algorithms can handle categorical and missing data.

2.Build an XGBoost Model.

3.Construct a LightGBM Model.

4.Select the Best Model through Cross-Validation and ROC-AUC analysis.

4.Utilize SHAP for Model Interpretation.

# Dataset
Portugal bank marketing campaigns results

## Data Description

    1 - age (numeric)

    2 - job : type of job (categorical: "admin.","blue-collar","entrepreneur","housemaid","management","retired","self-employed","services","student","technician","unemployed","unknown")

    3 - marital : marital status (categorical: "divorced","married","single","unknown"; note: "divorced" means divorced or widowed)

    4 - education (categorical: "basic.4y","basic.6y","basic.9y","high.school","illiterate","professional.course","university.degree","unknown")

    5 - default: has credit in default? (categorical: "no","yes","unknown")

    6 - housing: has housing loan? (categorical: "no","yes","unknown")

    7 - loan: has personal loan? (categorical: "no","yes","unknown")

    **related with the last contact of the current campaign:**
    
    8 - contact: contact communication type (categorical: "cellular","telephone")

    9 - month: last contact month of year (categorical: "jan", "feb", "mar", …, "nov", "dec")

    10 - day_of_week: last contact day of the week (categorical: "mon","tue","wed","thu","fri")

    11 - duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y="no"). Yet, the duration is not known before a call is                       performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic                      predictive model.
    
    **other attributes:**

    12 - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)

    13 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)

    14 - previous: number of contacts performed before this campaign and for this client (numeric)

    15 - poutcome: outcome of the previous marketing campaign (categorical: "failure","nonexistent","success")
    
    **social and economic context attributes**

    16 - emp.var.rate: employment variation rate - quarterly indicator (numeric)

    17 - cons.price.idx: consumer price index - monthly indicator (numeric)

    18 - cons.conf.idx: consumer confidence index - monthly indicator (numeric)

    19 - euribor3m: euribor 3 month rate - daily indicator (numeric)

    20 - nr.employed: number of employees - quarterly indicator (numeric)

    **Output variable (desired target):**

    21 - y - has the client subscribed a term deposit? (binary: "yes","no")

# Explanatory Data Analysis using Tableau

![Target-Variable-Pie Chart](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/e95fd774-d381-465a-b019-d0b76d6b65d0)


**This is an imbalanced dataset.**


![eda_1](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/030984ad-26e9-4f0f-89e0-f8f1946c5654)
![eda_2](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/1cdebda5-0c4a-488c-afad-1887a3b1af91)
![eda_3](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/30dd6cf1-7930-451e-80ec-5dc6b3b00754)
![eda_4](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/36c0af4e-eabe-428b-b18e-432151ff77a3)
![eda_5](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/ef4be4ba-14a6-48fd-b340-a36404c6e3ce)


# Model Results

![Bank_Marketing_Campaign_Results](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/91dfa23d-6103-471f-8852-bd61d84ed16b)
![XGBoost_Conf](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/a197f238-268f-46af-ae18-e18119e006cd)
![LightGBM_Conf](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/13f39468-89be-430f-ab50-61b52d4ffe77)
![cLASS_rEPORT](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/273e8d20-93c7-4491-b68e-12cbc80447d0)
![ROC](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/00f44e3d-3651-4e35-9367-a406c1c465c7)

**The XGBoost and LightGBM models exhibit very similar performance.**

1. Both the XGBoost and LightGBM models yield an average F1 score of 0.70.. .

2. Tuning LightGBM hyperparameters takes 0.56 minutes, whereas tuning XGBoost hyperparameters takes 19.04 minutes.

**Result : Since both models exhibit very similar performance, we will proceed with the LightGBM model due to its faster training speed.**


# Model Interpretation
The force plot indicates that when macroeconomic indicators such as consumer price index (cons.price.idx) and the number of employed individuals (nr.employed) are high, the log odds of depositing money increase. Additionally, if a customer is single, they are less likely to deposit money.
![SHAP_Force](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/84129729-16f7-4a24-9036-f1cc41205d93)


![shap_SUMMARY](https://github.com/ufuksecilmis/Bank_Marketing_Campaign_Prediction/assets/51096261/e18305ea-7c6b-4c62-b846-a497f9f4364b)

