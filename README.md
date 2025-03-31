# Challenges-Of-Healthcare-Accessibility-In-Africa
This project analyzes healthcare facility data from selected afrcian communities, to identify disparities in access to healthcare between rural and urban regions, 
and evaluate the efficiency of healthcare funding. The analysis uses power BI (power query, Dax, visualizations) to genrate insights.

## Table of content
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Tools](#tools)
- [Data Cleaning](#data-cleaning)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results and Findings](#results-and-findings)
- [Recommendations](#recommendations)


### Project Overview

This project aims to analyze the challenges of healthcare accessibilty in Africa, using data gathered from selected communities to:
- Identify key disparities in healthcare access between rural and urban regions.
- Analyze the efficiency of healthcare funding and resource allocation across different facilities.
- Provide data-driven insights to improve emergency response times and patient satisfaction.
- Develop strategic recommendations for policymakers to ensure equitable healthcare access.
- To communicate findings effectively using visualization techniques.
![rec](https://github.com/user-attachments/assets/96df4922-8f9f-4859-94b0-65b8f7a0c7ff)

[Click to downaod and interact with the dashboard](CHALLENGES OF HEALTHCARE ACCESSIBILTY IN NIGERIA.pbix)

### Dataset

The dataset used for this analysis is the [challenges of healthcare accessiblity in Africa ](https://github.com/timiols/Challenges-Of-Healthcare-Accessibility-In-Africa/blob/main/Healthcare_Access_Africa.csv) dataset consisting of 15 columns and 2001 rows.
### Tools
- **Power query**
- **Power Bi**
  
### Data Cleaning

The following steps were taken to improve the dataset;
- **Urban_rural_area** column was created to categorize the regions into their respective area type. To achieve this, the custom column function in power query was used, using data from *population* and *facility type* columns.
- **Funding per patient visit** column was created and added to the dataset using average function in Dax to derive average funding per patient visit. This was achieved using data from *funding received (USD)]*  and *annual Patient visits* columns.
- Measure was created using DAX  and added to the dataset to calculate the Pearson correlation coefficient between *funding received (USD)* and *emergency response time (minutes)* columns.

 *improved dataset* [Healthcare accessibilty in africa.xlsx](https://github.com/timiols/Challenges-Of-Healthcare-Accessibility-In-Africa/blob/main/CLEAN%20DATASET.csv)

### Exploratory Data Analysis

- How does the distribution of healthcare facilities compare between rural and urban regions?

  ![Screenshot 2025-03-25 133652](https://github.com/user-attachments/assets/9a3007dd-8eae-427c-b8e7-336df6cb943c)
- Are urban healthcare facilities receiving more funding than rural ones?

   ![Screenshot 2025-03-25 133703](https://github.com/user-attachments/assets/c9fa1ddf-9def-45ee-8dc6-a99f97a0620f)
- Are healthcare facilities with higher funding more likely to have shorter emergency response times?

  ![Screenshot 2025-03-25 133722](https://github.com/user-attachments/assets/ba92d887-3f6a-4271-9f35-debf4a51b926)

- Which facility types (hospitals, clinics, health centres) show the highest efficiency in terms of funding per patient visit?

  ![Screenshot 2025-03-25 133734](https://github.com/user-attachments/assets/55ade1f7-0713-4bae-8b8b-dd562db7bb92)

 ### Data analysis
 
 Power query M language and Power BI dax functions were used to create and insert relevant records to enhance the useability of the dataset.
 Here are the queries deployed in this analyis:
 ```M language
if [Facility Type] = "Hospital" then "Urban" 
else if [Population] >= 6000 then "Urban" 
else if [Facility Type] = "Clinic" or [Facility Type] = "Health Center" and [Population] < 6000 then "Rural" 
else "Rural"
```
```DAX
Funding_Emergency_Response_Correlation = 
VAR XMean = AVERAGE(Healthcare_Access_Africa[Funding Received (USD)])
VAR YMean = AVERAGE(Healthcare_Access_Africa[Emergency Response Time (minutes)])
VAR Numerator = SUMX(Healthcare_Access_Africa, 
    (Healthcare_Access_Africa[Funding Received (USD)] - XMean) * 
    (Healthcare_Access_Africa[Emergency Response Time (minutes)] - YMean))
VAR Denominator = SQRT(
    SUMX(Healthcare_Access_Africa, (Healthcare_Access_Africa[Funding Received (USD)] - XMean)^2) *
    SUMX(Healthcare_Access_Africa, (Healthcare_Access_Africa[Emergency Response Time (minutes)] - YMean)^2)
)
RETURN 
    IF(Denominator = 0, BLANK(), Numerator / Denominator)
```
```
Funding per Visit = 
DIVIDE(
    'Healthcare_Access_Africa'[Funding Received (USD)], 
    'Healthcare_Access_Africa'[Annual Patient Visits], 
    BLANK()
)
```

### Results and Findings

- Healthcare Facility Distribution: Urban areas have 1,220 facilities (61%), while rural areas have only 780 (39%). Rural regions have fewer healthcare facilities, limiting access for      underserved populations.
- Funding Distribution: Interestingly, urban and rural facilities receive almost equal funding averagely ($107,026 for urban and $106,242 for rural areas). Despite the closeness in         funding, rural areas have fewer facilities and the Funding distribution does not align with population needs - rural regions need more support.
- Funding vs. Emergency Response Time: There is no strong correlation (-0.032) between funding and emergency response time. More funding does not necessarily improve response times.        Other factors (infrastructure, staffing, logistics) may be more critical.
- Efficiency of Facility Types (Funding per Patient Visit): Hospitals are the most efficient, with the lowest funding per visit ($16.35). Hospitals benefit from higher patient volumes      and economies of scale compared to clinics and health centres.
  
### Recommendations

- Bridge Urban-Rural gaps in healthcare accessibility by increasing the number of rural healthcare facilities to improve accessibility and also enhance transportation network and           electricity supply in rural areas.
- Reallocate more funding to rural areas based on patient demand.
- Improve ambulance networks to reduce emergency response time, Also, telemedicine can be used to reach more rural people, to achieve this, the electricity in rural areas needs to be       efficient.
- Monitor facility performance and adjust funding based on impact metrics. 


 


