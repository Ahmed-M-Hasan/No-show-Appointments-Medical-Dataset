# No-Show Appointments Dataset Analysis
## by Ahmed M. Hassan

## Introduction

This report describes the process of the no-show appointment medical dataset analysis. The dataset is downloaded from `Kaggle`. This report was completed as a part of Udacity Data Analyst Nano-Degree. It is required to develop a complete data analysis process for a dataset and report the analysis process steps alongside with the findings of your the performed analysis.

## Dataset

The Inspection of dataset on a spreadsheet application shows that it contains `14` columns and `110527` records. The following table summarizes the variable in this dataset.

| Field Name | Description |
|:- | :- |
| `PatientId` | contains the id of each patient |
| `AppointmentID` | contains the id of the appointment itself |
|`Gender1`|indicates the gender of patient `(M)ale` or `(F)emale`|
|`ScheduledDay`| contains the date at which the appointment date was determined |
|`AppointmentDay`| contains the date at which the appointment will occur |
|`Age`|patient age|
|`Neighbourhood`|appointment location|
|`Scholarship`| indicates whether or not the patient is enrolled in Brasilian welfare program|
|`Hipertension`|indicates whether or not the patient has a hypertension|
|`Diabetes`|indicates whether or not the patient has diabetes|
|`Alcoholism`|indicates whether or not the patient drinks alcohol products|
|`Handcap`|an integer varying from 0 to 4 showing degree of handicap|
|`SMS_received`|indicates whether or not a reminder SMS was sent to the patient|
|`No-show`|indicates whether or not the patient missed his/her appointment|

## Scope of Analysis

The analysis is based on using this data to determine `which features can be used to predict whether or not the patient will miss his/her appointment`. Thus, the dependent variable here will be the absence or presence of the patient. The independent variable that will be considered:<br>
- Gender
- Interval between the appointment setting date and the actual appointment date 
- Age
- Hospital location
- Brasilian program enrollment
- Hypertension presence
- Diabetes presence
- Alcoholism
- Handicap degree
- Reminder SMS receival <br>

The distribution of each variable in the dataset will be first investigated. Then, the relationship between each variable and the absence ratio will be investigated. 

## Data Analysis Process
### Data Wrangling

The dataset used was downloaded from <a href="https://d17h27t6h515a5.cloudfront.net/topher/2017/October/59dd2e9a_noshowappointments-kagglev2-may-2016/noshowappointments-kagglev2-may-2016.csv">Kaggle</a>. The data is provided as a flat file `.CSV` file. The data is loaded into a dataframe using `Pandas` library.

### Data Assessing

The data was inspected and the summary of the issues is provided below.

| Column id | Data Issue Type | Issue Description |
|:- | :- | :- |
|`PatientId`|quality|should be of `str` data type not `int64`|
|`AppointmentID`|quality|should be of `str` data type not `float64`|
|`ScheduledDay`|quality|should be of `datetime` data type not `str`|
|`AppointmentDay` |quality|should be of `datetime` data type not `str`|
|`Hipertension` |quality|column name is not representative, has a typo|
|`Handcap` |quality|column name is not representative, has a typo|
|`No_show` |quality|column name is not clear enough alongside with the encoding used in the values|
|`Age` |quality|column has negative age value|

### Data Cleaning

The previous identified issues were cleaned. The clean dataset was saved in a separate dataframe for further analysis.

### Exploratory Data Analysis

The core question is which factor should be considered for prediction of patient absence. The overall absence ratio should be first evaluated to initiate a reference for comparing effect of different independent variables. The overall absence ratio is 0.2 or 20% of all patient would miss their appointment. Thus, the absent patients represent the less fimilar class in a skewed classes categorical variable. The effect of the independent variables shown in the introduction on the absence ratio was investigated.

## Conclusions

There are 10 different variables are investigated to check their relationship with the absence probability. First, the overall absence ratio was calculated. Then, the effect of changing these variables on the absence fraction was investigated. <br>
It was concluded that 
- Brasilian program enrollment
- Hypertension diagnosis
- Diabetes diagnosis
- Reminder SMS receival
- Handicap degree
- Neighbourhood 
- Patient Age
- Wait period

can be considered as effecting factor on absence probability. This analysis is limited as it didn't consider the inter-relationship between the above factors and this inter-relationship effect on the absence fraction. In other words, changing the age has shown a change in absence fraction, but this effect can't be justified only by age change. As, with age change, other variables change also. The change of the absence fraction is a contribution of all the changing variables with age group change. 

Also, the intercorrelation between these independent variables were investigated using the correlation coefficient. it was found that
- There is a positive correlaion between `Hypertension`, `Diabetes` and `Age`.
- There is a positive correlation between `WaitPeriod` and `SMS_received`. This correlation explains why receiving SMS increases the absence fraction. As receiving the SMS is correlated with long wait period which shows a positive correlation with absence fraction.<br>

