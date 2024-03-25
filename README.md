# Healthcare-Patients-Analysis Report

## Table of Content

- [Healthcare-Patients-Analysis Report](#healthcare-patients-analysis-report)
- [Introduction](#introduction)
- [ Skills demonstrated for the project](#skills-demonstrated-for-the-project)
- [Data Transformation](#data-transformation)

### Introduction
This is a Power BI project that shows analysis from the dataset gotten from kaggle. The reason for this project is to track patients experince through the lens of data-driven insights, transforming raw data into actionable strategies that resonate with the heartbeat of humanity.

### Skills demonstrated for the project:
Data Cleaning,
Data Visualization,
Quick Measure,
Filters, 
Critical Thinking,
Problem Solving.

### Problem statement:
1. Identify and mitigate factors contributing to extended waiting times for patients across various departments, ultimately enhancing the efficiency of care delivery processes.

2. Analyze monthly visit trends to identify patterns and fluctuations in patient demand, allowing for proactive resource allocation and staffing adjustments to meet fluctuating needs effectively.

3. Evaluate departmental referral patterns to streamline care pathways, reduce unnecessary delays, and ensure seamless transitions between different facets of care.

4. Investigate satisfaction levels among different age groups and racial demographics to address disparities in care experiences and tailor services to meet the diverse needs of our patient population effectively.

### Data Source
Kaggle
### Tool
- Power Bi - [Download Here](https://microsoft.com/powerbi)
### Data Transformation
The Healthcare data was not in a clean format, so I had to clean and transform it before I could create the visuals. The Data was efficiently cleaned and transformed with the Power Query editor in Power BI.

#### Some of the applied steps include:

- Making first role Headers

- Changing Data Types

- Split Description Column By Delimiter in Oder To Create The Reason Column.

- **Creating Measures to show**:
  
   % Administrative Sechedule
  ```DAX
  % Administrative Sechedule =
  DIVIDE(
  COUNTROWS(
  FILTER('Clinical Report','Clinical Report'[patient_admin_flag]=TRUE())),
  [Total_Patients])
  ```
  *Total_Patients*
  ```DAX
  Total_Patients = COUNTROWS('Clinical Report')
  ```
  *Average_Satisfaction_Score*
  ```DAX
  Average_Satisfaction_Score =
  CALCULATE(
  AVERAGE('Clinical Report'[patient_sat_score]),
  'Clinical Report'[patient_sat_score]<>BLANK())
  ```
  *Average_Wait_Time*
  ```DAX
  Average_Wait_Time =
  AVERAGE('Clinical Report'[patient_waittime])
  ```
  *CF Max Point(Month)*
  ```DAX
  CF Max Point(Month) =
   VAR _Patient_Table =
   CALCULATETABLE(
  ADDCOLUMNS(
  SUMMARIZE('Date','Date'[Month]),
   "@Total_Patients", [Total_Patients]),
   ALLSELECTED())
   VAR _MinValu = MINX(_Patient_Table,[@Total_Patients])
   VAR _MaxValu = MAXX(_Patient_Table,[@Total_Patients])
  VAR _Total_Patients = [Total_Patients]
  RETURN
   SWITCH(TRUE(),
  _Total_Patients= _MinValu, 0, _Total_Patients=_MaxValu, 1
  ```


