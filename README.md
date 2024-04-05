# Healthcare-Patients-Analysis Report
![Healthcare Assistant Jobs Information](https://github.com/Chiamakavivian/Healthcare-Patients-Analysis/assets/156147087/f485170f-5d2d-438d-b166-77c80db561b4)


## Table of Content

- [Healthcare-Patients-Analysis Report](#healthcare-patients-analysis-report)
- [Introduction](#introduction)
- [ Skills demonstrated for the project](#skills-demonstrated-for-the-project)
- [Data Transformation](#data-transformation)
- [Analysis and Visualization](analysis-and-visualization)
- [Conclusion and Recommendation](conclusion-and-recommendation)

### Introduction

This is a Power BI project that shows analysis from the dataset gotten from kaggle. The reason for this project is to track patients experince through the lens of data-driven insights, transforming raw data into actionable strategies that resonate with the heartbeat of humanity.


### Skills demonstrated for the project:

- Data Cleaning
- Data Visualization
- Quick Measure
- Filters
- Critical Thinking
- Problem Solving

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

- Creating Date table
  
  <img width="706" alt="date creation pic" src="https://github.com/Chiamakavivian/Healthcare-Patients-Analysis/assets/156147087/265ba6f5-4f37-4ba2-aa97-7b4c46de6aff">


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
  <img width="357" alt="CF max pic" src="https://github.com/Chiamakavivian/Healthcare-Patients-Analysis/assets/156147087/f53b63e6-62b2-4af7-9a2c-f69035ba398f">


### Analysis and Visualization:

I chose to create simple and easy-to-understand visuals. I used mild and friendly colors. These colors are also bold and eye-catching, which helps to make the visuals more memorable. I wanted to ensure that the visualization would be easily understood by anyone who viewed it, regardless of their level of expertise.

The Dashboard comprises of these visuals:

#### Patients Visit by weektype
<img width="623" alt="Patient visit by weektype" src="https://github.com/Chiamakavivian/Healthcare-Patients-Analysis/assets/156147087/e3bed6ce-6f4e-4984-ad1a-6e1efeffeeeb">

💫 From the analysis and visualization, I find out that, the clinic has more number of visit during the weekdays than weekend

#### Total visit by Age Group
<img width="748" alt="age group" src="https://github.com/Chiamakavivian/Healthcare-Patients-Analysis/assets/156147087/7aa1f81c-907b-4c4c-beea-9de5a11b914b">

💫 From the analysis and visualization, the clinic has the highest number of adult patient visit followed by Middle-childhood.

#### Departmental Referrals 
<img width="739" alt="dept refere" src="https://github.com/Chiamakavivian/Healthcare-Patients-Analysis/assets/156147087/2b48a6a6-6124-451f-892a-1d49a71aff28">

💫 From the analysis and visualization, I find out that, the clinic has the highst number of None-Referrals. None-Referral means the people that walked-in to the clincal by themself.


#### Month with Highest and lowest Visit
<img width="747" alt="month visit" src="https://github.com/Chiamakavivian/Healthcare-Patients-Analysis/assets/156147087/83197d58-390e-4ee5-87cd-a42477eb311f">

💫 From the analysis and visualization, I find out that the month of August has the highest number of visit while February has the lowest, this may be attributed to the winter season typically spans from December to February in the Northern Hemispher and June to August in the Southern Hemispher. It is characterized by colder temperature,snow, or rain, depending on the region.

#### Patient Satisfacation by Race and Age Group
<img width="506" alt="satisf" src="https://github.com/Chiamakavivian/Healthcare-Patients-Analysis/assets/156147087/dce10ff8-b8b3-4026-ab42-accc8a0ae922">

From the analysis and visualization, their are evenly distribution of Satistiction across age group and race. 

#### Patient Wait time by Race and Age Group
<img width="487" alt="wait time" src="https://github.com/Chiamakavivian/Healthcare-Patients-Analysis/assets/156147087/4842496d-40ec-4bb7-a73b-9acf9a4987ce">


### Here is the Dashboard

<img width="674" alt="Healthcare dashboard" src="https://github.com/Chiamakavivian/Healthcare-Patients-Analysis/assets/156147087/db8bc0b3-13d0-4f32-8120-9784761fc320">

You can interact with the report [Here](https://app.powerbi.com/groups/me/reports/8e6d137c-4942-4322-a586-b5d2e98983c6?experience=power-bi)


### Conclusion and Recommendation:
I realized that the waiting times across various departments exhibit significant variability, indicating potential inefficiencies in care delivery processes. Addressing bottlenecks and streamlining workflows can lead to substantial improvements in patient satisfaction and operational efficiency.

I realized that by examing monthly visit trends we can discern seasonal patterns in patient demand, enablingproactive resource allocation and staffing adjustments to ensure optimal care delivery and minimize wait times during peak periods.

The analysis highlights opportunities to improve departmental referrals, reducing unnecessary delays and enhancing care coordination across different specialties. Implementing standardized referral protocols and fostering inter-departmental communication can facilitate smoother transitions for patients between different areas of care.

Satisfaction levels among different age groups and racial demographics underscore the importance of personalized care approaches. Tailoring services to meet the unique needs of preferences of diverse patient populations can significantly enhance overall satisfaction and promote equity in healthcare delivery.

By implementing these, we can effectively address the identified challenges,optimize patient care delivery and elevate the overall pztient experience within our healthcare facility.
